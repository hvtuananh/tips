1. Create a mount directory
  
    mkdir /share

2. Create credential file with the following information

    username=<DomainName>/<user>
    password=<pass>
    
3. Add the following entry to `/etc/fstab`

    //<server>/<share_directory> /share cifs credentials=/location_of.credentials,sec=ntlm,uid=1000,forceuid,gid=1000,iocharset=utf8,file_mode=0664,dir_mode=0775 0 0
    #cifs: mount type
    #sec: login algorithm
    #uid and gid: user and group that will assume ownership of the share
    #iocharset: it's alway good to use utf-8
    #file_mode and dir_mode: it's not good to use 0777 as default
