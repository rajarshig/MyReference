# Jupyter Cheatsheet

## Run notebook on remote server with SSH tunneling
- ```
ssh -L 8000:localhost:8888 username@your_server_ip
source activate conda_env
jupyter notebook
```
- [https://www.digitalocean.com/community/tutorials/how-to-install-run-connect-to-jupyter-notebook-on-remote-server#step-3-%E2%80%94-connecting-to-the-jupyter-notebook-application-with-ssh-tunneling](https://www.digitalocean.com/community/tutorials/how-to-install-run-connect-to-jupyter-notebook-on-remote-server#step-3-%E2%80%94-connecting-to-the-jupyter-notebook-application-with-ssh-tunneling)

## Custom kernel in Virtualenv
- Install Ipython in Virtualenv
- Install custom kernel in Virtualenv
```
ipython kernel install --user --name=py_work
```
- You can use the same kernel from system install jupyter / other jupyter installations