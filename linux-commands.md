Commands Line
=================

### Print Current user's name
    
    $ whoami

### Print computer name

    $ hostname

### List item in directory

    $ ls

### Print working directory

    $ pwd

### List contents in long list format

    $ ls -l

### change directory to bin

    $ cd /bin

### Go to home directory

    $ cd 
    $ cd ~
### list content from other dir without moving from current dir

    $ ls /bin -l

### filter the output for files starts with p

    $ ls /bin/p* -l

### manual for command

    $ man ls

### single dash and double dash

    $ ls -l -G
    $ ls -l --no-group

### File permissions

    -rwxr-xr-x 1 elton staff   97 Jan 12  19:49 example.sh

- dash indicates Type: directory or file
- rwx Owners permissions: read+write+execute
- r-x Group permissions:read+execute
- r-x Other user permissions:read+execute
- 1 indicates File references: 1 link 
- Owner: elton
- Group: staff
- Size: 97 bytes
- Last Modified: 01/12/2020 19:49
- Name: exmaple.sh 

### list contents from root from any directory

    $ ls -l /

## In linux at root of the folder, we have a folder "var" which is used for creating frequently changing files

### Create a file at root/var folder

    $ sudo touch /var/file.txt

### echo command write output to screen

    $ echo "line 1"

### Elevating user to root user

    $ sudo su

### Writing to File

    # echo "line 1" >> /var/file.txt

###  Print file(s) to screen

    # cat /var/file.txt

### Print the last x lines of file

    # tail /var/file.txt

### print the file in pages

    # less /var/file.txt

- press q to exit from the less, mannual or man command also uses less

### change file permissions

    # chmod a+w /var/file.txt
- adding write permission to all users

### change user id or become super user

    # su mahesh

### To remove write permission

    $ sudo chmod a-w /var/file.txt

### change owner of the file

    $ sudo chown mahesh /var/file.txt

### change permission to user

    $ chmod u+w /var/file.txt

### Linux writes any system events into syslog file

    $ ls -l /var/log/syslog*

### find command

    $ find /var/log/syslog*

### using pipe for input to other cmd

    $ find /var/log/syslog* -type f -print0 | xargs -0 sudo chmod a+r

- type -f for selcting only file types
- print0 to input in unformatted list 
- xargs which accepts input from previous command

###  unzipping all archived files

    $ find /var/log/syslog*.gz -type f -print0 | xargs -0 sudo gunzip 

### another pipe example

    $ find /var/log/syslog* -type f -print0 | xargs -0 cat

### grep command

    $ find /var/log/syslog* -type f -print0 | xargs -0 cat | grep "NetworkManager"
    $ find /var/log/syslog* -type f -print0 | xargs -0 cat | grep "NetworkManager.*warn*"

###  network address

    $ ifconfig
    $ ifconfig | grep "inet "
    $ ifconfig | grep "inet " | head -n 1

- head -n 1 meaning just read the first line

### using cut command

    $ ifconfig | grep "inet " | head -n 1 | cut -d 'm' -f 1 | cut -d 't' -f 2 | cut -d 'n' -f 1

### bash script and nano

```bash
#!/bin/bash

originalAddress=$(ifconfig | grep "inet " | head -n 1 | cut -d 'm' -f 1 | cut -d 't' -f 2 | cut -d 'n' -f 1)

echo $originalAddress >> ~/ip.txt
```

### set permission to bash file

    $ chmod a+x ./write-ip.sh

### nano text editot

    $ nano write-ip.sh

- ctrl+O for save
- ctrl+X for exit

### change the bash script to run in loop

```bash
  GNU nano 2.9.3                                                                                       write-ip.sh                                                                                                 

#!/bin/bash

while [ : ]
do

        originalAddress=$(ifconfig | grep "inet " | head -n 1 | cut -d 'm' -f 1 | cut -d 't' -f 2 | cut -d 'n' -f 1)

        echo "$(date) $originalAddress" >> ~/ip.txt

        sleep 10

done

```

### execute and see output in another terminal tab

    $ ./write-ip.sh

### Task Scheduling CRON

    $ crontab -e

- edit the write-ip.sh file as below
```bash
    #!/bin/bash

    originalAddress=$(ifconfig | grep "inet " | head -n 1 | cut -d 'm' -f 1 | cut -$

    echo "$(date) $originalAddress" >> ~/ip.txt
```
- choose the editor nano for editing cron job
- schedule the ./write-ip.sh file for every one minute as like "* * * * * ./write-ip.sh"

NGINX Web Server
=====================

### updating local software repo

    $ sudo apt-get update

- if installing new software we should first run apt-get update to make sure my local packages are updated

### search for software

    $ apt search nginx

- if we dont know the name of the package we are searching then use this command

### installing nginx

    $ sudo apt-get install nginx

### installing nodejs

    $ sudo apt-get install nodejs

### create UI project and build it

    $ vue create .
    $ npm run serve
    $ npm run build

### make app directory for deployment 
    
    $ sudo mkdir -p /var/www/focusapp.net

- p aka --parent  no error if existing, make parent directories as needed

### copy everything from build directory dist to /var/www/app folder

    mahesh@mahesh-ubuntu:~/repo/byebye/dist$ cp -r * /var/www/focusapp.net


### ngnix uses text config file to describe site it hosts we can copy this file to our app
    $ sudo cp /etc/nginx//site-available/default /etc/nginx/sites-available/focusapp.net

### open the previosuly created file focusapp.net

    $ nano /etc/nginx/site-available/focusapp.net

### edit the configuration file as below

```bash
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /var/www/focusapp.net;

        # Add index.php to the list if you are using PHP
        index index.html;

        server_name localhost;

```

### creating link between config file and site

    $ sudo ln -s /etc/nginx/sites-available//focusapp.net /etc/nginx/sites-enabled/

- ln for link and -s for make symbolic link instead of hard link

### remove the default link enabled

    $ sudo rm /etc/nginx/sites-enabled/default 

### restart the nginx server

    $ sudo service nginx restart

### browse to the locahost url and congrats

    http://localhost/

SSH and Command Line
===================================

### 
    

