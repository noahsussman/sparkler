sparkler
========

A cli tool like spark, that produces graphical plots from
whitespace-delimited lists of numbers passed by other command line
arguments.

A _line graph_ is produced if you give **sparkler** a small data
set. Larger data sets are represented as _scatter plots._

The output image is written to a file called `my_graph.png` in the
current working directory. **Older output files will be silently
overwritten.**

## Usage

Just pipe a newline-delimited list of integers to **bin/sparkler** and it
will produce a graphical plot.

The following command will produce a file called `./my_graph.png` that
shows the first nine integers of the Fibonacci Sequence.

    echo 0 1 1 2 3 5 8 13 21 | bin/sparkler

or

    echo "0
    1
    1
    2" | bin/sparkler

Any text after the integer tokens is used as labels for the x-axis:

    echo "0 this is a label
    1 this is another label
    1 and so on
    2 yep labels" | bin/sparkler

You can also pass arguments directly:

    bin/sparkler 0 1 1 2 3 5 8 13 21

or

    bin/sparkler "0
    1
    1
    2"

and also

    bin/sparkler "0 this is a label
    1 this is another label
    1 and so on
    2 fun with labels"

## Installation

The following command will install all dependencies, and should work
on any system with a relatively modern version of Python:

    sudo easy_install numpy matplotlib

You can optionally move or symlink **bin/sparkler** to
**/usr/bin/sparkler** (or anywhere in your path) and it should then be
usable from anywhere on your system, just like any other shell
command.

## How to run the tests

    tests/run

If the exit code is `0`, all is well.

### How do the tests work?

The tests generate graphs off of various inputs and then diff the each
generated image against a fixture image, to validate that the expected
graphs were produced.

## What's not included

**sparkler** is intended to be like **spark:** a dead simple tool that
does the right thing 99% of the time. Thus there are no configuration
options.

The general use case for **sparkler** is: "I am looking at the output
from a shell command and I wonder what it looks like as a graph." More
complex use cases are intentionally not considered.

When you require that level of detail in your analysis, you should
switch to using matplotlib directly, or use another data visualization
tool like R, GNUPlot, Flot or d3.

Specifically, you cannot label the axis nor add a title to the graph
using **sparkler.** For that you can edit the PNG output files using
an image-annotating tool like Photoshop, Skitch or Jing.

And you also cannot combine multiple data series on a single
graph. When you reach a point where you have multiple data series
saved in different files, you should consider using a tool more
powerful than **sparkler.**

