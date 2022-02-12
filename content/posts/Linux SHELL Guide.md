# Linux SHELL Guide

Shows all hidden files and folders along with normal ones.

```
ls -a
```

list lot of information about non-hidden files and directories

```
la -l
```

list above info for hidden files and directories too

```
ls -la OR ls -l -a
```

to switch to a dir same as cd but it just saves the path from which you came

```
pushd <path>
```

to switch back to dir from which you came with `pushd`.

```
popd
```

tells details of file

```
file <name of file>
```

search a directory or a file in data base

```
locate <name of file or directory>
```

or

```
mlocate <name of file or directory>
```

NOTE: run before locate/mlocate to update database

```
sudo updatedb
```

see calander

```
cal
```

see if command is installed or not, returns path of the command

```
which <command>
```

brief one-line discription of what a command can do

```
whatis <command>
```

shows the commands related to or contain given keyword

```
apropos <keyword>
```

equivalent to apropos but show information in readable format

```
man <keyword>
```

copy a files and directories

```
cp -r<path of the file to be copied> <name of the copied file>
```

move files and directories

```
mv <path of file> <path to be moved>
```

delete/remove files

```
rm <file>
```

delete/remove directories

```
rm -r <directorie>
```

create a text file.

```
touch <file_name>
echo 'write text here' > textfile.txt
printf 'write \\ntext \\nhere' > textfile.txt
```

NOTE: use printf for format the text

show the content of a text file on terminal

```
cat <file>
```

write into the text file

```
cat >> <file_name>
```

copy file1 to file2

```
cat <file1> >> <file2>
```

- “>” operator will overwrite the existing data
- “>>” operator will append data

bash text editor for editing files in CLI format. there are others too

```
nano <file1>
ls -la ~ >> textfile.txt
```

switch to root user or root account, to exit type exit

```
sudo -s
```

switch to another user account, to exit type exit

```
su - <username>
```

move to root user account

```
su
su -
```

see how many accounts are logged in

```
users
```

executable permission to file for everyone

```
chmod +x <file_name>
```

![Screenshot from 2021-07-29 21-15-38.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7ff5704f-89b5-4c80-bb1d-46f694263177/Screenshot_from_2021-07-29_21-15-38.png)

get the PID of programme and all its instances

```
pidof brave
```

see the running process

```
top
```

kill process by their name

```
pkill brave
killall brave
```

kill process by their PID

```
kill <PID of the process>
```

get the snapshot of top (Best)

```
ps aux | grep <name of programme or running file or path or aything relatable to it>
```

find the exact package

```
apt search --names--only ___
```

Install .deb files

```
sudo dpkg -i /path/to/.deb/file
```

`sudo apt-get install -f` <fixes any dependencies which dpkg did not full fill>

`apt-cache showpkg/show package-name` <shows info about package if it is installed>

`apt-cache depends package-name` <see installed package dependencies>

see package info

```
dpkg-deb -I package.deb
```

create and edit cronjobs (scheduled server tasks)

```
crontab -e
```

see cronjobs on terminal

```
crontab -l
```

create a SCREEN session with name

```
screen -S <name_of_session>
```

see detached and running screen session

```
screen -ls
```

reattach to detached screen session

```
screen -r <pid_of_screen_session>
```

see cronjobs-logs with

```
journalctl -t CROND
```

install/extract tar files

```
tar xvf <file_name>
```

Find Public IPv4 address

```
dig -4 TXT +short o-o.myaddr.l.google.com @ns1.google.com
```

Fix bluetooth in ubuntu>18.04

```
sudo modprobe -r btusb && sudo modprobe btusb
```

Instll/Add PPA repository

`sudo add-apt-repository ppa:dr-akulavich/lighttable` // adds repository link to /etc/apt/source.list

```
sudo apt-get update
```

`sudo apt-get install lighttable-installer` // installing the software

Remove PPA repository and link

[listppa.sh](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/255f1de3-f939-4253-81fd-3135882692d3/listppa.sh)

Use the above script to see the list of installed PPAs

now remove the ppa

```
sudo add-apt-repository --remove ppa:bluetooth/bluez
```

Check mounted/connected disks to the system

```
lsblk
```

Command for burning USB {notice the of and if carefully}

```bash
sudo dd bs=4M if=Downloads/endeavouros-2021.08.27-x86_64.iso of=/dev/sdb conv=fdatasync status=progress
```

Set-up ssh key for connecting to git

`eval `ssh-agent``

```
chmod 400 <private_key_file>
ssh-add ~/.ssh/<private_key_file>**>> /dev/null 2>&1**
```

https://stackoverflow.com/questions/10508843/what-is-dev-null-21

## Pacman, AUR

List dependency of a package

```bash
pacman -Si
or
pacman -Si package_name | grep 'Depends On'
or
pactree -s package_name
or
pactree -sr package_name #see reverse dependency
or
pactree package_name -lu #in format for reinstalling dependency
```

See locally installed packages~ AUR(s) or installed with AUR helpers.

```bash
pacman -Qm or pacman -Qmq
```

To list all the **Fonts installed in your system**

```bash
fc-list
```

## How to add users in arch Linux

1. do `adduser NAME` or `useradd NAME` whichever is present in your system.
2. then set password for `NAME` with `passwd NAME`

- Give `sudo` privileges to `NAME`

  To give sudo rights to a user you can add him to group `wheel` . Wheel is group for users who want every system administrator privileges. you can add a user to group `wheel` with `gpasswd -a NAME wheel` , notice to give users of wheel group root privileges in `/etc/sudoers` (always edit `/etc/sudoers` with `sudo visudo` to avoid Error(s) ) file otherwise even if you add users to wheel group they will not be able to use sudo. add this line `%wheel ALL=(ALL) ALL` for wheel group users in `/etc/sudoers.`

  Or you can custom give a user root privilages like by adding this line

  `USER_NAME ALL=(ALL) ALL` to `/etc/sudoers` if you choose to do this then you don’t need to add `NAME` to `wheel` group.

  but the first approach is recommended.