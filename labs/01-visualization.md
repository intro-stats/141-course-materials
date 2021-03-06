Lab 1: Data Visualization
================

## Setup

This lab will focus on generating plots using the `ggplot2` package, as
well as practicing data subsetting with the `filter()` command from the
`dplyr` package, both of which live in the `tidyverse` package.

To get started, load the following packages and data set.

``` r
library(tidyverse)
library(oilabs)
data(survey141)
```

This data comes from a class survey that Math 141 students took two
years ago, however the data frame we’ll be using has been slightly
altered to make generating plots easier. The column names of the data
set have been changed as well. The help file contains the original
questions.

``` r
?survey141
```

## Plot Types

The `ggplot` command is used to create a base layer for a plot, with
`aes()` used to specify which visual cues to connect to variables in a
data frame. After creating this base layer, a geometry can be applied
which will render a specific type of plot.

``` r
d <- ggplot(survey141, aes(x = hot_dog, fill = dog_pants))
d + geom_bar()
```

![](01-visualization_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

Above a base layer for the survey data is created with `hot_dog` mapped
to the x-axis and `dog_pants` mapped to fill (a color based visual cue).
This base layer is assigned to `d` and then a bar plot layer is added to
it via `geom_bar()`.

The following geoms are some of the most commonly used:

    - `geom_bar()`:         for a categorical variables
    - `geom_histogram()`:   for a numerical variable
    - `geom_density()`:     for a numerical variable
    - `geom_boxplot()`:     for a numerical variable and possibly a categorical variable
    - `geom_point()`:       for 2 numerical variables
    - `geom_smooth()`:      for 2 numerical variables

Multiple geometries may be layered on top of each other, as is often the
case with `geom_smooth()` and `geom_point()` to create scatter plots
with trend lines.

1.  Create a density plot for the number of colleges applied to. Please
    describe this distribution in terms of its shape, center, and
    spread.

## Filtering Data

Often there will be entries in data sets that you’ll want to exclude
from a particular analysis. This is when the `filter()` command will be
useful. `filter()` will take a data set and find all rows that return
true under set conditions (or filters).

The following example has the `survey141` data being filtered to only
include rows which have “Tea” as the response for the `coffee_tea`
variable. This subset of the original survey data is then assigned to a
new data frame called `tea_drinkers`.

``` r
tea_drinkers <- filter(survey141, coffee_tea == "Tea")
```

The following uses the piping operator to apply a filter to `survey141`,
filtering out only those rows which have 0 in the `marijuana` variable,
**and** a value greater than 0 in the `alcohol` variable.

``` r
alcohol_only <- survey141 %>% 
  filter(alcohol > 0 & marijuana == 0)
```

Pulling up the help file will give a list of useful filter functions and
more examples of the function in use.

2.  Filter out those who answered PC or Mac to the computer of choice
    question. Create a side-by-side box plot comparing the first kiss
    age between the groups. Do you notice any differences between the
    two groups? If so, what are they? (Note: if the box plot does not
    render correctly, try switching the `x` and `y` assignments.)

## Settings, Labels and Limits

Beyond aesthetics and geometries, `ggplot2` also has settings and labels
for customizing visualizations.

Settings are options one can apply to a plot, but unlike aesthetics,
they are not directly linked to a variable.

``` r
ggplot(survey141, aes(x = hot_dog, fill = dog_pants)) +
  geom_bar(position = "fill")
```

![](01-visualization_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

In the above example, the setting `position = "fill"` is used in
`geom_bar()` so that count is no longer displayed, but instead
proportion.

3.  Using `position = "jitter"` create a scatter plot relating `alcohol`
    and `marijuana`.

Beyond geoms, additional layers such as `labs()` and `xlim()` can be
added to a plot, used to add labels/titles and axis limits respectively.
These layers are added on just like a geom and can help add clarity or
focus to a specific part of a plot.

4.  Give more descriptive axis labels and specify limits for the
    previous plot to remove more extreme cases. Describe any
    relationship or lack thereof. How do these last two plots compare to
    your personal conception of how these variables are related?

5.  Create 2-3 more visualizations from the survey data that are of
    interest to you. Have at least one visualization come from a
    filtered subset of the data and have at least one more map 3 or more
    variables. Describe any trends/patterns discovered.

6.  Recreate exactly the following plot. The help file for
    `geom_smooth()` will be useful to get the best fit lines looking
    appropriate.

![](01-visualization_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

## More Practice

[Fivethirtyeight.com](https://fivethirtyeight.com/) is a news website
that focuses on data journalism: nearly all of their stories are
inspired by a data set. The editors of the website make that data
available on github for all to explore, and several fine members of R
community put it into an R package so that we can have easy access to
it. Load in the package and view the names of the data sets with the
following.

``` r
library(fivethirtyeight)
data(package = "fivethirtyeight")
```

You can learn more about the listed data sets by pulling up with
helpfile by running a command like `?bob_ross`. If that seems a data set
of interest to you, you can load it into R and view it with:

``` r
data("bob_ross")
View(bob_ross)
```

7.  Select a data set (not `bob_ross`) and produce three plots. There
    are countless plots that you *could* generate, but aim to make plots
    that reveal interesting structure in the data and are throughfully
    constructed. Be sure to add useful axis labels and a title plot.
    Provide a sentence or two for each plot describing what it reveals
    about the subject matter. Hint: usually data sets with a mix of
    categorical and numberical data are easier to visualize.

8.  Only after you have produced these three plots, go ahead and read
    the story that this data set inspired. Those can be found by
    clicking into the appropriate folder at [this
    website](https://github.com/fivethirtyeight/data) and following the
    link. Try to reproduce one of the plots featured in the story. Add a
    sentence or two describing what the plot shows in terms of the data
    and how your plot differs from the one published in the story. If
    you aren’t able to reproduce any of the plots, describe precisely
    the hurdles that you ran into. Be sure to include in your answer a
    link to the original plot in the story. You can get this by
    right-clicking on the image, selecting “copy image address”, then
    pasting into a markdown section of your document with the syntax
    `[the original image can be found here](here-is-the-pasted-url)`.
