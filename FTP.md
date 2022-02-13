# udpate os

    sudo apt update
    sudo apt full-upgrade -y
    
# install    
    
    sudo apt install -y vsftpd
    
# config

    sudo nano /etc/vsftpd.conf
    
change the values

    write_enable=YES

    local_umask=022

    chroot_local_user=YES

Find the following line:

    anonymous_enable=YES

Change it to:

    anonymous_enable=NO

Add the following lines at the end of the config file:

    user_sub_token=$USER

    local_root=/home/$USER/FTP


These settings lock the server users to the FTP folder within the home directory.
    
# test

# docs

https://phoenixnap.com/kb/raspberry-pi-ftp-server
