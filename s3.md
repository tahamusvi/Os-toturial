# Session 3


## cat
- for create or display file
```
    cat file_name
```

#

## head
- Displays the contents of the beginning of the file.
```
    head -n 7 file_name
```

#

## tail

- Displays the contents of the ending of the file

```
    tail -n 10 file_name
```
#

## wc

- Displays the number of lines, words and letters of a text file in order from left to right.

- line count:
``` 
    wc -l file_name
```

- word count:
``` 
    wc -w file_name
```

- char count:
``` 
    wc -c file_name
```

#

## cut

- Extracts parts of each line from a text or a text file.

```
    cut -b 1 file_name
```

- -b ---> byte
- -c ---> char
- -d ---> delimiter
- -f ---> field

#

## less
- display content of file 

```
    less file_name
```

#

## more
- like less

```
    more file_name
```
#

## grep 
- Searches for a string. This search can be done in the contents of a file or in the output of a command

```
    grep pattern file_name
```


- -c ---> It shows the number of found lines.
- -r ---> Search all files in a directory recursively does
- -i ---> The search is not case sensitive.

#

## echo 
- It is used to display the message on the standard output. At the end of the phrase, n is placed at the beginning of the line
Then he goes.

```
    echo hello world
```


- -n ---> The end of the string is not \n.
- -e ---> enables backslash escape interpretation.
- -E ---> disables backslash escape interpretation

#


## Create file

```
    cat > file_name
```
