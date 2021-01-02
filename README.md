On my OKR process:

I have a text file in a known location. It's backed up on git.

I can open and edit that file quickly using bash. From within VIM I can quickly commit to reduce the # keystrokes. More details: https://github.com/jodavaho/bashlog

(Really though, you can just save as an environment variable your file location)

The text file is structured with space-delimited text, like this: https://github.com/dkogan/vnlog

My current structure:

"# date item amount"

Easy to open, easy to plop down today's date and the item / amount. Save multiple date/item entries and add them inscripts ...  Easy to save. Done.

The work came in building stuff to plot it:

I have other files that link "items" to goals or other metadata like categories, etc. Like a relational database, but easily edited in text.

For example, to make a link from daily items to Key Results

"# item okr"

okr is structured like this: <year>.<quarter>.<category/goal>.<kr>

For example:

2020.Q4.01.01 is workout 90x (1/day)

2020.Q4.02.02 is get through 26 textbook chapters

2020.Q4.02.03 is 100 h studying literature

The categories are usually Fighting (I box), Tech, Mental health,  and Social, but YMMV

Another example is "workout-mapping.vnl" with structure:
"# item muscle-group factor"

etc etc.

vnlog has nice vnl-join commands that quickly build the table and output formatted text (one command).  Then reading that in R is easy ...

```
data <- read.table('../2020-Q4-OKR.vnl',skip=2,stringsAsFactors = FALSE)
```

Aggregating by date is easy:

```
data.agg<- aggregate(x=data$Amount,by=list(data$Date),FUN=sum)
```

Then plot using ggplot2.

Examples from 2020 Q4 (just ran the numbers yesterday!)

https://josh.vanderhook.info/media/okr.png

https://josh.vanderhook.info/media/workouts.png

https://josh.vanderhook.info/media/mood.png
