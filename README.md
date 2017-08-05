# csv2api

## A simple tool to turn a CSV file into a simple web API

Ever wanted to access as CSV file as a web API? Probably not, but it's fun, so try it anyway!

## Installation

csv2api is written in R and several add-on packages.

Please ensure R is installed and available on your system before use.

R installation information can be found at the [official R project website](https://www.r-project.org/).

The additional package dependencies can be installed within R, as follows:

```
> install.packages(c('readr','plumber','argparser','dplyr'))
```

csv2api can be installed by simply cloning this repo.

Assuming everything worked without incident, you're nearly ready to enter the fascinating world of APIs.

## Usage

```
usage: ./csvtoapi [--] [--help] [--noheader] [--opts OPTS] [--port PORT] filename

Serve a CSV file via a JSON based API

positional arguments:
  filename			input CSV filename

flags:
  -h, --help			    show this help message and exit
  -n, --noheader			no headers [default: FALSE]

optional arguments:
  -x, --opts OPTS			RDS file containing argument values
  -p, --port PORT			specify port number [default: 8000]
```

## Examples

csv2api comes with a demo csv file which we'll use for the examples.

```
./csv2api csv2api-demo.csv
```

This loads the csv file and starts the API endpoint at http://localhost:8000

Congratulations, you now have a simple API to access your CSV file!

There are three main query types you can use against your new API.

Try the following:
* http://localhost:8000/ - the returns the entire CSV file as a JSON object
* http://localhost:8000/random/ - this returns a single, randomly selected record from the file.
* http://localhost:8000/language=='R'&score>90 - This uses a simple query language to return a subset of results

For any R users familiar with dplyr, you'll already be familiar with the query language as it's essentially passed straight through to dplyr's `filter()`.

If you want to load a CSV file that has no header row, use `-n` and if you want to change the port from 8000, you'll need `-p`

csv2api also comes with an even simpler command line access tool, that takes the JSON returned from your API and turns it back into a text format suitable for printing in the terminal.

To use it, run:

```
./apiclient "language=='R'&score>90"
```

Or whatever query you'd like. This will return:

```
Loading required package: methods
http://localhost:8000/language=='R'&score>90 
  id  name  country language score animal  drink
1  2 Henry   France        R    96    Dog Coffee
2 34  Anna Portugal        R    95    Dog   <NA>
3 55 Ethan  Denmark        R    99    Dog Coffee
```


## Security

A quick note about security - Please don't use this script in a manner that exposes it to the open internet. This tool was built to be a bit of fun, and to allow people to quickly turn their own data into a simple API that they can then play with for educational purposes. No effort has been put into security testing and hardening. It is not designed for use in production settings. Use at your own risk etc.
