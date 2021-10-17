# Bash

link: https://ryanstutorials.net/bash-scripting-tutorial/

## What is a Bash Script?

```bash
./myscript.sh
```

```bash
#!/bin/bash
# A sample Bash script, by Ryan
echo Hello World!
```

##### Why the ./

Bash only looks in those specific directories and doesn't consider sub directories or your current directory. It will look through those directories in order and execute the first instance of the program or script that it finds.

The $PATH variable is an individual user variable so each user on a system may set it to suit themselves.

This is done for a few different reasons.

It allows us to have several different versions of a program installed. We can control which one gets executed based on where it sits in our $PATH.
It allows for convenience. As you saw above, the first directory for myself is a bin directory in my home directory. This allows me to put my own scripts and programs there and then I can use them no matter where I am in the system by just typing their name. I could even create a script with the same name as a program (to act as a wrapper) if I wanted slightly different behaviour.
It increases safety - For example a malicious user could create a script called ls which actually deletes everything in your home directory. You wouldn't want to inadvertantly run that script. But as long as it's not in your $PATH that won't happen.  
If a program or script is not in one of the directories in your $PATH then you can run it by telling Bash where it should look to find it. You do so by including either an absolute or relative path in front of the program or script name. You'll remember that dot ( . ) is actually a reference to your current directory. Assuming this script is in my home directory I could also have run it by using an absolute path.


##### The Shebang (#!)


#!/bin/bash

This is the first line of the script above. The hash exclamation mark ( #! ) character sequence is referred to as the Shebang. Following it is the path to the interpreter (or program) that should be used to run (or interpret) the rest of the lines in the text file. (For Bash scripts it will be the path to Bash, but there are many other types of scripts and they each have their own interpreter.)

Formatting is important here. The shebang must be on the very first line of the file (line 2 won't do, even if the first line is blank). There must also be no spaces before the # or between the ! and the path to the interpreter.



## Variables

$1, $2, ...  
The first, second, etc command line arguments to the script.  
variable=value  
To set a value for a variable. Remember, no spaces on either side of =  
Quotes " '  
Double will do variable substitution, single will not.  
variable=$( command )  
Save the output of a command into a variable  
export var1  
Make the variable var1 available to child processes.  


```bash
#!/bin/bash
# A simple copy script
cp $1 $2
# Let's verify the copy worked
echo Details for $2
ls -lh $2

```
##### Special Variables

$0 - The name of the Bash script.
$1 - $9 - The first 9 arguments to the Bash script. (As mentioned above.)
$# - How many arguments were passed to the Bash script.
$@ - All the arguments supplied to the Bash script.
$? - The exit status of the most recently run process.
$$ - The process ID of the current script.
$USER - The username of the user running the script.
$HOSTNAME - The hostname of the machine the script is running on.
$SECONDS - The number of seconds since the script was started.
$RANDOM - Returns a different random number each time is it referred to.
$LINENO - Returns the current line number in the Bash script.


