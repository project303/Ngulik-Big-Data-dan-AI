{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Instalasi Apache Superset 1.0 Pada Ubuntu "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Pada area Business Intelligence (BI) terdapat banyak opsi tools data visualisasi yang dapat digunakan untuk mempermudah Data Analysts dalam melakukan banyak operasi dan analisa data. Tantangannya adalah bagaimana menyajikan data sehingga dapat dengan mudah dipahami dan interaktif bagi pengguna data non-teknis. Apache Superset adalah salah satu open source tools untuk Business Intelligence yang memiliki fitur cukup baik."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Pada pertengahan Januari 2021 lalu, Apache Superset telah merilis versi 1.0 yang juga menandakan bahwa Apache Superset telah masuk kedalam Top Project Apache."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Persiapan Instalasi"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Pada kali ini kita akan melakukan instalasi Apache Superset 1.0 pada Ubuntu. Versi yang digunakan adalah **Ubuntu Server 20.04**, tetapi seharusnya juga akan kompetibel dengan versi Ubuntu ataupun Debian lainnya."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Apache Superset membutuhkan beberapa paket pada Ubuntu. Perintah berikut memastikan paket-paket yang dibutuhkan terinstal"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# sudo apt-get install build-essential libssl-dev libffi-dev python3-dev python3-pip libsasl2-dev libldap2-dev"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Setelah melakukan instalasi tools **python3-pip** maka akan tersedia 3 opsi python installation package yaitu **pip, pip3 dan pip3.8** (tergantung versi python 3 yang terinstall). PIP adalah package manager yang digunakan untuk melakukan instalasi paket-paket Python. Untuk seterusnya akan digunakan **pip3.8** sebagai tools untuk menginstall paket pada python.\n",
    "\n",
    "--pip python adalah"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Sangat direkomendasikan untuk melakukan instalasi Superset pada **python virtual environment**. Untuk itu kita install virtual environment tools yang dibutuhkan"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "metadata": {},
   "outputs": [],
   "source": [
    "# sudo apt-get install python3-venv"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Install virtual environment menggunakan pip3.8"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {},
   "outputs": [],
   "source": [
    "# pip3.8 install virtualenv"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Membuat Virtual Environment"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Kita akan mambuat environment yang diberinama **superset**. Pemilihan nama virtual environment dapat disesuaikan dengan kebutuhan."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# python3 -m venv superset"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Untuk menggunakan virtual environment yang telah dibuat, kita harus melakukan aktifasi"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [],
   "source": [
    "# . superset/bin/activate"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Virtual environment yang sedang aktif akan tampil pada shell **(superset) yava@lunchbox:/home/yava$**. Dalam hal ini saya menggunakan environment **superset** dengan user **yava** pada host **lunchbox** dan berada dalam folder **/home/yava**."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Setelah berada dalam virtual environment, lakukan update"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# pip3.8 install --upgrade setuptools pip"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Instalasi Apache Superset"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Langkah-langkah berikut kita akan melakukan instalasi Apache Superset dalam virtual environment superset yang telah aktif sebelumnya. Gunakan pip3.8 untuk melakukan instalasi"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [],
   "source": [
    "# pip3.8 install apache-superset"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Install pake Pillow, untuk menghindari **warning** pada langkah berikutnya "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [],
   "source": [
    "# pip3.8 install Pillow"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Insialisasi database yang digunakan oleh **Superset**."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {},
   "outputs": [],
   "source": [
    "# superset db upgrade"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Jika muncul pesan error seperti contoh dibawah ini"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "ERROR: apache-superset 1.0.0 requires pandas<1.2,>=1.1.2, which is not installed.\n",
    "ERROR: apache-superset 1.0.0 has requirement flask<2.0.0,>=1.1.0, but you'll have flask 1.0 which is incompatible."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Pesan error diatas disebabkan karena versi Pandas, Flask ataupun SQLalchemy yang tidak sesuai dengan Apache Superset. Lakukan uninstall paket dan install dengan versi yang kompetibel dengan Superset"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [],
   "source": [
    "# pip3.8 uninstall pandas\n",
    "# pip3.8 install pandas==1.1.5\n",
    "\n",
    "# pip3.8 uninstall sqlalchemy\n",
    "# pip3.8 install sqlalchemy==1.3.21\n",
    "\n",
    "# pip3.8 uninstall flask\n",
    "# pip3.8 install flask==1.1.0"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Configure Apache Superset"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Setelah selesai dengan instalasi, berikutnya kita akan melakukan konfigurasi awal untuk dapat menjalankan Apache Superset"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [],
   "source": [
    "# export FLASK_APP=superset\n",
    "# superset fab create-admin"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Masukkan nama user yang akan dijadikan admin pada superset. Dalam hal ini kita menggunakan **admin** sebagai nama user"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "Username [admin]: admin\n",
    "User first name [admin]: admin\n",
    "User last name [user]: superset\n",
    "Email [admin@fab.org]: admin@em.com\n",
    "Password:\n",
    "Repeat for confirmation:"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Download data dan file-file contoh penggunaan supaya dapat dengan mudah mempelajari superset melalui contoh yang disediakan"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# superset load_examples"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Buat role dan permission standar"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# superset init"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Aktifkan Apache Superset"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Apache Superset adalah aplikasi berbasis web, sehingga kita perlu mengaktifkannya. Port yang akan kita gunakan adalah 8088"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# superset run -h 0.0.0.0 -p 8088"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Opsi **-h 0.0.0.0** digunakan supaya dapat diakses melalui komputer lain"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Mengakses Apache Superset"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Buka Superset melalui web browser dengan url : **ip-addr:8088**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.7.7"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
