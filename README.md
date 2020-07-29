# Raspberry Pi Hard Drive Analysis
Copy of commands and tools used to review hard drive content, then wipe for disposal.

# Check for Drives

Initial check:

```sudo fdisk -l```

To find mount points:

```lsblk -o "NAME,MAJ:MIN,RM,SIZE,RO,FSTYPE,MOUNTPOINT,UUID"```

# Xbox (Original) Hard Drive Check

I need to find further commands to use. For my own situation checking if old IDE/PATA drives

If the drive is shown as locked using this command it is likely an Xbox hard drive locked with a key stored in the eeprom:

```sudo smartctl -g security /dev/sda```

# To Shred

This is good enough for my needs. I do not have any senstive files on these drives.

```sudo shred -vfz -n 10 /dev/sdX```
