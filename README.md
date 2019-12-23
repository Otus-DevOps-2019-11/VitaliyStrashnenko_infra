# VitaliyStrashnenko_infra
VitaliyStrashnenko Infra repository

#Домашнее задание ssh

ssh-add -L
Could not open a connection to your authentication agent.
Поправил
eval `ssh-agent -s`
ssh-add ~/.ssh/appuser
редактируем файл /etc/ssh/ssh_config
раскаментироать и задать
	ForwardAgent yesForwardAgent yes
	IdentityFile ~/.ssh/appuser
Одной командой заходим через bastion на someinternalhost

ssh -i ~/.ssh/appuser -t -A appuser@146.148.123.146 ssh 10.132.0.6 #Одной командой

Дополнительное задание

Дописать в конфигурацинный файл /etc/ssh/ssh_config

Host someinternalhost
       HostName 146.148.123.146
       Port 22
       User appuser
       IdentityFile ~/.ssh/appuser
       RequestTTY force
       RemoteCommand ssh 10.132.0.6
       ForwardAgent yes

bastion_IP = 146.148.123.146
someinternalhost_IP = 10.132.0.6
