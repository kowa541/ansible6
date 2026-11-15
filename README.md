# ansible6
# Лабораторная работа П06: Использование Ansible Role для виртуальных хостов Nginx

## Цель работы
Структурирование кода Ansible с использованием Ролей (Roles) для развертывания и конфигурации нескольких виртуальных хостов (Virtual Hosts) на одном веб-сервере.

## Инфраструктура
- **Управляющая машина:** `10.0.2.4`
- **Целевая машина:** `10.0.2.3`

## Структура роли `nginx_vhosts`
- `defaults/main.yml` — определение переменной `sites` со списком доменов (`mehmat.ru`, `fizfak.ru`, `etis.com`).
- `tasks/main.yml` — основные задачи: установка Nginx, создание директорий, деплой шаблонов, создание симлинков в `sites-enabled`, удаление дефолтного сайта.
- `templates/index.html.j2` — шаблон индексной страницы с динамической подстановкой имени домена (`{{ item }}`) и имени хоста.
- `templates/site.conf.j2` — шаблон конфигурационного файла Nginx для виртуального хоста.
- `handlers/main.yml` — обработчик для перезапуска службы Nginx при изменении конфигураций (`notify: restart nginx`).

## Результаты
На целевой машине развернуты три независимых виртуальных хоста. Корректность маршрутизации проверена через отправку HTTP-запросов с подменой заголовка Host.

##  Доказательства 

<img width="1227" height="728" alt="image" src="https://github.com/user-attachments/assets/4cbec5bc-18ca-4bcf-b069-4a884fd0593a" />
<img width="1300" height="252" alt="image" src="https://github.com/user-attachments/assets/7ee1e782-f48e-49ee-bd96-c866c66f030d" />


<img width="895" height="531" alt="image" src="https://github.com/user-attachments/assets/809b2a25-6d2c-40a7-8299-985100bd7f10" />
<img width="1040" height="298" alt="image" src="https://github.com/user-attachments/assets/08e87adf-259e-4503-b125-fb8121276dbd" />

