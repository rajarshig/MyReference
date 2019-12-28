# Jupyter Cheatsheet

## Run notebook on remote server with SSH tunneling
- 
```
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

## Start Jupyter without automatically opening browser
```
jupyter notebook --no-browser
```
## Debugging (IPython debugger)
- Import 
```from IPython.core.debugger import set_trace```
- Use
```
def add(a,b):
    '''
    Cell execution will stop here and open the command line for code inspection
    '''
    set_trace()  
    return a + b
```

## Debugging (pixie debugger)
pixiedust is a debugging tool which provides IDE like debugging capability in a Jupyter notebook
- Install
```pip install pixiedust```
- Use
```
import pixiedust
%%pixie_debugger # call magic function in the cell you want to debug
```
- Once run, it will create a Debug view with options like Breakpoint, Step over, Step into etc in that cell


## Reference
- [https://medium.com/@chrieke/jupyter-tips-and-tricks-994fdddb2057](https://medium.com/@chrieke/jupyter-tips-and-tricks-994fdddb2057)
-  [https://medium.com/codait/the-visual-python-debugger-for-jupyter-notebooks-youve-always-wanted-761713babc62](https://medium.com/codait/the-visual-python-debugger-for-jupyter-notebooks-youve-always-wanted-761713babc62)

- [https://ipython.readthedocs.io/en/stable/install/kernel_install.html#kernels-for-different-environments](https://ipython.readthedocs.io/en/stable/install/kernel_install.html#kernels-for-different-environments)

## How Jupyter works internally
[https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter/](https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter/)