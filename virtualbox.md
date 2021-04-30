# Increase disk size for Ubuntu
## Increase "physical" disk size
VirtualBox -> File -> Virtual Media Manager -> Select disk  -> Set size -> Apply

## Increase guest disk size
### Discover disk info
`lsblk`

Result example:
```bash
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda                         8:0    0 20.1G  0 disk
├─sda1                      8:1    0    1M  0 part
├─sda2                      8:2    0    1G  0 part /boot
└─sda3                      8:3    0   19G  0 part
  └─ubuntu--vg-ubuntu--lv 253:0    0   19G  0 lvm  /
```

### Remember the device and partition number, where lvm volume is located
e.g. /dev/sda 3 (ubuntu--vg-ubuntu--lv) from example

### Fix GPT
`sudo parted -l`

Write `Fix` to apply

### Increase partition size
`sudo parted /dev/sda`

`resizepart 3`

\* see the partition name and number in the previous steps

### Notify the system about changes
`sudo pvresize /dev/sda3`

### Increase lvm volume size
#### Remember the maximum possible size of the partition (sda3 from example)
`lsblk`

#### See lvm mapper device name
`df -h /`

#### Expand lvm volume to the entire disk
`sudo lvextend -L {partition_max_size} {lvm_mapper_device}`

e.g. `sudo lvextend -L 19G /dev/mapper/ubuntu--vg-ubuntu--lv`

### Check results (see increased free space)
`df -h`
