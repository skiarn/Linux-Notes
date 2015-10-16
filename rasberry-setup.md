Pi sd card:

BSD Name:	disk3s1

unmount using disk utility.
sudo dd bs=1m if=/Users/andreaswestberg/Desktop/rasb/2015-05-05-raspbian-wheezy.img of=/dev/rdisk3
sudo diskutil eject /dev/rdisk3
#Install

###Prepare Rasberry Pi sd card:
Lookup disk name, ex, About this mac -> System Report... -> Storage view micro SD card.  
ex: `BSD Name:	disk3s1`

>Unmount using disk utility. Then execute.
```
 sudo dd bs=1m if=/Users/andreaswestberg/Desktop/rasb/2015-05-05-raspbian-wheezy.img of=/dev/rdisk3
 sudo diskutil eject /dev/rdisk3
```

###Setup correct protection, setup access from mac-book.
``` 
 cd /Users/andreaswestberg/.ssh/
 ssh-keygen -t rsa -b 4096 -C "rasberry"
 ```

**Copy to raspberry Pi authorised keys**
* Create dir with correct rights:  `mkdir ~/.ssh/;chmod 700 ~/.ssh`
* Paste: rasberry.pub mac-book key in vi ~/.ssh/authorized_keys  

**Configure access settings**
 `sudo vi /etc/ssh/sshd_config`
 Change port: Port XXXX
 >PasswordAuthentication no
 ´´´ 
 sudo /etc/init.d/ssh reload
 sudo /etc/init.d/ssh restart
 ´´´

**Update system**
```
sudo apt-get update
sudo apt-get upgrade
````



