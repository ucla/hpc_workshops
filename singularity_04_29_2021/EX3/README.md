# Using a container

Building a container for the PySCF python application

https://pyscf.org

First, create a container with PySCF installed

This is done on your local machine that you have Singularity installed (and have root access)

Download a Ubuntu container from dockerhub

```
sudo singularity build --sandbox ubuntu/ docker://ubuntu:20.04 
```

Get inside container

```
sudo singularity shell --writable ubuntu/ 
```

Install pyscf inside container

```
apt update
apt install python3-dev python3-pip
pip3 install pyscf
```

Convert Sandbox to SIF

```
sudo singularity build --sandbox ubuntu/ docker://ubuntu:20.04 
```

Transfer SIF to Hoffman2, then login 

```
scp pyscf.sif dtn.hoffman2.idre.ucla.edu:
ssh hoffman2.idre.ucla.edu
```

Submit job

```
qsub pyscf.job
```


 
