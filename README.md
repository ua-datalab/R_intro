# R_intro_posit_cloud

This tutorial is supplemental information for the Carpentries intro lesson on R. https://swcarpentry.github.io/r-novice-inflammation/

https://swcarpentry.github.io/r-novice-gapminder/01-rstudio-intro.html


<br/>
<br/>
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




