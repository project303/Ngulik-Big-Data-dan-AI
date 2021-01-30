# Instalasi Apache Superset 1.0 Pada Ubuntu 

## Persiapan Instalasi

Pada kali ini kita akan melakukan instalasi Apache Superset 1.0 pada Ubuntu. Versi yang digunakan adalah **Ubuntu Server 20.04**, tetapi seharusnya juga akan kompetibel dengan versi Ubuntu ataupun Debian lainnya.

Apache Superset membutuhkan beberapa paket pada Ubuntu. Perintah berikut memastikan paket-paket yang dibutuhkan terinstal
```
sudo apt-get install build-essential libssl-dev libffi-dev python3-dev python3-pip libsasl2-dev libldap2-dev
```

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

Untuk menggunakan virtual environment yang telah dibuat, kita harus melakukan aktifasi
```
. superset/bin/activate
```

Setelah berada dalam virtual environment, lakukan update
```
pip3.8 install --upgrade setuptools pip
```

## Instalasi Apache Superset

Gunakan pip3.8 untuk melakukan instalasi
```
pip3.8 install apache-superset
```

Install pake Pillow
```
pip3.8 install Pillow
```

Insialisasi database
```
superset db upgrade
```

Jika muncul pesan error seperti contoh dibawah ini
```
ERROR: apache-superset 1.0.0 requires pandas<1.2,>=1.1.2, which is not installed.
ERROR: apache-superset 1.0.0 has requirement flask<2.0.0,>=1.1.0, but you'll have flask 1.0 which is incompatible.
```

Lakukan uninstall paket dan install dengan versi yang kompetibel dengan Superset
```
pip3.8 uninstall pandas
pip3.8 install pandas==1.1.5

pip3.8 uninstall sqlalchemy
pip3.8 install sqlalchemy==1.3.21

pip3.8 uninstall flask
pip3.8 install flask==1.1.0
```

## Configure Apache Superset

melakukan konfigurasi awal untuk dapat menjalankan Apache Superset
```
export FLASK_APP=superset
superset fab create-admin
```

Download data dan file-file contoh
```
superset load_examples
```

Buat role dan permission dafault
```
superset init
```

## Aktifkan Apache Superset

Aktifkan Apache Superset dan port yang akan kita gunakan adalah 8088
```
superset run -h 0.0.0.0 -p 8088
```

Buka browser dan akses ip address besarta portnya
