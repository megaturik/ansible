# bitrix-env
Простой плейбук для установки стандартного битрикс-окружения, в CentOS 7.

Вы можете описать один или несколько сайтов, установив соответствующие переменные:

bitrix_php_type =  может принимать значение main, или additional, если = main - будет установленна как основная версия, если additional - как дополнительная /opt/remi...( используются репозитории remi)

bitrix_php_version = версия php

bitrix_env_user = системный пользователь под которым будет работать сайт.

bitrix_php_port = порт для php-fpm пула.

Пример:
```
- name: Playbook for Bitrix-ENV
  hosts: site1.bitrix.ru
  remote_user: root

  roles:
    - common
    - percona
    - firewalld
    - zabbix
    - { role: bitrix-env,
      bitrix_php_type: 'main',
      bitrix_php_version: 'php72',
      bitrix_env_user: site1,
      bitrix_php_port: '9001',
      bitrix_server_name: site1.bitrix.ru,
      bitrix_mysql_db: 'site1' }

```