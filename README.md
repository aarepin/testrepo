Инструкция:
1. Установить Vagrant
2. Установить VirtualBox, настроить путь расположения VM (должны быть только латинские буквы)
3. Скачать образ в папку с проектом https://app.vagrantup.com/ubuntu/boxes/bionic64/versions/20221201.0.0/providers/virtualbox.box (если проблемы со скачиванием напрямую)
4. Создать переменную оружения `VAGRANT_HOME=c:\path\to\thisproject` 
5. Запустить PowerShell и перейти в папку с проектом (где находятся все файлы включая этот README.md)
6. Выполнить команды(добавить локальный образ, запуск деплоя):<br>
   `vagrant box add ubuntu/bionic64 .\bionic-server-cloudimg-amd64-vagrant.box`<br> (если проблемы со скачиванием напрямую)
   `vagrant up`
6. Подключиться к хостам стенда по SSH к 192.168.56.101-192.168.56.104 с использованием логина `vagrant` и ключа `id_rsa.key.ppk`
7. Для остановки всех ВМ выполнить команду `vagrant halt`
8. После завершения работы для полного удаления стенда выполнить `vagrant destroy`
# from testrepo2
