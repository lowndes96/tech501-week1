# Linux 

- [Linux](#linux)
    - [random useful commands (move latter if needed)](#random-useful-commands-move-latter-if-needed)
  - [thursday linux learning](#thursday-linux-learning)
    - [running a new vm](#running-a-new-vm)
      - [making a script:](#making-a-script)
      - [making a new webpage](#making-a-new-webpage)
        - [store the default page in a safe location](#store-the-default-page-in-a-safe-location)
        - [make a new page](#make-a-new-page)
        - [adding an image to the page](#adding-an-image-to-the-page)
  - [friday linux learning](#friday-linux-learning)
    - [navigating files and folders](#navigating-files-and-folders)
      - [ls command](#ls-command)
      - [directory navigation](#directory-navigation)
    - [manipulating files and folders](#manipulating-files-and-folders)
    - [looking at file contents](#looking-at-file-contents)
    - [environment variables:](#environment-variables)
          - [non persistant](#non-persistant)
        - [persistant](#persistant)
  - [looking at files](#looking-at-files)
  - [editing files](#editing-files)
  - [27th](#27th)
    - [what is a linux process?](#what-is-a-linux-process)
    - [running a process in the background (11:15 on )](#running-a-process-in-the-background-1115-on-)
    - [killing a process:](#killing-a-process)
    - [what is the difference between these kill commands?](#what-is-the-difference-between-these-kill-commands)

### random useful commands (move latter if needed)
sudo !! - runs previous command with sudo at front <br>
*quiting a process in linux*: q / ctrl z / ctrl c  - order of preferance 
<br>
wget - webget - used: wget [options] [url]
<br>
curl webpath.jpg --output cat.jpg 


## thursday linux learning 

### running a new vm 

#### making a script: 
> nano prevision.sh <br>
> prevision.sh script <br>
> >#file run with bash interpreter <br>
> > #!bin/bash <br>
> > sudo apt install nginx <br>
> >sudo systemct1 restart nginx <br>
> >status nginx <br>
> >sudo systemctl enable nginx <br>

* make script exicutable via `chmod +x provision.sh` 
* run script using full filepath name `./provision.sh` 

#### making a new webpage 

##### store the default page in a safe location 
> sudo mkdir /var/www/html/backup <br>
> sudo cp /var/www/html/index.nginx-debian.html /var/www/html/backup/index.nginx-debian.html <br>
##### make a new page 
> sudo nano /var/www/html/index.htm <br>
  GNU nano 2.9.3       /var/www/html/index.html                 

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-$
    <title>woah</title>
</head>
<body>
    <h1>emily made a  Webpage!</h1>
    <p>big day .</p>
<img src="image/frog.jpg" alt="frog image" >
</body>
</html>
```

##### adding an image to the page 
> curl https://media.istockphoto.com/id/175397603/photo/frog.jpg --output frog.jpg <br>
or <br>
> sudo wget -P /var/www/html/images https://www.thepetexpress.co.uk/blog-admin/wp-content/uploads/2022/07/shutterstock_223329445.jpg <br>
then make a more appropriate folder and move it there  <br>
> sudo mkdir /var/www/html/images <br>
> sudo mv frog.jpg /var/www/html/images <br>
> cd /var/www/html/images <br>
> ls  <br>

## friday linux learning 

### navigating files and folders 
* dont mess with system files unless you know what you are doing! 
#### ls command 
> * `ls` - list files 
> * `ls -a` - list files including hidden 
> * `ls -l -a` - list files, hidden and permissions 

#### directory navigation  
> * `cd .`  current directory 
> * `cd ` or `cd ~` home directory 
> * `cd /` navigate to root directory
> * `cd ..` parent directory 
> * `pwd` print working directory 
> * `cd /then_path` gets you to a path from the root 

### manipulating files and folders 
* `rm` delete a file (wont get a warning)
* `rmdir` removes an empty directory
* `rm -r` removes files recursively (can be used on whole directorys, with caution!)
* `cp` copy a file 
* `mv [OPTIONS] SOURCE DESTINATION` - moving a file 

### looking at file contents 

`grep [option...] [patterns] [file...]` used to find sequences or patterns within code, can also be formatted as `cat chicken-joke.txt | grep chicken`
* multiple arguments can be used alongside the grep command, this is also where a regex may be used. 

### environment variables: 
###### non persistant 
* to view all environment variables use `printenv` 
* to see a specific environment variable use `printenv $VARIABLENAME`
* to add a new variable type `NEWVARIABLE = my_new_var`
These are examples of non persistant variables, any added variables will cease to exitst at the end of the session
##### persistant 
* inorder to make a persistant variable it must be exported to the .bashrc folder <br>
* generally this wont be neccisary 
>  echo "export MYNAME=Emily_is_persistant" >>.bashrc 
this adds the line to the end of the file ( a single > would overwrite the file)

## looking at files 
* `head -3 file.txt` shows 1st 3 lines of file 
* `tail -3 file.txt` shows last 3 lines of a file 
* `cat file.txt` shows contents of file 
## editing files 
* `touch file.txt` makes file 
* `nano file.txt` makes/opens file for editing 


## 27th 

### what is a linux process?  

* process is an active instance of that program running in memory (could be taking up CPU)
* `ps` can be used to list processes and `kill` to terminate
* multi-core cpu - the more 'cores' the more processes that can be run at once 
* user process is ustally related to a terminal, there is also a process ID (PID) for each one
  * you are also able to have parent and child processes (parent process is able to start a child process)
* `ps --help` shows help  
* `ps -e` will show all processes 
* `ps aux` aux is a combination of 3 flags 
  * a = show processes for all users
  * u = display the process's user/owner
  * x = also show processes not attached to a terminal
<br>

### running a process in the background (11:15 on )
* `sleep 3` delays execution of code by 3 seconds 
* `sleep 3 &` will run this process in the background 
  <br>
### killing a process: 
* if there is a tool to manage a particular process it can be switched on and off via that it `sudo systemctl start nginex` 
* **missed something** 
* `sudo systemctl status nginex` 
* `kill process` is a more blunt way, and can be used if something goes wrong 
* `kill -1 processID` hang-up most gentle form of kill  
* `kill processID` graceful shutdown (is the default if no numerical argument)
* brute force `kill -9 processID`
* `ps aux | grep sleep`
<br>
* parent process will restart a child process if killed, as that is its 'job' 
* have to kill the parent process 'gracefully' 
<br>

### what is the difference between these kill commands?  

* medium kill - will 'gracefully' terminate child processes associated with the parent process 1st 
* brute force kill - will shutdown parent first, and the child processes stay as 'zombie' processes and are left running in memory 
* to find child processses can add flag for 'parent process' (look up in help guide), command column can also give clues




