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

# Another Path 
for FTP than USER HOME folder: /home/$USER/

## Add the following lines at the end of the config file ( /etc/vsftpd.conf ):

    user_sub_token=$USER

    local_root=/home/$USER/FTP


These settings lock the server users to the FTP folder within the home directory.

## FTP directory on RPI

    mkdir -p /home/pi/FTP/testftp
    chmod a-w /home/pi/FTP


# restart

    sudo service vsftpd restart
    
# test


# docs

https://phoenixnap.com/kb/raspberry-pi-ftp-server
