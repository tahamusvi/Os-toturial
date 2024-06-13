
# Session 8

## awk

The `awk` tool is typically used for reporting from various files. This tool was developed at Bell Labs in the 1970s. The `awk` tool has numerous capabilities, among the most important of which are the following:

- A powerful tool and an interpretive programming language
- Used for text processing, report generation, and presentation of informational reports

`awk` can process text files and streams. The input data is divided into records and fields. `awk` operates on one record at a time until the input is exhausted. Records are separated by a character called the record separator (RS). The default record separator is the newline character, meaning that each line in the text data is a record. A new record separator can be set using the `RS` variable.

The records consist of fields that are separated by the field separator (FS). By default, fields are separated by one or more spaces, tabs, and newline characters.

The fields of each record are referenced using the dollar sign ($) followed by the field number, starting from 1. The first field is $1, the second field is $2, and so on. The last field can also be referenced using the special variable `NF`.

The entire record can be referenced using `$0`.

```
awk 'pattern {action}' input-file > output-file
```

As `awk` processes the data, if a record matches the pattern, it performs the specified action on that record. If the rule has no pattern, all records (lines) will match.

The actions defined in `awk` are enclosed in curly braces `{}` and consist of multiple statements, each specifying an operation to be performed. An action can have more than one statement, separated by a newline or a semicolon (;). If the rule has no action, it will default to printing the entire record.

If the column separator is not space or tab, the `-F` option is used.

`awk` supports various types of expressions, including expressions, conditions, input/output statements, and more. The most common `awk` statements are:

- `exit`: Stops the execution of the entire program and exits.
- `next`: Stops the processing of the current record and moves to the next record in the input data.
- `print`: Prints records, fields, variables, and custom text.
- `printf`: Provides more control over the output format.

When writing `awk` programs, anything after the hash sign (#) until the end of the line is considered a comment.

Long lines can be split into multiple lines using the continuation character, the backslash (`\`).


#



## Internal Variables in awk

awk has several internal variables that contain useful information and allow you to control the way the program is processed. Here is a description of some of the most common internal variables in awk:

- `NF`: Displays the number of fields in the record.
- `NR`: Displays the number of the current record.
- `FILENAME`: Displays the name of the input file that is currently being processed.
- `FS`: Displays the field separator.
- `RS`: Displays the record separator.
- `OFS`: Displays the output field separator.
- `ORS`: Displays the output record separator.


#



## Changing the Field and Record Separators

The default field separator in awk is one or more spaces or tabs. This value can be changed by setting the `FS` variable.

For example, to set the field separator to the dot character, you can use the following command:

```
awk 'BEGIN { FS = "." } { print $1 }' test.txt
```

Output:
```
Name1 Milwaukee 60 22 0
Name2 Toronto 58 24 0
33Name3 Philadelphia 51 31 0
Name4 Boston 49 33 0
Name5 Indiana 48 34 0
```

The field separator can also be set to multiple characters:

```
awk 'BEGIN { FS = ".." } { print $1 }' test.txt
```

When running awk from the command line, you can also use the `-F` option to change the field separator:

```
awk -F "." '{ print $1 }' test.txt
```

By default, the record separator is a newline character, and it can be changed using the `RS` variable.

In the following example, the record separator is set to the dot character:

```
awk 'BEGIN { RS = "." } { print $1 }' test.txt
```

Output:
```
Name1 Milwaukee 60 22 0
732
Name2 Toronto 58 24 0
707
33Name3 Philadelphia 51 31 0
622
Name4 Boston 49 33 0
598
Name5 Indiana 48 34 0
585
```