**Find usb UUID name.**
Connect usb and find uuid name, example: mine is: 7C66-1EE4 -> ../../sda1
```cat /var/log/messages```

**Mount usb disk.**
I mount my usb at /mnt/usb. I register my uuid to the fstab file so that it automaticly mounts on boot.
```
   mkdir -p /mnt/usb;
   sudo cp /etc/fstab /etc/fstab.old; 
   echo 'UUID=7C66-1EE4 /mnt/usb vfat defaults 0 2' | sudo tee -a /etc/fstab; 
   sudo mount -a;
   
 ```

**Make swap**
* Saves swap configuration to dphys-swapfile.
* Creates a swapfile on my usb.
* Create a swap memory space and turn it on.
* Register swapfile in fstab so that it mounts on bootup.
```
   sudo printf '%s\n%s\n' 'CONF_SWAPSIZE=1024' 'CONF_SWAPFILE=/mnt/sda1/swap.file' | sudo dd of=/etc/dphys-swapfile;
   sudo dd if=/dev/zero of=/mnt/usb/swap.file bs=1M count=1024; sudo chmod 600 /mnt/usb/swap.file;
   sudo mkswap /mnt/usb/swap.file; sudo swapon /mnt/usb/swap.file;
   sudo cp /etc/fstab /etc/fstab.old; echo '/mnt/usb/swap.file none swap defaults 0 0' | sudo tee -a /etc/fstab;
```

**Success**
Shows mount point statistics
```df -h /mnt/usb/```

Shows memory statistics
```free -h```
