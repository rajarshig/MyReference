# Learning References
- [https://www.tecmint.com/](https://www.tecmint.com/)
- [https://www.cyberciti.biz](https://www.cyberciti.biz)
# Add user
- Create user with default setting
```
sudo useradd [username]
```
- Various setting & configurations can be provided. Reference [https://www.tecmint.com/add-users-in-linux/](https://www.tecmint.com/add-users-in-linux/)

# Run shell script files
-  Set execute permission on the file
```
chmod +x scriptname.sh
```
- Run the file
```
./scriptname.sh
/path/to/scriptname.sh
```

# Check file & folder size
```
df -h
du -sh [folder]
```

# Change root password

- Type the following command to become root user and issue passwd:
```
sudo -i
passwd
```
- OR set a password for root user in a single go:
```
sudo passwd root
```
- Test it your root password by typing the following command:
```
su -
```
- Reference
[https://www.cyberciti.biz/faq/change-root-password-ubuntu-linux/](https://www.cyberciti.biz/faq/change-root-password-ubuntu-linux/)

# Create user with sudo
- Create user
```
adduser username
```
- Give sudo permisson to new user
```
usermod -aG sudo username
```
- Reference
[https://www.digitalocean.com/community/tutorials/how-to-create-a-sudo-user-on-ubuntu-quickstart](https://www.digitalocean.com/community/tutorials/how-to-create-a-sudo-user-on-ubuntu-quickstart)


# RSync
- [https://www.cyberciti.biz/faq/use-rsync-to-backup-directory/](https://www.cyberciti.biz/faq/use-rsync-to-backup-directory/)

# SCP

- Server to local system
```
scp username@hostip:/filepath/filename ~/
```
- Local to server
```
scp filename username@hostip:~
```

# Counting files & directories
[https://www.theurbanpenguin.com/counting-files-directories-linux/](https://www.theurbanpenguin.com/counting-files-directories-linux/)

# Aliases

- Add aliases in .bash_aliases file
```
nano ~/.bash_aliases
```
- Add alias
```
alias gtst="git status"
```
- Activate 
```
source ~/.bash_aliases
```

# SSH key
- For issue 'sign_and_send_pubkey: signing failed: agent refused operation'
[https://askubuntu.com/questions/762541/ubuntu-16-04-ssh-sign-and-send-pubkey-signing-failed-agent-refused-operation](https://askubuntu.com/questions/762541/ubuntu-16-04-ssh-sign-and-send-pubkey-signing-failed-agent-refused-operation)
```
eval `ssh-agent -s`
ssh-add
```

# Search processes in local network with port or host IP
- Using `netstat` utility
```
netstat -anlp | grep '8015'
```

# Search in all processes with process name
- Using grep
```
ps aux | grep [processname]
```

# Kill a process
- By pid
```
sudo kill -9 [pid]
```
- By process name
```
sudo pkill -9 -f [processname] 
# eg. sudo pkill -9 -f dbeaver
```
- Other variations & reference
[https://stackoverflow.com/questions/3510673/find-and-kill-a-process-in-one-line-using-bash-and-regex](https://stackoverflow.com/questions/3510673/find-and-kill-a-process-in-one-line-using-bash-and-regex)

# Ubuntu
## View installed package with grep query
```
dpkg -l | grep postgres
```
## Remove installed package
```
sudo apt-get --purge remove postgresql
```

