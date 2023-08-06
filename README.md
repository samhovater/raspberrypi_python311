# raspberrypi_python311

### Install various SSL related libraries
If you don't do this step first, pip doesn't work later
```bash
sudo apt install libssl-dev libncurses5-dev libsqlite3-dev libreadline-dev libtk8.6 libgdm-dev libdb4o-cil-dev libpcap-dev
```
### Download latest python source and extract
Get the latest python3.11 Gzipped source tarball from here: https://www.python.org/downloads/. In my case it's Python-3.11.4
```bash
wget https://www.python.org/ftp/python/3.11.4/Python-3.11.4.tgz
tar -zxvf Python-3.11.4.tgz 
```
### Switch to python directory and begin installation, this will take a few minutes
```bash
cd Python-3.11.4
./configure --enable-optimizations
sudo make altinstall
```
### OPTIONAL: Make Python3.11 the default python3 version on the system
This change enables `python3` to refer to the python 3.11 install you just did, as opposed to 3.7 that comes installed already
```bash
cd /usr/bin
sudo rm python3
sudo ln -s /usr/local/bin/python3.11 python3
```
Check that it's correct by typing `python3 --version`
(You could also do the same steps but with `python` instead of `python3`. Also check out [pyenv](https://github.com/pyenv/pyenv) for better python version management.

### Make sure it's working and install a package
Make a venv for installations (I like to put them in my ~/envs directory). This will take a few seconds
```bash
python3 -m venv ~/envs/py311-test
```
Now activate and upgrade pip
```bash
source ~/envs/py311-test/bin/activate
python -m pip install --upgrade pip
```
If that worked, you should be all set to install packages
```bash
python -m pip install scapy
```

This guide makes heavy references to this page: https://raspberrytips.com/install-latest-python-raspberry-pi/

This might not work/might bork your system, python installs are weird...
