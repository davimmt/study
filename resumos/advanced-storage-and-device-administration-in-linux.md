## Sumário
* [Redudant Array of Independednt Disks (RAID)](#redudant-array-of-independednt-disks-raid)
* [Internet Small Computer System Interface (iSCSI)](#internet-small-computer-system-interface-iscsi)
* [Logical Volume Manager (LVM)](#logical-volume-manager-lvm)

---

### Redudant Array of Independednt Disks (RAID)

* Used to organize or combine a group of disks into one or more logical units.

- **General types:**
  - Mirroring: one disk exact copy of another disk;
  - Stripping: data is spread across more than on disk;
  - Parity: parity bits is store in the end of data to check integridy.

- **RAID levels:**
  - RAID 0: block-level stripping
  - RAID 1: data mirroring
  - RAID 4: block-level stripping with dedicated parity disk
  - RAID 5: block-level stripping with distributed parity disk
  - RAID 6: block-level stripping with double parity disk
  - RAID 10: RAID 1 + RAID 0
  - RAID 2 & 3: not used

- **Configuring a RAID**
  - Configure the Software RAID
    - mdadm -C </dev/new_device> -l <raidlevel> -n </dev/active_partitions> -x </dev/spare_partitions>

  - Make RAID persistent
    - mdadm -Dsv > /etc/mdadm.conf
      - run this after any raid partition changes to </dev/new_device>

  - Create the RAID's filesystem
    - mkfs.ext4 /dev/md0

  - Mount it
    - mkdir </mnt/raid>
    - mount -t ext4 </dev/new_device> </mnt/raid>
    - Get its UUID: blkid </dev/new_device>

  - Create the RAID's entry on fstab
    - vim /etc/fstab
    - UUID=<new_device_UUID> </mnt/raid> ext4 defaults 0 0

  - Check
    - mount -a
    - df -h

---

### Internet Small Computer System Interface (iSCSI)

**TARGET**
- yum install -y targetcli

- In the targetcli interface, create the <block> backstore from </dev/device>:
  - backstores/block create <block> </dev/device>

- Create the iSCSI target with a unique IQN:
  - iscsi/ create iqn.<yyyy-mm>.com.<name>.target:t1

- In the targetcli interface, change to the tpg1 directory:
  - cd iscsi/iqn.<yyyy-mm>.com.<name>.target:t1/tpg1/

- Create LUNs from the <block> backstore:
  -  luns/ create /backstores/block/<block>

- Create an acl for the iSCSI initiator:
  -  acls/ create iqn.<yyyy-mm>.com.<name>.initiator:init

- exit / systemctl enable target --now

**INITIATOR**
- yum install -y iscsi-initiator-utils

- Open the initiatorname.iscsi file:
  - vim /etc/iscsi/initiatorname.iscsi
    - iqn.<yyyy-mm>.com.<name>.initiator:init

- Discover and copy the iSCSI the target name:
  - iscsiadm -m discovery -t st -p <target_ip>

- Connect to the target:
  - iscsiadm -m node -T <target_name> -l

- Run iscsisd and iscsi
  - systemctl enable iscsid --now
  - systemctl enable iscsi --now

- Verify that the iSCSI devices were attached to the initiator host:
  - lsblk --scsi 

- Create a file system on </dev/device>:
  - mkfs.ext4 </dev/device>

- Create a mount points for the file systems on </mnt/mount_point>:
  - mkdir </mnt/mount_point>

- List the UUID for the mount points and copy them down:
  - lsblk -f

- Open /etc/fstab and write te UUID:
  - vim /etc/fstab
  - UUID=<DEV_UUID>   </mnt/mount_point> ext4    _netdev 0 0

- Mount the file systems and verify:
  - mount -a
  - df -h

---

### Logical Volume Manager (LVM)

- Device mapper framework that provides logical volume management for the Linux kernel.

**CREATING**
- parted </dev/device> mklabel msdos
- parted </dev/device> mkpart primary 1 400
- parted </dev/device> mkpart primary 401 800
- parted </dev/device> set 1 lvm on
- parted </dev/device> set 2 lvm on
- pvcreate </dev/device>
- vgcreate <virtual_group_name> </dev/device>
- lvcreate -L 200m <virtual_group_name> / lvcreate -l 50 <virtual_group_name> / lvcreate -l 20%VG <virtual_group_name>

- mkfs.ext4 /dev/<virtual_group_name>/<logic_volume_name>
- mkdir /mnt/<logic_volume_name>
- mount -t ext4 /dev/mapper/<virtual_group_name>-<logic_volume_name> /mnt/<logic_volume_name>

fstab:
- /dev/mapper/<virtual_group_name>-<logic_volume_name> /mnt/<logic_volume_name> ext4 defaults 0 0
  - OBS.: Don't use UUID in fstab for LVM; snapshots have the same.

  - lvextend -rL 400m /dev/<virtual_group_name>/<logic_volume_name>
  - lvreduce -rl -50 /dev/<virtual_group_name>/<logic_volume_name>

**SNAPSHOT**
- lvcreate -l 20%ORIGIN -s -n <snapshot_name> /dev/mapper/<virtual_group_name>/lvol0
  - lvextend -l 50%ORIGIN /dev/mapper/<virtual_group_name>/<snapshot_name>
  - lvreduce -L -25 /dev/mapper/<virtual_group_name>/<snapshot_name>

- lvconvert --merge <virtual_group_name>/<snapshot_name>
- umount /mnt/<logic_volume_name>
- lvchange -an /dev/<virtual_group_name>/<logic_volume_name>
- lvchange -ay /dev/<virtual_group_name>/<logic_volume_name>
- mount /dev/mapper/<virtual_group_name>-<logic_volume_name> /mnt/<logic_volume_name>
  - validate: pv/vg/lvdisplay, pv/vg/lvs