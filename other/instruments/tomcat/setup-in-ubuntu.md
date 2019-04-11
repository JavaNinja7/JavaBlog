---
description: Описание установки в Ubuntu 18.04
---

# Setup in Ubuntu

Оригинал  [тут](https://community.vscale.io/hc/ru/community/posts/211836285-%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0-%D0%B8-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-Tomcat-9-%D0%BD%D0%B0-Ubuntu-16-04)

Сборка из исходников - [тут](http://dev-blogs.com/%D1%81%D0%B1%D0%BE%D1%80%D0%BA%D0%B0-%D0%B8-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-tomcat/)

Скачивание и распаковка как у обычных программ. А дальше интересно. Дальше для того чтобы запускать Tomcat рекомендуется его добавить в [службы](https://javaninja.gitbook.io/project/other/linux/notes/services-in-ubuntu) Ubuntu. Можно в принципе запускать его как обычную программу.. но думаю я еще пойму в чем преимущества служб.  А преимущества скорее всего в том, что можно запускать службы с разным приоритетом, в разном порядке, а также удобно перезагружать при их падении и так далее.

Итак, вот примерный юнит файл для tomcat:

```text
[Unit]
Description=Tomcat9
After=network.target

[Service]
Type=forking

# Environment=CATALINA_PID=/opt/tomcat9/tomcat9.pid
Environment=JAVA_HOME=/usr/lib/jvm/jdk-12
Environment=CATALINA_HOME=/opt/tomcat9
Environment=CATALINA_BASE=/opt/tomcat9
ExecStart=/opt/tomcat9/bin/startup.sh
ExecStop=/opt/tomcat9/bin/shutdown.sh

[Install]
WantedBy=multi-user.target
```

Сохраняем файл и перезапускаем менеджер служб:

```text
$ systemctl daemon-reload
```

Запускаем Tomcat через сервис и проверяем его статус:

```text
$ service tomcat start

$ service tomcat status
Loaded: loaded (/etc/systemd/system/tomcat.service: disabled; vendor preset: enabled)
Active: active (running) since Mon 2016-11-28 20:48:18 MSK; 6s ago
```

По умолчанию Tomcat запускается на 8080 порту. При желании его можно изменить.

#### Настройка

Рассмотрим основные директории в корневой папке Tomcat _**/opt/tomcat:**_

*  _**bin**_ - файлы и скрипты для запуска, остановки tomcat;
*  _**conf**_ - конфигурационные файлы, главный их которых server.xml;
*  _**lib**_ - используемые библиотеки;
*  _**logs**_ - директория для хранения всех логов сервера и работы запущенных приложений;
*  _**webapps**_ - папка для веб-приложений. По умолчанию Tomcat устанавливает свои приложения с примерами и веб-консоль для настройки.

Для изменения порта, на котором запускается Tomcat, необходимо открыть на редактирование файл server.xml в папке conf:

```text
$ nano /opt/tomcat/conf/server.xml
```

Находим запись:

```text
    <Connector port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
```

Меняем порт 8080 на желаемый, а затем перезапускаем Tomcat:

```text
$ service tomcat restart
```

Если Tomcat не доступен на запускаемом порту извне, то необходимо проверить настройки фаервола и открыть порт.

В файле server.xml можно также настроить поддержку SSL/TLS. Для этого нужно раскомментировать следующие строки:

```text
<Connector port="8443" protocol="org.apache.coyote.http11.Http11AprProtocol"
               maxThreads="150" SSLEnabled="true" >
        <UpgradeProtocol className="org.apache.coyote.http2.Http2Protocol" />
        <SSLHostConfig>
            <Certificate certificateKeyFile="conf/localhost-rsa-key.pem"
                         certificateFile="conf/localhost-rsa-cert.pem"
                         certificateChainFile="conf/localhost-rsa-chain.pem"
                         type="RSA" />
        </SSLHostConfig>
    </Connector>
```

Более подробно о всех поддерживаемых форматах и параметрах можно прочитать на официальной [странице](https://tomcat.apache.org/tomcat-9.0-doc/ssl-howto.html) Tomcat.

Если нужно настроить права доступа для работы с сервером Tomcat, то это можно сделать в файле _**tomcat-users.xml**_, который находится в папке conf. После внесения изменений следует перезагрузить сервер.

