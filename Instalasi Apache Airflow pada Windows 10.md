## 1. Aktifasi feature WSL pada Windows dan install Ubuntu
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```
untuk detailnya bisa mengunjungi: 
https://docs.microsoft.com/en-us/windows/wsl/install-manual

Untuk mengupdate ke WSL2, ikut Step 4 dan Step5

Install Ubuntu melalui Microsoft Store. Ikuti Step 6

Setelah selesai, lakukan update Ubuntu
```
sudo apt update && sudo apt upgrade
```


## 2. Konfigurasi automount windows file system


Hal ini berfungsi supaya folder yang ada dalam Windows dapat diakses langsung menggunakan Ubuntu terminal.
Buka Ubuntu terminal, dan buat file baru
```
sudo nano /etc/wsl.conf
```
Tambahkan baris berikut pada file tersebut, dan simpan kemudian keluar dari editor
```
[automount]
root = /
option = "metadata"
```
Sign Out pada Windows, dan Sign In kembali. Lakukan perintah berikut
```
ls /
```
maka akan tampil filder c atau d, sesuai yang ada pada Windows file system


## 3. Install conda
```
# download miniconda
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh

# instal miniconda
./Miniconda3-latest-Linux-x86_64.sh
```
Ikuti saja langkah yang disediakan oleh script. Pada opsi, ketik yes
```bash
Do you wish the installer to initialize Miniconda2
by running conda init? [yes|no]
[no] >>> yes
```

## 4. Buat environment airflow yg python 3.7
```
conda create --name airflow python=3.7 
```

## 5. Install Apache Airflow
```
conda activate airflow
pip3 install apache-airflow[gcp]==1.10.10 --constraint https://raw.githubusercontent.com/project303/Ngulik-Big-Data-dan-AI/master/airflow/airflow-python3.7.txt 
```

## 6. Home directory untuk Airflow

Buat home directory untuk Airflow pada Windows file system, misal pada D:\Airflow. Tambahkan variable $AIRFLOW_HOME pada file .bashrc
```
nano .bashrc
```
Tambahkan pada baris paling akhir
```
export AIRFLOW_HOME=/d/airflow
```
Keluar dari Ubuntu terminal, dan masuk kembali. Coba variable $AIRFLOW_HOME
```
echo $AIRFLOW_HOME
```
maka akan tampil
```
/d/airflow
```

## 7. Konfigurasi Apache Airflow

Masuk ke dalam directory $AIRFLOW_HOME
```
cd $AIRFLOW_HOME
```
Inisialisasi database Airflow
```
airflow initdb
```

## 8. Aktifkan Apache Airflow
Aktifkan schedluer
```
airflow scheduler
```

Bukan Ubuntu terminal lain, untuk mengaktifkan Airflow webserver
```
airflow webserver
```

Buka web browser
![alt text](images/Airflow.png "Apache Airflow")
