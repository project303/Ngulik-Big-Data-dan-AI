# Installing Ubuntu on WSL

## Enable WSL

Untuk system yang belum diaktifkan fitur WSL
1. Open PowerShell as Administrator (Start menu > PowerShell > right-click > Run as Administrator) and enter this command:

dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

https://docs.microsoft.com/en-us/windows/wsl/install-manual


sudo apt update && sudo apt upgrade

sudo apt install python3-pip

pip3 --version

pip3 install apache-airflow[gcp,statsd,sentry]==1.10.10


https://insaid.medium.com/setting-up-apache-airflow-in-windows-using-wsl-8e0a87cd4945
