Task 1. Kernel Update
Цель домашнего задания
Научиться обновлять ядро в ОС Linux. Получение навыков работы с Vagrant, Packer и публикацией готовых образов в Vagrant Cloud. 

Описание домашнего задания
1) Обновить ядро ОС из репозитория ELRepo
2) Создать Vagrant box c помощью Packer
3) Загрузить Vagrant box в Vagrant Cloud

Дополнительные задания (не выполнены):
Ядро собрано из исходников
В образе нормально работают VirtualBox Shared Folders

Если я правильно понял, нужно описать скрипт обновления ядра.
Сначала импортируется репозиторий:
sudo yum install -y https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm 
# Установка нового ядра из репозитория elrepo-kernel
yum --enablerepo elrepo-kernel install kernel-ml -y

# Обновление параметров GRUB
grub2-mkconfig -o /boot/grub2/grub.cfg -- создаем файл конфигурации grub
grub2-set-default 0 --настраиваем загрузку с последней установленной версией ядра
echo "Grub update done."
# Перезагрузка ВМ
shutdown -r now


