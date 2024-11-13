## **Формализапция задания**

### Перечень создаваемых ВМ по заданию:
#### Web-servers:
1. web01
2. web02
Параметры:
3. Target Group
Параметры:
4. Backend Group
Параметры:
5. HTTP Router
Параметры:
6. Application Load Balancer
Параметры:


#### Мониторинг:
1. Prometheus
Параметры:

2. Graphana
Параметры:

#### Сбор логов:
1. Elasticsearch
Параметры:
2. Kibana
Параметры:

#### Сеть:
1. VPC
Параметры:
2. Security Groups
Параметры:

#### Резервное копирование
1. Snapshots
Параметры:

#### Опционально:

1. Кластер из 2-х нод PostgreSQL для Prometheus с автоматическим failover (Yandex Managed Service for PostgreSQL. https://github.com/CrunchyData/postgresql-prometheus-adapter для настройки отправки данных из Prometheus в новую БД)
2. InstanceGroup  конкретных ВМ, которые входят в target group (правила автоматического горизонтального масштабирования: минимальное количество ВМ на зону — 1, максимальный размер группы — 3)
3. Добавить в Grafana оповещения с помощью Grafana alerts. Как вариант, можно также установить Alertmanager в ВМ к Prometheus, настроить оповещения через него.
4. В Elasticsearch добавить мониторинг логов самого себя, Kibana, Prometheus, Grafana через filebeat. Можно использовать logstash
5. Воспользуйтесь Yandex Certificate Manager, выпустите сертификат для сайта, если есть доменное имя. Перенастройте работу балансера на HTTPS, при этом нацелен он будет на HTTP веб-серверов.
