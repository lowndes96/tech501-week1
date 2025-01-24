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
**add html next time on VM (but pretty much a standard html page)
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





