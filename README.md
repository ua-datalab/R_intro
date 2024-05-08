# R_intro_posit_cloud

This is a tutorial on the very basics of R and RStudio. The tutorial is meant to use a cloud version of Rstudio with [Posit Cloud]() but can also be used with local installation. Most of the education material was pulled directly from Carpentries lessons on R, including:

https://swcarpentry.github.io/r-novice-inflammation/ and https://swcarpentry.github.io/r-novice-gapminder/01-rstudio-intro.html


<br/>
<br/>

<img src="/images/rstudio_logo.jpeg" width=300 style="display:inline-block; margin-right:20px;"> <img src="/images/r_logo.jpeg" width=200 style="display:inline-block;">    



<br/>

## What is R?

R is a scripting language originally developed at the University of Aukland, NZ for statistically data analysis. R software is open-source and free software and uses [GNU General Public License](https://en.wikipedia.org/wiki/GNU_General_Public_License#Version_2). R runs natively in a command line interface. R software is available for Windows, Mac, and Linux operating systems. The base source code is maintained by the R Core Team, but additional software packages are developed by thousands of independent people around the world. 

Scripting languages like R are very useful for data exploration and analysis because they offer limitless customization for instructing a computer to do something. They can, however, take more time to learn compared with purely graphical user interface (GUI) programs (think Microsoft Word). 

<br/>
<br/>
<br/>

## What is RStudio?

Rstudio is an integrated development environment (IDE) built specifically for using the R language. It was developed by [Posit PBC](https://posit.co/) and uses the license [GNU Affero General Public License version 3](https://en.wikipedia.org/wiki/GNU_Affero_General_Public_License).

RStudio makes is easier and more ituitive to use the R language by providing point-and-click elements, a script editor, console, package management features, help documentation, and tools to visualize data graphs. 

Rstudio can be ran on your local computer, on a server, or in the cloud (i.e., on a Posit Computer).

<br/>
<br/>
<br/>

## Launch RStudio on Posit Cloud

For learning R/Rstudio today, we will all use a cloud version of Rstudio hosted on Posit Cloud. Cloud instances of software are great for educational environments because they require minimal setup and avoid the pitfalls of local installation. The drawback of such an approach is that educational cloud instances often have low computing resources and requesting more resources costs $$. We will interact with cloud Rstudio using a web browser (e.g, Google Chrome). 

Sign up for a free account with Posit Cloud to launch a cloud instance of RStudio https://posit.cloud/plans. It is probably easiest to sign-up using your University of Arizona Google account. 

<br/>
<br/>

## Navigating the RStudio Interface

When you first open RStudio, you will be greeted by three panels:

* The interactive R console/Terminal (entire left)
    * The console is for typing R commands (one at a time)
    * The terminal is the Linux Command Line. This is where you give instructions to your underlying computer.
      
* Environment/History/Connections (tabbed in upper right)
    * The environment pane will show all of your variables and objects
      
* Files/Plots/Packages/Help/Viewer (tabbed in lower right)
    * Files tab gives you access to the directories and files in the underlying computer
    * Plots tab will show graphical representations of data
    * Packages tab shows all of the software
    * Help tab shows documentation on all of the software 




<img src="/images/rstudio.png" width=800>
<br/>


<br/>
<br/>

Once you open files, such as R scripts, an editor panel will also open in the top left. 

An R script (.R) is a file that holds multiple R commands that can be run automatically in sequence. 

<img src="/images/rstudio2.png" width=800>


<br/>
<br/>

#### Type some commands in the script editor

<img src="/images/script.png" width=300>

'#' makes the line a comment and disables it as code 

<br/>
<br/>

#### Run a line of code 
With the curser on the code line of interest, you can: 

Click the <img src="/images/run.png" width=85>

or type

 `CTRL` + `Return` on Windows or Linux
 
 `⌘` + `Return` on MacOS
 
<br/>
<br/>
<br/>

#### Install New Packages

install.packages("lidR")


#### Bring Packages into Memory (ready for use)

library("spatial")



variable assignments



<br/>
<br/>
<br/>

## Download Patient Data

We are studying inflammation in patients who have been given a new treatment for arthritis, and need to analyze the first dozen data sets of their daily inflammation. The data sets are stored in CSV format (comma-separated values): each row holds information for a single patient, and the columns represent successive days. 

<br/>
<br/>

In the terminal:

Download r-novice-inflammation-data.zip

`curl -o r-novice-inflammation-data.zip https://swcarpentry.github.io/r-novice-inflammation/data/r-novice-inflammation-data.zip` 

<br/>
<br/>

Unzip the file 

`unzip r-novice-inflammation-data.zip`

<br/>
<br/>

Once Unzipped, go into the data directory

`cd data`

<br/>
<br/>

List the files in the directory 

`ls`

<br/>
<br/>
<br/>

## Bring the Patient Data Into RStudio

In the R script, type:

`read.csv(file = "data/inflammation-01.csv", header = FALSE)`

<br/>
<br/>

Assign the data as a variable

`inflam = read.csv(file = "data/inflammation-01.csv", header = FALSE)`

<br/>
<br/>

## Query and Manipulate the Data

Now that our data are loaded into R, we can start doing things with them. First, let’s ask what type of thing inflam1 is:

`class(inflam1)`

ouput = "data.frame"

<br/>
<br/>

`dim(inflam1)`

output = "60 40"

<br/>
<br/>

### Get data values from specific rows and columns

Get value of row 1 and column 1

`inflam[1,1]`

<br/>

Get value of row 30 and column 20

`inflam1[30,20]`

<br/>

Get values from rows 1, 3, 5, and columns 10, 20

`inflam1[c(1,3,5), c(10,20)]`

<br/>

Get values for rows 1-4, and columns 1-10

`inflam1[1:4, 1:10]`

<br/>

Get values for row 5 and all columns

`inflam1[5, ]`

<br/>

Get values from all rows, but only for columns 16-18

`inflam1[, 16:18]`

<br/>

Assign the values to a new variable (ie, subset data)

`subset = inflam1[, 16:18]`

<br/>
<br/>


Addressing Columns by Name

`column_16 = inflam$V16`

<br/>
<br/>

### Descriptive Statistics

Calculate the Median value of column 16

`median(inflam1$V16)`

<br/>
<br/>

Calculate the Mean value of column 16

`mean(inflam1[, 16])`

<br/>

Calculate the Mean value of row 3

`mean(inflam1[3, ]`

<br/>

Note that R may return an error when you attempt to perform similar calculations on subsetted rows of data frames. This is because some functions in R automatically convert the object type to a numeric vector, while others do not (e.g. max(dat[1, ]) works as expected, while mean(dat[1, ]) returns NA and a warning). You get the expected output by including an explicit call to as.numeric(), e.g. mean(as.numeric(dat[1, ])). By contrast, calculations on subsetted columns always work as expected, since columns of data frames are already defined as vectors.

<br/>

For row statistics try:

`mean(as.numeric(inflam1[3, ]))`

<br/>
<br/>

Use `summary` to get basic descriptive stats

`summary(inflam1$V16)`

<br/>
<br/>

Get the mean inflammation value for each patient. The '1' argument specifies rows. 

`mean_patient_inflammation = apply(inflam1, 1, mean)`

<br/>
<br/>

Get the mean inflammation value for each day. The '2' argument specifies columns.  

`mean_day_inflammation = apply(inflam1, 2, mean)`

<br/>
<br/>

### Challenge

The apply function can be used to summarize datasets and subsets of data across rows and columns using the MARGIN argument. Suppose you want to calculate the mean inflammation for specific days and patients in the patient dataset (i.e. 60 patients across 40 days).

Please use a combination of the apply function and indexing to:

1. calculate the mean inflammation for patients 1 to 5 over the whole 40 days
   
2. calculate the mean inflammation for days 1 to 10 (across all patients)

3. calculate the mean inflammation for every second day (across all patients)

<br/>
<br/>

## Plotting

`plot(mean_day_inflammation, xlab = "Day")`



