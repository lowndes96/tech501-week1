# Linux Research Tasks: 

## Task 1: 

The ls command along with its -l (for long listing) option will show you metadata about your Linux files, including the permissions set on the file.
<br>

* File type: -
* Permission settings: rw-r--r--
* Extended attributes: dot (.)
* User owner: root
* Group owner: root
<br>
https://www.redhat.com/en/blog/linux-file-permissions-explained 

### Does being the owner of a file mean you have full permissions on that file? Explain. 

Typically you have read write and modify access. 

### If you give permissions to the User entity, what does this mean? 

User refers to the owner of the file.

### If you give permissions to the Group entity, what does this mean? 

Group refers to the user group associated with the file.

### If you give permissions to the Other entity, what does this mean? 

Other refers to everyone else who is not the file’s owner and does not belong to the group.

### long answer q's: 
```
When the system is looking at a file's permissions to determine what information to provide you when you interact with a file, it runs through a series of checks:

It first checks to see whether you are the user that owns the file. If so, then you are granted the user owner's permissions, and no further checks will be completed.
If you are not the user that owns the file, next your group membership is validated to see whether you belong to the group that matches the group owner of the file. If so, then you're covered under the group owner field of permissions, and no further checks will be made.
"Others" permissions are applied when the account interacting with the file is neither the user owner nor in the group that owns the files. Or, to put it another way, the three fields are mutually exclusive: You can not be covered under more than one of the fields of permission settings on a file.

You give the following permissions to a file: User permissions are read-only, Group permissions are read and write, Other permissions are read, write and execute.  
```
**You are logged in as the user which is owner of the file. What permissions will you have on this file? Explain.**
<br>
You will have read only permissions, as the checks stop there. 

**Here is one line from the ls -l. Work everything you can about permissions on this file or directory.**

`-rwxr-xr-- 1 tcboony staff  123 Nov 25 18:36 keeprunning.sh `
<br>

* file or directory: `-` indicates its a file, as directory is indicated with a `d`
* owner permissions: `-rwxr` read, write, execute <br>
* user group permissions: `-xr` read and execute <br>
* others permissions: `-r` read only permissions <br>
<br>

* no of links to file: `1` <br>
* file owner: `tcboony` <br>

## Task 2: 

### What numeric values are assigned to each permission? 
* Read (r): 4
* Write (w): 2
* Execute (x): 1

### What can do you with the values assign read + write permissions? 

* these permissions are often written additivly: ie read+write permissions = 6 

### What value would assign read, write and execute permissions? 

7 

### What value would assign read and execute permissions? 

5

### Often, a file or directory's mode/permissions are represented by 3 numbers. What do you think 644 would mean? 
* The number 644 represents the following permissions:
    * Owner: 6 (Read + Write)
    * Group: 4 (Read)
    * Others: 4 (Read)


## Task 3: 

### What is piping?

* Piping sends the output of one command to another command as input.
* It's used in UNIX like opperating system 

### How is piping different to redirection using > or >>?

* Redirection is used to send the output of a command to a file instead of the terminal.
  * `>`: Redirects output to a file, overwriting it if the file exists.
  * `>>`: Redirects output to a file, appending to it if the file exists.
* Redirection is about output storage, while piping is about passing data between commands.

### What character is used for piping?
| 

### Give an example of a command that using piping once
`echo "Hello" | tr 'a-z' 'A-Z'`
<br>
This converts "Hello" to uppercase using the tr command. Here, the echo output is piped directly into tr for processing.

### Example of a command that uses piping twice

`cat /var/log/syslog | grep "error" | wc -l`
<br>

Explanation:

* `cat /var/log/syslog`: This command outputs the contents of the syslog file.
* `| grep "error"`: The output from cat is piped into grep, which filters out only the lines containing the word "error".
* `| wc -l`: The filtered lines are then piped into wc -l, which counts how many lines contain the word "error."

### Example of a command that uses piping twice and then sends the output to a file:
`ps aux | grep "python" | sort > python_processes.txt`
<br>
Explanation:

* `ps aux`: This command lists all running processes on the system.
* `| grep "python"`: The output from ps aux is piped to grep, which filters and shows only the lines containing "python".
* `| sort`: The output from grep is piped to sort, which sorts the filtered lines.
* `> python_processes.txt`: Finally, the sorted output is redirected to the file python_processes.txt.

<br>

>Hint:
>
>>    The grep, sort, head, tail commands could be useful
>>    For piping twice, you could:
>>    use ls as the input, search for string in more than folder/file, then sort the files/folders that match in reverse order.
>>    use ls as the input, get the bottom 2 rows of the first 3 rows


## Task 4 


### Why is managing file ownership important?
Managing file ownership is important for several reasons:

* Security: Ownership ensures that only authorized users can access or modify a file or directory. By assigning ownership, you can control who has permission to read, write, or execute files.
* Accountability: Ownership helps in tracking who owns or is responsible for a file or directory. This can be critical for auditing and troubleshooting.
* Access Control: Properly managing ownership allows for fine-grained control over file permissions. By setting the right ownership, you ensure that sensitive files or directories are only accessible to the right people.

### What is the command to view file ownership?
`ls -l`
### What permissions are set when a user creates a file or directory? Who does file or directory belong to?
When a user creates a file, the default permissions are typically `rw-r--r-- `
### Why does the owner, by default, not recieve X permissions when they create a file?
Because the file is assumed to be a regular data file
### What command is used to change the owner of a file or directory?
`chown`