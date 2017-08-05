# csv2api

## A simple tool to turn a CSV file into a simple web API

Ever wanted to access as CSV file as a web API? Probably not, but it's fun, so try it anyway!

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

