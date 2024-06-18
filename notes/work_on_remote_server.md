# Work on Remote Server
Tips and cookbooks related to working on a remote server. Modified from [this file](https://github.com/wy2136/learnPython/blob/master/get_started.md).

### Run graphical Linux applications on Windows 10
https://seanthegeek.net/234/graphical-linux-applications-bash-ubuntu-windows/

### ssh login

        ssh -Y username@remote_server
       
e.g. 
        
        ssh -Y punetid@tigressdata.princeton.edu

### Inquire information from netCDF files

        ncdump -h xxxx.nc

### Quick visualization of netCDF files

        ncview xxxx.nc


### ssh login without typing password
1. generate the keys (private + public)

        ssh-keygen -t rsa
> all use the defaults settings.

2. copy the  public key to the remote server

        ssh-copy-id username@remote_server

### Open Jupyter notebook on remote server and access it at local machine
1. Remote server terminal

        jupyter notebook --no-browser --port=8899 --ip=127.0.0.1
> port 8899 might be unavailable, in which case a different port # may be used.

In case you want to use Jupyter lab, you can run the following command instead:

        jupyter lab --no-browser --port=8899 --ip=127.0.0.1


2. Local machine terminal

        ssh -NL localhost:8899:localhost:8899 username@remote_server
> use the assigned port number in step 1 to replace 8899 when applicable.

In case you are not allowed to log in the remote server (e.g. tigressdata.princeton.edu) directly from an outside network, a jump server (e.g. nobel.princeton.edu) is needed if you do not want to use VPN:

        ssh -N -J username@jump_server -L localhost:8899:localhost8899 username@remote_server

3. Local machine browser

        http://localhost:8899
  
Or copy the full link (containing token info) seen in the remote server in step 1.

### The jupyterhub server at Princeton
[https://github.com/Resplandy/climate-hpc/blob/master/jupyterhub.md](https://github.com/Resplandy/climate-hpc/blob/master/jupyterhub.md)
