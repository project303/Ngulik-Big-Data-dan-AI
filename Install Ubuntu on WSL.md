# Installing Ubuntu on WSL

## Enable WSL

Untuk system yang belum diaktifkan fitur WSL
1. Open PowerShell as Administrator (Start menu > PowerShell > right-click > Run as Administrator) and enter this command:

dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

https://docs.microsoft.com/en-us/windows/wsl/install-manual


sudo apt update && sudo apt upgrade

sudo apt install python3-pip

pip3 --version

sudo pip3 install virtualenv

virtualenv airflow_env

source airflow/bin/activate

pip3 install apache-airflow[gcp,statsd,sentry]==1.10.10


conda install airflow=1.10.10

conda install attrs=19.3.0
conda install markupsafe=2.0.1
conda install wtforms=2.3.3

conda install flask=1.1.1
conda install sqlalchemy=1.3.15
conda install marshmallow-sqlalchemy=0.24.0
conda install sqlalchemy=1.3.15
conda install cattrs==1.0.0
 

pip3 install cryptography
 
pip3 install apache-airflow[gcp]==1.10.10 --constraint https://raw.githubusercontent.com/project303/Ngulik-Big-Data-dan-AI/master/airflow/airflow-python3.7.txt

pip3 install pyspark==2.4.5

echo $AIRFLOW_HOME

deactivate

https://insaid.medium.com/setting-up-apache-airflow-in-windows-using-wsl-8e0a87cd4945

https://github.com/apache/airflow/issues/8211


conda install jupyter notebook

https://github.com/andreax79/airflow-code-editor

https://stackoverflow.com/questions/48986732/airflow-creating-a-dag-in-airflow-via-ui


Jika airflow resetdb, trus airflow webserver, muncu error

Error: Already running on PID 6244 (or pid file '/home/marcofumagalli/airflow/airflow-webserver.pid' is stale)

maka lakukan

sudo lsof -i tcp:8080

kill -9 semua pid

delete file airflow-webserver.pid dan coba lagi airflow webverser
