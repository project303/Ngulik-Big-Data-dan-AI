Seringkali terjadi kita kekurangan kapasitas disk pada root ("/"), karena biasanya kita menggunakan default configurasi pada saat instalasi. Berikut cara menambahkannya dengan memperkecil ruang pada /home

1. Backup content /home
2. Lihat disk yang digunakan
```
# df -h
Filesystem               Size  Used Avail Use% Mounted on
devtmpfs                 908M     0  908M   0% /dev
tmpfs                    919M     0  919M   0% /dev/shm
tmpfs                    919M  8.6M  911M   1% /run
tmpfs                    919M     0  919M   0% /sys/fs/cgroup
/dev/mapper/centos-root   50G  1.2G   49G   3% /
/dev/sda1               1014M  149M  866M  15% /boot
/dev/mapper/centos-home   75G   33M   75G   1% /home
tmpfs                    184M     0  184M   0% /run/user/0
```

3. Unmount and Remove home
```
umount /dev/mapper/centos-home
```
4. Remove logical volume
```
lvremove /dev/mapper/centos-home
```
5. Buat logigal volume home yang baru dengan ukuran lebih kecil
```
lvcreate -L 400GB -n home centos
mkfs.xfs /dev/centos/home
mount /dev/mapper/centos-home
```
6. Gunakan sisa kapasitas disk untuk root 
```
lvextend -r -l +100%FREE /dev/mapper/centos-root
```
7. Restore kembali isi home yang tadi dibackup


sumber:
https://qastack.id/server/771921/how-to-shrink-home-and-add-more-space-on-centos7

https://www.tecmint.com/move-home-directory-to-new-partition-disk-in-linux/

http://www.infolt.net/extending-root-partition-in-centos-7-by-resizing-home-partition/

