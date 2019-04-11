---
description: Службы в Ubuntu
---

# Services in Ubuntu

Оригинал [про службы тут](https://losst.ru/upravlenie-sluzhbami-linux) и [про юниты тут](https://blog.pridybailo.com/%D0%B7%D0%B0%D0%BF%D1%83%D1%81%D0%BA-%D1%81%D0%BB%D1%83%D0%B6%D0%B1-%D0%B2-linux/) .

**Службы** - это работающие в фоне программы,  которые выполняются в фоне; пользователь не имеет к ним прямого доступа. Например, службы следят за состоянием системы, обеспечивают автоматическое подключение внешних устройств и сети, позволяют процессам взаимодействовать с оборудованием \(dbus\). Также в виде служб реализованы различные веб-серверы и серверы баз данных. 

**systemd** - "системный демон", служба в linux которая отвечает за запуск других служб и мониторинг. Позволяет запускать службы не только параллельно, но и в сложном порядке в зависимости от места в иерархии наследования служб. 

**systemctl** - главная команда для отслеживания и контроля состояния systemd

**service** - запускает скрипт инициализации System V или юнит systemd

**Юнит Systemd**

Служба в Systemd описывается файлом юнита\( `/etc/systemd/system/name.service`\), в нем описано что с ней нужно делать и как себя вести. Существуют такие типы служб:

* **service** - обычная служба, программа
* **target** - группа служб
* **automount** - точка автоматического монтирования
* **device** - файл устройства, генерируется на этапе загрузки
* **mount** - точка монтирования
* **path** - файл или папка
* **scope** - процесс
* **slice** - группа системных служб systemd
* **snapshot** - сохраненное состояние запущенных служб
* **socket** - сокет для взаимодействия между процессами.

Юнит - текстовый файл вида:

```text
[Название секции]

имя_переменной = значение
```

\*\*\*\*

Для создания юнита надо описать три секции: \[Unit\], \[Service\], \[Install\]

В секции Unit описываем:

```text
[Unit]
Description=java servlet container # Описание юнита 
# Далее следует блок переменных, которые влияют на порядок загрузки сервисов:
After=mysql.service 
Requires=mysql.service # Для запуска сервиса необходим запущенный mysql
Wants=nginx.service    # Для запуска сервиса желателен запущенный nginx:

[Service] #Как нужно запускать сервис
Type=simple #Тип сервиса systemd предполагает, что служба будет запущена незамедлительно. Процесс при этом не должен разветвляться.
#Type=forking systemd предполагает, что служба запускается однократно и процесс разветвляется с завершением родительского процесса
PIDFile=/var/run/name.pid # следует определить PIDFile=, чтобы systemd могла отслеживать основной процесс
WorkingDirectory=/opt/local/name # Рабочий каталог, он становится текущим перед запуском стартап команд
#Пользователь и группа:
User=ninja
Group=ninja
Environment=SERVER=production # Переменные окружения
OOMScoreAdjust=-100  #Запрет на убийство сервиса вследствие нехватки памяти и срабатывания механизма OOM:-1000 полный запрет , -100 понизим вероятность.
# Команды на старт/стоп и перезапуск сервиса
ExecStart=/sbin/ant start-portal
ExecStop=/sbin/ant stop-portal-force
ExecReload=/sbin/ant stop-portal-force start-portal
TimeoutSec=300 #Таймаут в секундах, сколько ждать system отработки старт/стоп команд.
Restart=always #Попросим systemd автоматически рестартовать наш сервис, если он вдруг перестанет работать.Контроль ведется по наличию процесса из PID файла
[Install] # в каком уровне запуска должен стартовать сервис
WantedBy=multi-user.target #соответствует нашему привычному runlevel=3 
```

Если сервис есть в Requires, но нет в After, то наш сервис будет запущен параллельно с требуемым сервисом. Уровни запуска - [это вот что](http://linux-notes.org/runlevel-v-unix-linux/). 

**Запуск юнита с помощью**  `systemctl` .

Кладем этот файл в каталог /etc/systemd/system/:

```text
systemctl status name

myunit.service - name
   Loaded: loaded (/etc/systemd/system/name.service; disabled)
   Active: inactive (dead)
```

```text
systemctl enable name
systemctl -l status name
```

Если все впорядке— то вывод будет вот такой:

```text
myunit.service - name
   Loaded: loaded (/etc/systemd/system/name.service; enabled)
   Active: inactive (dead)
```

Запускаем сервис:  


```text
systemctl start name
```

Смотрим  статус:

```text
systemctl -l status name
```

Перегружаем демон systemd:

```text
systemctl daemon-reload
```

 





