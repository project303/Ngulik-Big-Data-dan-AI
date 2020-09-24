Seringkali terjadi kita kekurangan kapasitas disk pada root ("/"), karena biasanya kita menggunakan default configurasi pada saat instalasi. Berikut cara menambahkannya dengan memperkecil ruang pada /home

1. Backup content /home
2. Unmount and Remove home
```
umount /dev/mapper/centos-home
```
3. Remove logical volume
```
lvremove /dev/mapper/centos-home
```
4. Buat logigal volume home yang baru dengan ukuran lebih kecil
```
lvcreate -L 400GB -n home centos
mkfs.xfs /dev/centos/home
mount /dev/mapper/centos-home
```
5. Gunakan sisa kapasitas disk untuk root 
```
lvextend -r -l +100%FREE /dev/mapper/centos-root
```
6. Restore kembali isi home yang tadi dibackup


sumber:
https://qastack.id/server/771921/how-to-shrink-home-and-add-more-space-on-centos7
https://www.tecmint.com/move-home-directory-to-new-partition-disk-in-linux/
http://www.infolt.net/extending-root-partition-in-centos-7-by-resizing-home-partition/

