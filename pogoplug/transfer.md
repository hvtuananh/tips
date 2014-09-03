Transfer OS from one USB to another

  fdisk /dev/sdb #/dev/sda is the main USB
  #press p to list, o to delete all partitions, n to create with config p, 1, <default>, <default>
  mke2fs -L Label -j /dev/sdb1
  mkdir /mnt/usb
  mount /dev/sdb1 /mnt/usb
  rsync -av --exclude=/mnt/usb/ --exclude=dev --exclude=run --exclude=proc --exclude=sys / /mnt/usb/
  sync
