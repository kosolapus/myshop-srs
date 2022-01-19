# Спецификация Требований к Программному продукту (SRS) "Автоматизированная информационная система оптовой продажи книг" (АИС ОПК)
_Автор: Имя Автора_

_Заказчик: Имя Заказчика_

_Исполнитель: Имя Исполнителя_

## Введение

Спецификация требований к программному обеспечению предназначена для
документирования и описания соглашения между заказчиком и разработчиком
относительно деталей разрабатываемого программного продукта.
Его основная цель — предоставить четкое и описательное «изложение требований
пользователя», которое можно использовать в качестве справочного материала
при дальнейшей разработке программной системы. Этот документ разбит на несколько
разделов, используемых для логического разделения требований к программному
обеспечению на части, на которые легко ссылаться.

Настоящая Спецификация требований к программному обеспечению предназначена для
описания функциональных возможностей, внешних интерфейсов, атрибутов и проектных
ограничений, налагаемых на реализацию программной системы, описанной в
остальной части документа. В описании программной системы язык и терминология
должны быть однозначными и согласованными во всем документе.

## Цель создания SRS

Определение и описание функций и спецификаций АИС ОПК является основной целью данной Спецификации требований к,
программному обеспечению (SRS). Эта Спецификация требований к программному
обеспечению ясно иллюстрирует основные виды использования системы и требуемые
функции, указанные Заказчиком.

## Описание возможностей АИС ОПК

Создаваемая программная система называется "Автоматизированная информационная
система оптовой продажи книг" или АИС ОПК. Она создается для клиента,
заинтересованного в продаже книг через Интернет. Эта система предназначена для
"обеспечения поддержки автоматизации" процесса размещения книг для продажи в
Интернете и облегчения фактической продажи. Эта система в значительной степени
кроссплатформенна и доступна любому, кто пользуется компьютерными ресурсами сети
Интернет. Система будет работать на центральном сервере, и каждый пользователь
будет иметь удаленный пользовательский интерфейс через веб-браузер для
взаимодействия с ней.

АИС ОПК в значительной мере будет являться проксирующим сервером между клиентом
и ERP 1C Заказчика. Здесь и далее в документе рассматриваемые возможности системы
подразумевают наличие реализации подобных возможностей в рамках ERP 1C. Система
представляет собой 3 основных модуля, предназначенные для полноценного и целостного
взаимодействия между Посетителем сайта и организацией Клиента.

С одной стороны, система будет поддерживаться в актуальном состоянии при помощи
модуля "Обмен" (module.exchange). Этот модуль позволит загружать/выгружать товарные
позиции, новости, данные об акциях, обеспечивать контроль и учет заказов, а так же
управлять состоянием Пользователей системы путем добавления, получения, изменения
или удаления (CRUD-операции).

С другой стороны, все взаимодействие пользователя с системой будет осуществляться
при помощи интерфейсного модуля "Фронтэнд" (module.frontend), обеспечивающего
базовые возможности по взаимодействию с системой, например: регистрацию, просмотр
и поиск товаров, просмотр новостей, изменение данных пользователя
__<TBD: Уточнить прочие возможности>__.

Поддерживать данный функционал позволит модуль "Прокси" (module.proxy), который
будет отвечать за бесперебойную работу и взаимодействие остальных элементов системы.

## Обозначения, сокращения и терминология

| Обозначение | Расшифровка                                                                                                            |
|-------------|------------------------------------------------------------------------------------------------------------------------|
| АИС ОПК     | Автоматизированная Информационная Система Оптовой Продажи Книг                                                         |
| CRUD        | Набор базовых операций с базой данных, включающих в себя создание, чтение, изменение и удаление значений в базе данных |
| SRS         | Software Requirements Specification, Спецификация Требований к Программному продукту                                   |


## Содержание документа
## Общее описание
## Обзор АИС ОПК
АИС ОПК будет включать в себя набор функций, перечисленных ниже:
- module.exchange:
    - <TBD: Уточнить требования к обмену>
- module.proxy:
  - Отправка сообщений Пользователям
    - Рассылки
    - Изменение статуса заказа
    - Восстановление пароля
  - <TBD: Уточнить требования к бэкенду>
- module.front:
    - Предоставлять возможность работы с Личным Кабинетом:
        - Запрос на регистрацию
            - Шаблон для регистрации на основе карточки контрагента 1С
            - С обязательным предоставлением номера телефона для передачи пароля
            - Логином зарегистрированных пользователей может быть электронная почта
            - Менеджер проверяет и активирует клиента в 1с
            - Клиент получает пароль автоматически, менеджер не видит пароля.
        - Логин
        - Логаут
        - Редактирование данных пользователя
            - <TBD: список параметров>
        - Запрос на восстановление пароля
            - Клиент может восстанавливать пароль в случае его утраты по логину на тот телефон, который указан как контакт.
              <TBD: уточнить, что это значит>
        - Обратная связь
    - Предоставлять возможность работы с Корзиной:
        - Добавление товара
        - Удаление товара
        - Изменение количества товара
        - Добавление товаров из файла
    - Предоставлять возможность работы с Каталогом товаров:
        - Отображать на устройстве пользователя актуальный каталог книг со следующими
          атрибутами:
            - Основной родитель номенклатуры
            - Подраздел
            - ISBN
            - EAN
            - стандарт
            - автор (?)
            - Производитель
            - переплет (?)
            - год издания (?)
            - <TBD: список атрибутов>
            - цена
                - Цены на витрине клиент видит с учетом своей скидки.
                - Цена берется максимальная из всех карточек аналогов.
            - Предоставлять возможность поиска товаров по следующим параметрам
              <TBD: уточнить необходимость полнотекстового поиска>:
                - автору
                - наименованию
                - ISBN
                - EAN
                - <TBD: список параметров>
        - Предоставлять возможность сортировки товаров по следующим параметрам:
            - родителю
            - Подразделу
            - Производителю
            - <TBD: список параметров>
        - Предоставлять возможность фильтрации товаров по следующим параметрам:
            - <TBD: список параметров>
    - Предоставлять возможность работы с Заказами:
        - Просмотр списка Заказов
        - Создание заказа
            - Заказ формируется для заполненной корзины
            - Заполненную корзину можно сохранить без оформления заказа
            - Возможно выбрать место доставки клиента или оставить его пустым для самовывоза
        - Отслеживание заказа (<TBD: Уточнить, что это значит>)
            - Просмотр зарезервированных товаров в заказе
            - При формировании отгрузочных документов и проведении транспортного требования,
              клиент получает обратную связь в личном кабинете (<TBD: Уточнить, что это значит>)
                - спецификацию подвоза (расходная накладная УПР)
                - данные о времени водителя из транспортного требования
                - сведения по готовности сборки на складе.
        - Получать доступ к взаиморасчетам (<TBD: Уточнить, что это значит>)
            - Формировать сверку взаиморасчетов (формируется запрос в 1С)
            - Запрашивать печать финансовых документов
            - Формировать прайс из выбранных параметров номенклатуры
                - со своими ценами
                - или с расчетными по формуле ценами
            - Из спецификации на отгрузку делать прайс с изменяемой ценой
            - По спецификации запрашивать сертификаты на товары.
            - получать сканы, возможно только на отгруженное.
    - Предоставлять интерфейс менеджера (?)
      - Менеджер может заблокировать пользователя
## Функциональные модули АИС ОПК
## Описание пользователя АИС ОПК
## Допущения
1. Предполагается, что разработка данной системы будет идти в итеративном порядке.
   В случае необходимости возможен пересмотр данных требований в процессе работы по
   соглашению сторон
2. Рекомендованный порядок разработки модулей:
    1. module.exchange
    2. module.proxy
    3. module.front

## Предположения и зависимости

## Обобщенные требования

## Специфические требования

## Модели требований

### Диаграмма использования
#### Аутентификация пользователя
#### Просмотр каталога
#### Создание заказа
#### Редактирование данных пользователя

### Диаграмма классов
#### Пользователь
#### Корзина
#### Позиция заказа
#### Товар
#### Новость

### Диаграмма поведения
### Диаграмма состояния (?)
## Прототипы
## Примеры использования

1. Иван Алексеевич - представитель родительского комитета, ему нужно заказать 
комплект учебников на класс к учебному году, которые он самостоятельно заберет из ПВЗ
2. Инна Анатольевна - ИП из Екатеринбурга, ей нужно разослать прайсы своим покупателям
3. Олег Геннадьевич - менеджер по закупкам из Москвы, ему нужно пополнить складские запасы книг
## Ссылки
## Обратная связь
По вопросам - в PR / issues ☺