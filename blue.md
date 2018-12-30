## driver for Ralink (Mediatek) RT3290 # located at https://github.com/loimu/rtbth-dkms # install 
    sudo add-apt-repository ppa:blaze/rtbth-dkms
    sudo apt-get update
    sudo apt install rtbth-dkms

## install dependencies control
    sudo apt-get install bluetooth bluez bluez-tools rfkill blueman

## pulseaudio ## This may be due to the pulseaudio-bluetooth-module package not being installed. Install it if it missing, 
    sudo apt install pulseaudio-module-bluetooth
    sudo nano /etc/bluetooth/main.conf

## add "AutoEnable=true"

    sudo modprobe rtbth
    sudo rfkill unblock bluetooth
    bluetoothctl
    sudo rfkill unblock bluetooth
    pulseaudio -k
    pulseaudio --start

## turn on
    sudo modprobe rtbth
    sudo rfkill unblock bluetooth

## manager application
    bluetoothctl

## options

    #help
    #scan on
    #trust 
    #pair
    #connect 
    
## then restart pulseaudio.
    pulseaudio -k  
    pulseaudio --start  

## to restart session
    sudo service bluetooth restart  
    killall pulseaudio  

## If the issue is not due to the missing package, the problem in this case is that PulseAudio is not catching up. A common solution to this problem is to restart PulseAudio. Note that it is perfectly fine to run bluetoothctl as root while PulseAudio runs as user. After restarting PulseAudio, retry to connect. It is not necessary to repeat the pairing.

## Continue trying second part only if above does not work for you:
## If restarting PulseAudio does not work, you need to load module-bluetooth-discover.

    sudo pactl load-module module-bluetooth-discover

## The same load-module command can be added to /etc/pulse/default.pa. If that still does not work, or you are using PulseAudio's system-wide mode, also load the following PulseAudio modules (again these can be loaded via your default.pa or system.pa):

    module-bluetooth-policy
    module-bluez5-device
    module-bluez5-discover
