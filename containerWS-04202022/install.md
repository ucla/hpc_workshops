# Installing Container software

This README will go over installing Apptainer on your local machine. You will want to install Apptainer on a computer that you have admin/sudo access so you can create containers.

## Using Workshp VM

THESE STEPS HAVE ALREADY BEEN DONE ON THE VM FOR THIS WORKSHOP

wscontainers.ova

https://ucla.box.com/s/ud10r0scf50hglo3pw6ktl9rx0dr0cxn

Username: wscontainer
password: wscontainer


## Install Apptainer


More detailed steps can be found on apptainer's website https://apptainer.org/docs/user/main/quick_start.html

## Install dependencies

You will need to first install the dependencies of Apptainer

```
sudo yum groupinstall -y 'Development Tools'
# Ensure EPEL repository is available
sudo yum install -y epel-release
# Install RPM packages for dependencies
sudo yum install -y \
   libseccomp-devel \
   squashfs-tools \
   cryptsetup \
   wget git
```

## Install Go

First, you will need to install the Go language 

```
export VERSION=1.17.5 OS=linux ARCH=amd64 
wget https://dl.google.com/go/go$VERSION.$OS-$ARCH.tar.gz 
sudo tar -C /usr/local -xzvf go$VERSION.$OS-$ARCH.tar.gz 
rm go$VERSION.$OS-$ARCH.tar.gz   
echo 'export PATH=/usr/local/go/bin:$PATH' >> ~/.bashrc 
source ~/.bashrc
```

This will install Go in `/usr/local` 


## Install Apptainer

```
export VERSION=1.0.1
wget https://github.com/apptainer/apptainer/releases/download/v${VERSION}/apptainer-${VERSION}.tar.gz 
tar -xzf apptainer-${VERSION}.tar.gz 
cd apptainer-${VERSION}

./mconfig 
make -C builddir 
sudo make -C builddir install

cd ..
rm -rf apptainer-${VERSION}*
```

## Install Docker

https://docs.docker.com/engine/install/centos/

```
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

sudo yum -y update
sudo yum install -y docker-ce docker-ce-cli containerd.io
sudo systemctl start docker
sudo systemctl status docker
```





