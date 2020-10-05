## get live updates of a process

    watch ls -ltr 

## troubleshoot crash

    Alt+F2 and if you get a dialog for executing commands type restart
    Ctrl+Alt+F2 to switch to terminal console 2 (tty2), login and try killing gnome-screensaver and/or restarting a replacement gnome-shell with: 
    pkill gnome-screensaver 

## switch back to tty7 ( Ctrl+Alt+F7) to check your Gnome screen, if not, go back to tty2 and 

    gnome-shell --display :0.0 --replace & 
    (which was suggested before by steve and msdin respectively)

## troubleshoot crash

    psudo restart

## If both fail, then you need to restart your display manager (gdm, lightdm, kdm). Typically: 

    sudo service gdm restart
    sudo service lightdm restart

## to restart network

    sudo service network-manager restart\n\n DKMS: (If next boot fails, revert to initrd.img-4.4.0-75-generic.old-dkms image)


## autoupdate log

    tail -f XX.log

## check port

    get listening port for remote dektop
    sudo netstat -taupen | grep ssh

## make global

    sudo chmod +x
    cp usr/local/bin

## open java
    javaws strucalign.jnlp

## protect dirs from suckers!
    sudo chmod 0750 /home/lori #only your group can access
    sudo chmod 0700 /home/lori #only you can access

## purge PPAs
    sudo purge-ppa ppaname

## restart wifi

    sudo service network-manager restart

## start VPN session

    sudo openconnect vpn.domain.name

## install 

Install an RPM Package on Ubuntu Linux
Installing software on Ubuntu usually entails using Synaptic or by using an apt-get command from the terminal. Unfortunately, there are still a number of packages out there that are only distributed in RPM format.

There's a utility called Alien that converts packages from one format to the other. This doesn't always mean that an rpm will work on your system, though. You will need to install some prerequisite software packages in order to install alien, however. These packages include gcc and make.

## Run this command to install alien and other necessary packages:

    sudo apt-get install alien dpkg-dev debhelper build-essential

## To convert a package from rpm to debian format, use this command syntax. The sudo may not be necessary, but we'll include it just in case.

    sudo alien packagename.rpm

## To install the package, you'll use the dpkg utility, which is the internal package management tool behind debian and Ubuntu.

    sudo dpkg -i packagename.deb

## vbox

The best way to login to a guest Linux VirtualBox VM is port forwarding. By default, you should have one interface already which is using NAT. Then go to the Network settings and click the Port Forwarding button. Add a new Rule:

## Host port 3022, guest port 22, name ssh, other left blank. or from command line

    VBoxManage modifyvm myserver --natpf1 "ssh,tcp,,3022,,22"
    VBoxManage showvminfo myserver | grep 'Rule'

where 'myserver' is the name of the created VM. Check the added rules:
    
## That's all! Please be sure you don't forget to install an SSH server:

    sudo apt-get install openssh-server
    To SSH into the guest VM, write:

    ssh -p 3022 user@127.0.0.1

Where user is your username within the VM.

## system wide execute a script

    echo "alias shortcutname='/path/to/script'" >> ~/.bashrc

## more system wide (for usage through python scripts)
    sudo cp localscript /usr/local/bin/
    
## search installed packages

    apt list --installed | grep magick
    dpkg-query --list | grep magick

## search for running commands 
    pgrep -f 'wget' | xargs ps -f -p

## running docker container

    docker pull docker_container_name
    docker run docker_container_name program_name options

    List all images on your system:
    docker images

    List all containers you ran:
    docker ps -a

    Clean all the containers:
    docker container prune

    Remove a specific container:
    docker rm container_ID

## Manipulating pdf

    Extract comments from pdf to txt
    pdfcomments <infile.pdf> <outfile.txt>

    Extract pages from pdf
    pdftk myoldfile.pdf cat 1-2 4-5 output mynewfile.pdf
    pdftk myoldfile.pdf cat 1 2 4 5 output mynewfile.pdf

    Merge several pdfs into one
    pdftk pg_0001.pdf pg_0002.pdf pg_0004.pdf pg_0005.pdf output mynewfile.pdf
