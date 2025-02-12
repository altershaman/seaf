# Архитектурные объекты слоя "Техническая архитектура"
Слой технической архитектуры представлен базовой метамоделью **SEAF-CORE** и двумя расширениями:
* **SEAF-DZO** - расширение **SEAF-CORE** нацеленное на автоматизированную проверку стандартов
* **REVERSE** - независимое от **SEAF-CORE** расширение нацеленное на автоматизированный реверс архитектуры из окружения облачных провайдеров

## Состав технической архитектуры
Техническая архитектура строится на базе двух фундаментальных сущностей.

### Технические компоненты
Это простейшие сущности технической архитектуры из которых состоит технический сервис.
К техничесим компонентам относятся такие простейшие вещи как:
* Пользовательское устройство
* Офис или иное место присутствия
* Аппаратный сервер
* Виртуальный сервер
* Аппаратная СХД
* Сетевое устройство
* K8s Deployment
* POD K8s
* K8s Container
* Image ПО для развёртывания в K8s

### Технические сервисы
Это сущность, которая предоставляет слою прикладной архитектуры вычислительные сервисы. Только технический сервис может иметь связанность со слоем прикладной архитектуры.
К техничесим сервисам относятся:
* Регион развёртывания инфраструктуры
* Зона доступности
* Центр обработки данных
* Кластер приложений
* Кластер виртуализации
* Программная СХД
* Объектная СХД
* Kubernetes Cluster
* WAN сеть
* LAN сеть
* DMZ сеть
* Сетевая связь
* Сервис мониторинга
* Сервер резервного копирования

## Структура каталогов технической архитектуры
    -*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-
    |- _metamodel_                      - Подключенные пакеты метамоделей
    |  |- seaf-core                     - Пакет seaf-core метамодели
    |  |  |- entities                   - Сущности метамодели
    |  |  |  |- ta                      - Описание метамодели технической архитектуры
    |  |  |  |  |- services.yaml        - Описание сущности технических сервисов 
    |  |  |  |  |- components.yaml      - Описание сущности технических компонентов
    |  |  |  |  |- services_docs.yaml   - Описание реестров технических сервисов 
    |  |  |  |  |- components_docs.yaml - Описание реестров технических компонентов
    |- architecture                     - Архитектурные объекты поставляемые с пакетом
    |  |- ta                            - Техническая архитектура
    |  |  |- reverse                    - Архитектура описанная с помощью технологии реверса

## Использование слоя технической архитектуры
Рекоменудемый порядок описания архитектуры инфраструктуры:
1. Регионы, зоны доступности, ЦОДы, офисы
2. Сетевое оборудование, аппаратных серверы и СХД
3. Кластера виртуализации и виртуальные машины
4. Кластера приложений и кластера Kubernetes
5. Системы мониторинга и резервного копирования
6. Пользовательские устройства

## Использование расширений базовой метамодели **SEAF-CORE**
В подавляющем большистве случаев достаточно будет использовать базовый набор сущностей из поставки **SEAF-CORE**. 
Для некоторых компаний будет полезным использование расширенния **SEAF-DZO**. Все сущности этого расширения имеют суффикс **_dzo**.
**SEAF-DZO** содержит в себе все поля из базовой метамодели **SEAF-CORE**, но дополнительно включает параметры, которые можно проверять автоматически на соответствие стандартам группы Сбер.
Например, для описания сервиса мониторинга необходимо использовать **seaf.ta.services.monitoring_dzo**.