Lab 2: Sampling
================

The quintessential activity that Reed alumni do upon returning to campus
is head up to the thesis tower to check to see if anyone has checked out
their senior thesis. They’re wondering: what is the chance that someone
was interested in my work? To answer that question and learn more
generally about the way in which senior theses are checked out, you will
collect data on this phenomenon.

## Recording Data

Your group will enter their data in a spreadsheet found here:
<https://bit.ly/38shltt>.

Each group will have their data in a different sheet of this google doc.
Click the plus in the lower-left corner to add a new sheet, rename by
concatenating your first names with `_`. To make life easier down the
line, please follow the division name guidelines on the first example
sheet.

1.  What is your guess of the total number of theses in the tower? Enter
    your guess here as well in the google sheet.

Add the following row of data to your google
sheet.

|  barcode | author\_last\_name | year | checkouts | division | n\_pages |
| -------: | :----------------- | ---: | --------: | :------- | -------: |
| 12345678 | tester             |  999 |         1 | MNS      |      100 |

Next, try running the following code to test if you’re able to bring the
data set into R:

``` r
options(httr_oob_default = TRUE)
library(tidyverse)
library(googlesheets4)
url <- "https://docs.google.com/spreadsheets/d/14DG_oUyg4bHFkQZsIgWVF9A042lw4ft9uWVAI4yTqyY/edit?usp=sharing"
theses <- read_sheet(ss = url,
           sheet = "andrew",
           skip = 11)
```

Be sure to swap out `"andrew"` with the name of your group’s sheet.

## Sampling considerations

Your objective is to learn as much about senior theses checkout patterns
as you can with 3 people and only about an hour. You need to record six
items of information on each thesis; `barcode` number,
`author_last_name`, `year` of publication, number of `checkouts`, and
`division` (all departments are grouped into divisions, found at
<http://www.reed.edu/academics.html>).

Since your resources are limited, sampling is an essential technique
here. With your group, discuss the following considerations to help
guide your sampling. Keep in mind the example of literary digest - more
data is worthless if it’s not representative - and spend 15 - 30 minutes
on this section. Also, you may want to collect preliminary data,
i.e. try out your method on a very small population to assess if it is
working as you intended and how long it takes. Please detail your
sampling strategy below.

2.  What organizational scheme do the theses follow in the tower?

3.  Please do your best to estimate the total number of theses in the
    tower (also record this in your google sheet).

4.  Please provide a detailed plan of how you will collect a sample of
    data that is representative and efficient? You might consider using
    a simple random sample, stratified sampling, or cluster sampling.
    Your plan should be explicit enough that someone else could follow
    in your footsteps next semester and know how to collect a sample in
    an identical manner.

## Data Collection and Reflections

Now is your opportunity to draw a sample of theses and record the
variables of interest. Please wrap things up in the tower room at the
end of class: even if you’d like to have a larger sample, a small
thoughtful data set can still be very valuable. Before 6 pm this
evening, your group is responsible for entering that data into your
google sheet.

After you have entered in all of your data, please answer the following
questions. Don’t forget to load your data set into your Rmd\! You can
find the code for that in the chunk of code at the top of this lab. To
keep things clean for that chunk, use the following R chunk options:
\`\`\``{r echo = FALSE, eval = TRUE, message = FALSE}`.

5.  Did you encounter any unexpected challenges when collecting this
    data? How did you resolve them?

6.  Create a plot to visualize the relationship between the number of
    checkouts and the year of publication. Describe the structure that
    you find. How many checkouts can you expect in your thesis if you
    come back for your 10th reunion? Your 20th?

7.  Create a plot that addresses the question: “Is there a trend in
    length of theses over time?”. Answer that question also in words.

8.  Create a plot that addresses the question: “Are theses from the
    different divisions checked out at different rates?”. Answer that
    question also in words.

9.  Combine the variables from plots 6 and 8 into a single plot that
    shows the trends in checkouts over time, separated out for each
    division. Describe any structure that you see.
