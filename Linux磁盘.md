## 查看分区挂在情况

### lsblk

NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0   20G  0 disk
├─sda1   8:1    0  300M  0 part /boot
├─sda2   8:2    0    2G  0 part [SWAP]
└─sda3   8:3    0 17.7G  0 part /
sr0     11:0    1 1024M  0 rom

### lsblk -f

NAME   FSTYPE LABEL UUID                                 MOUNTPOINT
sda
├─sda1 xfs          d21eaec7-22bf-4e0d-9513-6ad9d1ecd854 /boot
├─sda2 swap         f13d54e6-8db1-44ff-91fe-dca3fcf11ade [SWAP]
└─sda3 xfs          9da6bba5-ae94-4d86-bb00-561a9c63c3ac /
sr0
