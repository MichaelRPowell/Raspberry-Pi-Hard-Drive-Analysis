# Raspberry Pi Hard Drive Analysis
Copy of commands and tools used to review hard drive content, then wipe for disposal.

## Check for connected USB Devices

I run this first to make sure the USB to IDE/PATA device is detected.

```lsusb```

## Check for Drives

Initial check for drives connected:

```sudo fdisk -l```

Find mount points for connected drives:

```lsblk -o "NAME,MAJ:MIN,RM,SIZE,RO,FSTYPE,MOUNTPOINT,UUID"```

## Xbox (Original) Hard Drive Check

I need to find further commands to use. For my own situation checking if old IDE/PATA drives

If the drive is shown as locked using this command it is likely an Xbox hard drive locked with a key stored in the eeprom:

```sudo smartctl -g security /dev/sda```

## Find Bad Blocks and Log

This command will scan for bad blocks and log the results to badblocks.txt

```sudo badblocks -v /dev/sdX# > badblocks.txt```

## Mount SSHFS Share for Backup Storage

```sudo sshfs -o allow_other (Remote User)@(IP):(Remote Folder) (Local Folder)```

## Create DD Backup

```sudo dd if=/dev/sdX of=/folder/backupname.dd conv=noerror,sync status=progress```

## To Shred

This is good enough for my needs. I do not have any senstive files on these drives.

```sudo shred -vfz -n 10 /dev/sdX```
