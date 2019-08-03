# Jupyter Cheatsheet

## Run notebook on remote server with SSH tunneling
- ```
ssh -L 8000:localhost:8888 username@your_server_ip
source activate conda_env
jupyter notebook
```
- [https://www.digitalocean.com/community/tutorials/how-to-install-run-connect-to-jupyter-notebook-on-remote-server#step-3-%E2%80%94-connecting-to-the-jupyter-notebook-application-with-ssh-tunneling](https://www.digitalocean.com/community/tutorials/how-to-install-run-connect-to-jupyter-notebook-on-remote-server#step-3-%E2%80%94-connecting-to-the-jupyter-notebook-application-with-ssh-tunneling)

## Custom kernel in env
- Install Ipython in env
- Install custom kernel in env
```
pip install --user ipykernel
python -m ipykernel install --user --name myenv --display-name "conda_base"
```
- You can use the same kernel from system installed jupyter / other jupyter installations
- Reference
[https://ipython.readthedocs.io/en/stable/install/kernel_install.html#kernels-for-different-environments](https://ipython.readthedocs.io/en/stable/install/kernel_install.html#kernels-for-different-environments)

## How Jupyter works internally
[https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter/](https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter/)