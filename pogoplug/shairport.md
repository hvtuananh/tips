Configure and install shairport

    sudo pacman -Sy glibc #reinstall glibc just to be sure
    sudo pacman -Sy libao alsa-utils avahi libpulse
    sudo -i
    echo "use_mmap=no" >> /etc/libao.conf
    cd /etc
    wget https://dl.dropbox.com/u/42238/pogoplug/v2/asound.conf
    sudo pacman -Sy git-core
    exit
    mkdir ~/sources
    cd ~/sources
    git clone https://github.com/abrasive/shairport.git
    cd shairport
    ./configure
    make
    sudo make install
    sudo -i
    systemctl restart dbus
    systemctl start avahi-daemon
    systemctl enable avahi-daemon
    cd /etc/systemd/system
    wget http://dl.dropbox.com/u/42238/pogoplug/v2/shairport.service
    systemctl start shairport
    systemctl status shairport
    systemctl enable shairport
