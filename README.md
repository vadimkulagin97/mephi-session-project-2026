Операционные системы семейства Unix
Студент: Кулагин Вадим ДН036

Описание

Минимальная установка Fedora 43 подготовлена для работы в локальной сети МИФИ и в других сетях:

- Настройка сети и hostname
- Установка ПО: nginx, tcpdump, libcap-ng-utils, vim, git
- Создание и монтирование файловой системы
- Настройка прав пользователей и SELinux
- Развёртывание веб-сервера с персонализированной страницей

Все настройки сохраняются после перезагрузки.

Настройка сети
- Статический IP (для сети МИФИ): 192.168.1.100/24
- Шлюз: 192.168.1.1
- DNS: 8.8.8.8
- Hostname: mephi-2026.domain.local

|Примечание: На моей машине использовался DHCP (динамический IP). Все сетевые настройки и веб-сервер работают корректно и при динамическом IP, что позволяет тестировать проект в любой сети.|

Результаты проверки сети: network_check.txt.

Программное обеспечение
- Пакеты из репозиториев: nginx, tcpdump, libcap-ng-utils, vim, git, policycoreutils-python-utils
- Локальный RPM tcpdump: скачан и установлен

Файловые системы и сервисы
- Второй диск /dev/sdb:
   - Раздел ext4, метка MEPHI_DATA
   - Точка монтирования: /data/mephi-web
   - fstab настроен для автоподключения
- Nginx:
   - Запущен и включён на автозапуск
   - Логи последних 5 минут: nginx_recent_logs.txt

Пользователи и доступ
- Пользователь: mephi-admin (пароль: P@ssw0rd2026)
- Группа: mephi-devs
- Права на /data/mephi-web: 2775, setgid
- SELinux: Enforcing, контекст httpd_sys_content_t
- tcpdump с capabilities: cap_net_admin,cap_net_raw=eip

Тестирование
 - Персонализированная страница: /data/mephi-web/index.html

|Hello from Student: Кулагин Вадим ДН036|

 - Проверка веб-сервера:

|curl http://localhost
curl http://<текущий_IP_машины>|

Результат: curl_output.txt

GitHub репозиторий
https://github.com/vadimkulagin97/mephi-session-project-2026

Загруженные файлы
- project_history.txt – история команд
- network_check.txt – результаты ping
- nginx_recent_logs.txt – логи nginx
- fstab.txt – автоподключение раздела
- selinux_status.txt – статус SELinux
- file_contexts.txt – контекст SELinux
- tcpdump_capabilities.txt – возможности tcpdump
- permissions.txt – права и владельцы
- users_groups.txt – информация о пользователях и группах
- index.html – персонализированная веб-страница
- curl_output.txt – проверка доступности веб-сервера
- mephi-nginx-screenshot.png – скриншот успешного отображения страницы
- tcpdump.rpm – локальный пакет tcpdump

Особенности
- Настройки сохраняются после перезагрузки
- Веб-сервер работает из /data/mephi-web
- Поддержка динамического IP для тестирования в других сетях
