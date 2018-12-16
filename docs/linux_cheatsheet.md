# Add user

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

# SCP

- Server to local system
```
scp username@hostip:/filepath/filename ~/
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
# Ubuntu
## View installed package with grep query
```
dpkg -l | grep postgres
```
## Remove installed package
```
sudo apt-get --purge remove postgresql
```