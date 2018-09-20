hw02\_gapminder
================

Homework 02: Explore Gapminder and use dplyr
============================================

Bring rectangular data in
-------------------------

Work with the `gapminder` data we explored in class. *If you really want to, you can explore a different dataset. Self-assess the suitability of your dataset by reading [this issue](https://github.com/STAT545-UBC/Discussion/issues/115), and if you still aren't sure if it's suitable, send Vincenzo an email.*

The Gapminder data is distributed as an R package from [CRAN](https://cran.r-project.org/web/packages/gapminder/index.html).

Install it if you have not done so already and remember to load it.

    install.packages("gapminder")
    library(gapminder)

Install and load dplyr. Probably via the tidyverse meta-package.

    install.packages("tidyverse")
    library(tidyverse)

``` r
library(gapminder)
library(tidyverse)
```

    ## -- Attaching packages ------------------------------------------------------------ tidyverse 1.2.1 --

    ## v ggplot2 3.0.0     v purrr   0.2.5
    ## v tibble  1.4.2     v dplyr   0.7.6
    ## v tidyr   0.8.1     v stringr 1.3.1
    ## v readr   1.1.1     v forcats 0.3.0

    ## -- Conflicts --------------------------------------------------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

Smell test the data
-------------------

Explore the `gapminder` object:

-   Is it a data.frame, a matrix, a vector, a list?
-   What is its class?
-   How many variables/columns?
-   How many rows/observations?

``` r
str(gapminder)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    1704 obs. of  6 variables:
    ##  $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
    ##  $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
    ##  $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
    ##  $ pop      : int  8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
    ##  $ gdpPercap: num  779 821 853 836 740 ...

The output shows that the gapminder is a data frame (Classes are ‘tbl\_df’, ‘tbl’ and 'data.frame'). There are 6 columns/variables and 1704 rows/observations.

-   Can you get these facts about "extent" or "size" in more than one way? Can you imagine different functions being useful in different contexts?

``` r
nrow(gapminder)
```

    ## [1] 1704

``` r
ncol(gapminder)
```

    ## [1] 6

Using `ncol` and `nrow` is another way to get these dimensions. While `str` gives us more information, these 2 can be useful, especially if you want to use just the number of rows/cols. One might do so to calculate mean or loop through columns.

-   What data type is each variable?

From `str`, we can see the type for each variable.

-   country is Factor
-   continent is Factor
-   year is int
-   lifeExp is num
-   pop is int
-   gdpPercap is num

Be sure to justify your answers by calling the appropriate R functions.

Explore individual variables
----------------------------

Pick **at least** one categorical variable and at least one quantitative variable to explore.

-   What are possible values (or range, whichever is appropriate) of each variable?
-   What values are typical? What's the spread? What's the distribution? Etc., tailored to the variable at hand.
-   Feel free to use summary stats, tables, figures. We're NOT expecting high production value (yet).

Explore various plot types
--------------------------

Make a few plots, probably of the same variable you chose to characterize numerically. You can use the plot types we went over in class (cm006) to get an idea of what you'd like to make. Try to explore more than one plot type. **Just as an example** of what I mean:

-   A scatterplot of two quantitative variables.
-   A plot of one quantitative variable. Maybe a histogram or densityplot or frequency polygon.
-   A plot of one quantitative variable and one categorical. Maybe boxplots for several continents or countries.

You don't have to use all the data in every plot! It's fine to filter down to one country or small handful of countries.

Use `filter()`, `select()` and `%>%`
------------------------------------

Use `filter()` to create data subsets that you want to plot.

Practice piping together `filter()` and `select()`. Possibly even piping into `ggplot()`.

But I want to do more!
----------------------

*For people who want to take things further.*

Evaluate this code and describe the result. Presumably the analyst's intent was to get the data for Rwanda and Afghanistan. Did they succeed? Why or why not? If not, what is the correct way to do this?

    filter(gapminder, country == c("Rwanda", "Afghanistan"))

Read [What I do when I get a new data set as told through tweets](http://simplystatistics.org/2014/06/13/what-i-do-when-i-get-a-new-data-set-as-told-through-tweets/) from [SimplyStatistics](http://simplystatistics.org) to get some ideas!

Present numerical tables in a more attractive form, such as using `knitr::kable()`.

Use more of the dplyr functions for operating on a single table.

Adapt exercises from the chapters in the "Explore" section of [R for Data Science](http://r4ds.had.co.nz) to the Gapminder dataset.

Reflection
----------

Once you're done the above, go back to [UBC canvas](https://canvas.ubc.ca/), and find the "Homework 02" page. Here, you should submit a reflection (and, although not required, adding a link to your homework respository would be helpful for the markers).

Please don't skip this reflection! We really care about this.

Reflect on what was hard/easy, problems you solved, helpful tutorials you read, etc. What things were hard, even though you saw them in class? What was easy(-ish) even though we haven't done it in class?

Special Submission Cases
------------------------

**Are you worried about submitting early, and then wanting to make changes that are included in your submission?**

Don't be. We'll always grade your GitHub repository as it was at the last commit prior to the deadline. Therefore, we encourage you to submit early and often, especially regarding your GitHub repository!

**Want to submit early, and continue making contributions to your repository that you *don't* want to be graded?**

Just [create a release](https://help.github.com/articles/creating-releases/) of your homework repo, and include the link to this release in your submission, being sure to indicate that this is a special early release that you want graded. Or, even better, just fork the repo.
