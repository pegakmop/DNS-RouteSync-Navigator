## DNS-RouteSync-Navigator


**Основные функции:** Этот скрипт представляет собой простой DNS сервер, способный автоматически добавлять статические маршруты на роутере для указанных в фильтре доменов.
- Создано в первую очереь для роутеров Keenetic младших моделей.

**Функции:**
- Сервер принимает DNS запросы от клиентов и отправляет их на обработку публичному DNS серверу для получения IP-адресов доменов.
- Скрипт проверяет полученные DNS записи на соответствие фильтру доменов, указанному в конфигурационном файле. Если DNS имя найдено в фильтре, скрипт принимает решение о добавлении статического маршрута на роутер.
- Для добавления маршрутов на роутер, скрипт использует Telnet-подключение, отправляя соответствующие команды на роутер.

**Зависимости:** Для работы Domain Mapper необходимо наличие следующих библиотек Python:
- telnetlib3
- configparser
- dnslib

*Не забудьте установить их перед запуском:*
```
pip3 install -r requirements.txt
```

**Использование:**

Внимательно заполните конфигурационный файл config.ini, указав все параметры.

Скопируйте в domain.txt доменные имена, которые необходимо перенаправлять через укзанное в настройках подклчюение роутреа.

Установите IP машины с DNS-RouteSync-Navigator в качестве основного DNS на роутере или ПК.

Запустите скрипт. Он будет слушать DNS запросы, и при совпадении доменов с фильтром, добавлять их IP в статические маршруты роутера на указанный в config.ini интерфейс.

#### Протестировано в Windows 11


# Скрипт написан в качестве "proof of concept"!
Автору известно большинство его проблем и недочетов, возможно, когда-нибудь они будут исправлены.

**От автора:** Скрипт является логическим продолжением DomainMapper и был задуман в качестве альтернативы OPKG пакетам на Open WRT и Keenetic OS роутерах.
Основной причиной стало обладание роутером Keenetic младшей модели - без USB, с 32 Мб ПЗУ и отсутствием возможности установки entware.
Главной целью была реализации функционала OPKG пакетов дающих возможность динамически маршрутизировать трафик по разным каналам основываясь на DNS именах посещаемых сайтов.
Даже при суловии облегчения процесса сопоставления тысячь IP-адресов необходимых сайтов и их добавления в статические маршруты, для чего и был написан DomainMapper, это занятие наскучило на третий день…

