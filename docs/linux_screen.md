
## Basics

- Start
```
screen -S [screen_view_name]
```
- Entered into screen view. now run command
eg. python script 

- Detach
```
screen -d res_gid
```
- Re attach
```
screen -d -r [ID]
```
- List all running Screen
```
screen -ls
```

- Ctrl-a followed by d: detach a screen session without stopping it
- ctrl-a followed by k: kill session

## Reference:
[https://www.rackaid.com/blog/linux-screen-tutorial-and-how-to/](https://www.rackaid.com/blog/linux-screen-tutorial-and-how-to/)
[https://linoxide.com/linux-command/15-examples-screen-command-linux-terminal/](https://linoxide.com/linux-command/15-examples-screen-command-linux-terminal/)