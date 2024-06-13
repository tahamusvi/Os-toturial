# Session 7


## assign variable
- use let
- dont use space
```
    let t=5+3
    let t=$1+$2
```


## special variables
- $0 : The name of the Bash scripts.
- $1 - $9 : The first 9 arguments to the Bash scripts. 
- $# : how many arguments were passed to the Bash script.
- $@ : All the arguments supplied to the bash script.
- $? : the exit status of the most recently run process.
- $USER : The username of the user running the scripts.
- $HOSTNAME : the hostname of the machine the script is running on.
- $SECONDS : the number of seconds since the script was started.
- $RANDOM : Returns a different random number each time is it referred to.
- $LINENO : Returns the currents line number in the bash script.

## get direct input 
```
    bash samplefile 1 3
```
- $1 : 1
- $2 : 3

## get input
- use read
```
    read -p "text" variable_name
```
- for password
```
    read -sp "text" variable_name
```

## if statement
- use if ,elif and else in end fi 
```
    if [[state]] 
        then
        command
    elif [[]]
        then
        command
    else
        command

    fi
```
- -gt : great than
- -lt : lower than
- -eq : equal

## swtich case
- use string if statement
```
    case $variable_name in
        "case1")
        command1
        command2
        ;;

        "case2")
        command1
        command2
        ;;
    
    esac
```

## while statement
- with condition
```
    while [[conditions]]
        do
            command1
            command2
        done
```


## for statement
```
    for variable in list
        do
            command1
            command2
        done
```
- list can be : 1 2 3 4 5 .. N, file1 file2 file3,$(linux-or-Unix-Command-Here)

## functions
- for create or display file
```
    functions_name(){
        command1
        command2
        command3
        #return
    }
```


