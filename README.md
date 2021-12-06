# nginx-docker-template
Шаблон для проекта docker + nginx + что-то еще

# Введение
## ***1. Доменное имя***
Получите доменное имя, например, на сайте [reg.ru](https://reg.ru).

Также в файле [docker-compose.yml](docker-compose.yml) задайте переменную окружения ***NGINX_HOST*** по образцу вашим новым доменным именем, которое вы приобрели.
## ***2. Арендуйте хостинг***
## ***3. Переадресация***
Свяжите __ip__-адресс вашего хостинга, где будет запускаться проект, с доменным именем. Чаще всего это можно сделать там же, где покупали доменное имя.
## ***4. Настройка сертификатов***
Для начала вам нумно получить __ssl__ сертификат лоя вашего сайта. Можно настроить __certbot__ c __letsencrypt__, но в нашем случае мы будем использовать сертификаты c [reg.ru](https://reg.ru).

Нужно создать два файла по [этой инструкции](https://help.reg.ru/hc/ru/articles/4408046821009/) (смотреть только на пункты 1-2, дальше не надо).

Но в данном проекте файлы из инструкции мы переименуем так:
* __your_domain.crt__ -> ***my_ssl.crt***
* __your_domain.key__ -> ***private_my_ssl.key***

Далее внутри папки __nginx__ создать папку __certs__ и перенести туда эти файлы, чтобы в итоге получилось:

`./nginx/certs/my_ssl.crt`

`./nginx/certs/private_my_ssl.key`

## ***5. Работа с проектом***
Чтобы запустить проект вам понадобиться __docker__ и __docker-compose__. Как их установить рассказано [тут](https://docs.docker.com/engine/install/). Сразу стоить заметить, что иногда __docker-compose__ не всегда хорошо ставится на сервер вместе с __docker-engine__. И если __docker-compose__ не работает, то стоить попробовать его устаноить через __pip__ по этой [инструкции](https://docs.docker.com/compose/install/#install-using-pip). Если вы запускается проект на __windows__ сервере, то вам может понадобиться дополнительно установить ***CMake***, но к счатью на большинтсве __Linux__ серверов она работает уже из коробки.

### __5.1 Для *запуска* приложения на удалённом сервере__
выполните в консоли
```console
make up
```

### __5.2 Чтобы *прекратить* работу приложения__
выполните в консоли
```console
make down
```
