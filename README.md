# DoctorsAsDataScientists

*A course by Harry Green and Kate Ruth*

## Introduction

Data science has become increasingly important in modern medical research, which is often done using large databases of millions of people. As computing facilities become better, the amount of data available for medical research will only increase. Data science is about gaining insights from large data. Most medical guidelines that inform your practice will have been informed by data science, so having some experience in the field will help understand where these insights come from.

As a junior doctor, you will also be expected to be auditing your own practice. You may also become involved in research using data from either your own practice or larger, external databases. Efficient and accurate data-handling skills can make these processes a lot easier.


## Session 1

### Loading and using RStudio

We will be using the R programming language through a piece of software called RStudio, hosted on a website called Posit Cloud, which is free to use.
On the website https://posit.cloud, create a new RStudio project called Doctors as Data Scientists. This project is where you will be running the workshop commands, and saving your work.

![image](https://github.com/hdg204/DoctorsAsDataScientists/assets/36624710/116f2fe3-2f50-4aeb-b3b1-4a18bec55315)


### Command line vs script window

First, create a new R file. 

![image](https://github.com/hdg204/DoctorsAsDataScientists/assets/36624710/47198d65-22af-4f60-bdf5-30de1f7cf7e4)

Your window should now look something like this.

![image](https://github.com/hdg204/DoctorsAsDataScientists/assets/36624710/87374858-6099-48f5-86d8-d3ee324e8576)


There are two ways to run code in R. The script window (top left bit) allows you to write and save multiple lines of code to be executed in one batch. The console (bottom left bit) is useful for testing individual lines of code if you’re not sure if you want to save them. I generally recommend testing stuff in the console, and once you have it working, saving the working commands in a script

### Simple commands

To check R is running properly, in the console, run

``` 40+30 ```

You should get the answer appearing on screen.

### Variable Types

This course covers three basic variable types.

* **numeric**, for example a person’s BMI
* **character**, for example a person’s name
* **logical**, which is a TRUE/FALSE variable, e.g. whether a person has cancer or not
  
There are other variable types too, such as date, time, and factors, but we will not go into these in this course.

### Assigning Variables

The power of R comes in being able to save lots of things in variables to perform tasks. 

```
height=1.7
weight=75
```

These should now be stored in R as numeric variables, and you can see them in the workspace on the top right. You can then perform calculations on these variables. For example:

```BMI=weight/(height^2)```

You can also store character variables in this way, but they require quotation marks around them. Try storing your name in a character variable.

```
first_name='your_name'
surname='your_name'
```

Note that a character variable, which can essentially store any kind of text, needs quotation marks around it. If you try ```first_name=Harry```, then it will trigger an error.

Note that these quotation marks MUST be 'and'. Not ‘and’. If your keyboard is adding these 'smart quotes', you'll need to disable these using Settings > general > keyboard on an ipad.

### Comparing variables

It is often useful to be able to compare two numbers. Since = is used for assigning variables, testing if two things are equal to each other is done using ==. You can also use < or >. The output will always be a logical variable.

For example, ```comp=5==7``` will create a logical variable called comp with the value FALSE.

Compare 5 with 7 using the following operators: < > <= >= == and !=.

### Vectors
A vector is a list of values, which can be stored under one name. This is done using c. For example,

```v=c(5,6,7,8)```

will store ```v``` as a vector which contains the 4 numbers. You can then operate on these at once.
Try running ```v*2```, ```v-4```, and ```v>6```.

### Functions, arguments and outputs

A series of commands can be pre-packaged into a function to allow common tasks to be run quicker and easier.
A function can have one or more arguments. Sometimes, these additional arguments control how the function works.
Using some of the variables that should be stored from earlier, run the following commands to get a feel for how they work:

```
mean(v)
length(v)
paste(first_name,surname)
```

You can also store the output of a function in a variable. This is very useful when you have a long series of commands to write.
```full_name=paste(first_name,surname)```

## Exercise

You have a group of patients, who have HbA1c values, in percent, of 5, 7, 6.5, 9, 8, 7, 5.5, 5.5, 9, 4. Store this as a numerical vector called HbA1c1.

You don’t like working with %. In diabetes class, you were taught mmol/mol. Subtract 2.15 from HbA1c1, and multiply it by 11, to give HbA1c2, which is now in mmol/mol.

What is the highest HbA1c value in mmol/mol? What is the mean?

Check if this is greater than 48, and store the answer in a variable called diabetes. 

Use ```sum()``` to find how many people have diabetes and ```length()``` to find how many people are in your data and calculate the prevalence of diabetes.

Write this in a script and save it as HbA1c.R. The data should **only** appear on line 1. It should be very easy to add new people to this, run the script again and get a new output. If you save the script, it should appear in your list of files on the bottom right.

### Solution

*This will be hidden until the last 10 minutes of the workshop*

<!-- 
```
HbA1c1=c(5, 7, 6.5, 9, 8, 7, 5.5, 4.5, 9, 4)
HbA1c2=11*(HbA1c1-2.15)
max_HbA1c= max(HbA1c2)
mean_HbA1c= mean(HbA1c2)
diabetes=HbA1c2>48
prevalence=sum(diabetes)/length(diabetes)
```
-->

### Conclusion

In this workshop we've learned how to handle basic variable types in R and run a series of calculations. While everything we did here could be done on a calculator, in the next workshop we will be working with a large dataset of 250,000 people.


## Session 2 - Working with Data

In the last session, we learned how to work with simple variable types in R, and covered assignment, functions, and vectors. In this session, we will move on to studying real healthcare data using R. We will use the Behavioral Risk Factor Surveillance System (BRFSS) dataset, collected by the CDC to study risk factors for Diabetes. The 2015 data is publicly available.

### Packages

When you load up R, you don't typically get any specialist functions to use. To load the data and do anything interesting with it, we need three packages, which first need to be installed. The `dplyr` package is very common in data science, and contains a lot of useful functions for managing data. The others are used for accessing and reading the file.

```
install.packages('readr')
install.packages('knitr')
install.packages('dplyr')
```

A load of red text appears, just ignore it. Then, once the packages are installed, they need to be loaded.

```
library('readr')
library('knitr')
library('dplyr')
```

Now we have our packages loaded, we can read in the data. I've stored this in the github repository along with this course.


```
myfile = "https://raw.github.com/hdg204/DoctorsAsDataScientists/main/diabetes_012_health_indicators_BRFSS2015.csv"
testdata=read.csv(myfile)
```



But these aren't children. The age was 'coded' using a 13 point variable, seen in https://www.icpsr.umich.edu/web/NAHDAP/studies/34085/datasets/0001/variables/AGEG5YR?archive=NAHDAP. This was likely to protect anonymity. We can do some guesswork if we want the real ages, and assume everyone is in the middle of their category. Except the top category is over 80. So we'll just call that 85.

testdata[age==1]=21




Your environment should now look like this

![image](https://github.com/hdg204/DoctorsAsDataScientists/assets/36624710/d90bb56f-bf93-4c04-8ca1-b1f2967ebada)

You can see we have 250,000 observations and 22 variables in a table, which in R is called a dataframe.

### Inspecting Data

You can take a closer look with the following functions

```
dim(testdata)
nrow(testdata)
ncol(testdata)
ls(testdata)
head(testdata)
head(testdata, n= 10) 
```

Run each of them in turn and take some time to work out what each one does.

You can also get a good picture of how the dataframe looks by using ```glimpse(testdata)```, and you can navigate the data interactively using ```View(testdata)```.  




