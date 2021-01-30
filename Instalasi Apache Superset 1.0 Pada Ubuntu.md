# Instalasi Apache Superset 1.0 Pada Ubuntu 


Pada area Business Intelligence (BI) terdapat banyak opsi tools data visualisasi yang dapat digunakan untuk mempermudah Data Analysts dalam melakukan banyak operasi dan analisa data. Tantangannya adalah bagaimana menyajikan data sehingga dapat dengan mudah dipahami dan interaktif bagi pengguna data non-teknis. Apache Superset adalah salah satu open source tools untuk Business Intelligence yang memiliki fitur cukup baik.

Pada pertengahan Januari 2021 lalu, Apache Superset telah merilis versi 1.0 yang juga menandakan bahwa Apache Superset telah masuk kedalam Top Project Apache.

## Persiapan Instalasi

Pada kali ini kita akan melakukan instalasi Apache Superset 1.0 pada Ubuntu. Versi yang digunakan adalah **Ubuntu Server 20.04**, tetapi seharusnya juga akan kompetibel dengan versi Ubuntu ataupun Debian lainnya.

Apache Superset membutuhkan beberapa paket pada Ubuntu. Perintah berikut memastikan paket-paket yang dibutuhkan terinstal
```
sudo apt-get install build-essential libssl-dev libffi-dev python3-dev python3-pip libsasl2-dev libldap2-dev
```

```
sudo
```

Setelah melakukan instalasi tools **python3-pip** maka akan tersedia 3 opsi python installation package yaitu **pip, pip3 dan pip3.8** (tergantung versi python 3 yang terinstall). PIP adalah package manager yang digunakan untuk melakukan instalasi paket-paket Python. Untuk seterusnya akan digunakan **pip3.8** sebagai tools untuk menginstall paket pada python.

Sangat direkomendasikan untuk melakukan instalasi Superset pada **python virtual environment**. Untuk itu kita install virtual environment tools yang dibutuhkan
```
sudo apt-get install python3-venv
```

Install virtual environment menggunakan pip3.8
```
pip3.8 install virtualenv
```

## Membuat Virtual Environment

Kita akan mambuat environment yang diberinama **superset**. Pemilihan nama virtual environment dapat disesuaikan dengan kebutuhan.
```
python3 -m venv superset
```
