# Фиды жилых объектов (вторичный рынок)


## Описание элементов


|Элемент                                   |Обязательно для заполнения|Тип данных  |Описание и значения                                                                                                                                                                                                                                                                                                                                                                                                        |
|------------------------------------------|--------------------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|sku                                       |да                        |String      |Внешний идентификатор объекта                                                                                                                                                                                                                                                                                                                                                                                              |
|category                                  |да                        |SingleSelect|Категория объекта<br/>- **aftermarket**                                                                                                                                                                                                                                                                                                                                                                                  |
|sub-category                              |да                        |SingleSelect|Под-категория или тип объекта<br/>- **apartment**: квартира<br/>- **house**: дом                                                                                                                                                                                                                                                                                                                                    |
|title                                     |да                        |String      |Заголовок, будет отображаться на карточке объекта                                                                                                                                                                                                                                                                                                                                                                          |
|description                               |нет                       |String      |Описание объекта. Поддерживается разметка MARKDOWN.                                                                                                                                                                                                                                                                                                                                                                        |
|images.url                                |нет                       |String[]    |Массив ссылок на фотографии объекта                                                                                                                                                                                                                                                                                                                                                                                        |
|apartment-complex                         |нет                       |String      |Внешний идентификатор жилого комплекса                                                                                                                                                                                                                                                                                                                                                                                     |
|location.latitude                         |да                        |Decimal     |Широта                                                                                                                                                                                                                                                                                                                                                                                                                     |
|location.longitude                        |да                        |Decimal     |Долгота                                                                                                                                                                                                                                                                                                                                                                                                                    |
|location.address                          |да                        |String      |Адрес объекта                                                                                                                                                                                                                                                                                                                                                                                                              |
|location.precise-location                 |нет                       |Boolean     |\- **true**: местоположение объекта на карте будет точным<br/>- **false**: местоположение объекта на карте будет приблизительным.<br/>Значение по умолчанию: `true`                                                                                                                                                                                                                                                            |
|deal.price                                |да                        |Integer     |Цена объекта в UZS                                                                                                                                                                                                                                                                                                                                                                                                         |
|deal.aftermarket-deal-status              |нет                       |SingleSelect|Тип сделки<br/>- **primary** (Первичная продажа)<br/>- **direct** (Прямая продажа)<br/>- **counter-sale** (Встречная продажа)                                                                                                                                                                                                                                                                                          |
|deal.mortgage                             |нет                       |Boolean     |Доступна ипотека                                                                                                                                                                                                                                                                                                                                                                                                           |
|deal.discount                             |нет                       |Boolean     |Наличие скидки                                                                                                                                                                                                                                                                                                                                                                                                             |
|deal.haggle                               |нет                       |Boolean     |Возможен торг                                                                                                                                                                                                                                                                                                                                                                                                              |
|object.rooms                              |да                        |SingleSelect|Кол-во комнат<br/>- **1** (1)<br/>- **2** (2)<br/>- **3** (3)<br/>- **4** (4)<br/>- **5-and-more** (больше четырех)                                                                                                                                                                                                                                                                                        |
|object.total-space                        |да                        |Decimal     |Общая площадь                                                                                                                                                                                                                                                                                                                                                                                                              |
|object.kitchen-space                      |нет                       |Decimal     |Площадь кухни                                                                                                                                                                                                                                                                                                                                                                                                              |
|object.aftermarket-renovation             |да                        |SingleSelect|Ремонт<br/>- **euro** (евроремонт)<br/>- **redecorating** (косметический)<br/>- **designer** (дизайнерский)<br/>- **without** (требует ремонта)                                                                                                                                                                                                                                                                                                         |
|object.bathroom                           |да                        |SingleSelect|Санузел<br/>- **combined** (Совмещенный)<br/>- **separated** (Раздельный)<br/>- **2** (2)<br/>- **3** (3)<br/>- **4-and-more** (больше трех)                                                                                                                                                                                                                                                               |
|object.balcony                            |нет                       |MultiSelect |Балкон<br/>- **balcony** (Балкон)<br/>- **loggia** (Лоджия)<br/>- **terrace** (Терраса)                                                                                                                                                                                                                                                                                                                          |
|object.apartment.apartment-floor          |да                        |Integer     |Этаж<br/>Только если `sub-category = apartment`                                                                                                                                                                                                                                                                                                                                                                            |
|object.apartment.apartment-window-view    |нет                       |MultiSelect |Вид из окон<br/>- **courtyard** (Во двор)<br/>- **street** (На улицу)<br/>Только если `sub-category = apartment`                                                                                                                                                                                                                                                                                                  |
|object.house.house-floors-count           |да                        |Integer     |Количество этажей<br/>Только если `sub-category = house`                                                                                                                                                                                                                                                                                                                                                                   |
|object.house.house-lot-space              |да                        |Decimal     |Площадь участка<br/>Только если `sub-category = house`                                                                                                                                                                                                                                                                                                                                                                     |
|building.housing-class                    |да                        |SingleSelect|Класс жилья<br/>- **economy** (Эконом)<br/>- **comfort** (Комфорт)<br/>- **comfort-plus** (Комфорт+)<br/>- **business** (Бизнес)<br/>- **elite** (Элитный)                                                                                                                                                                                                                                                 |
|building.ceiling-height                   |да                        |Decimal     |Высота потолков                                                                                                                                                                                                                                                                                                                                                                                                            |
|building.built-date                       |да                        |Integer     |Год постройки                                                                                                                                                                                                                                                                                                                                                                                                              |
|building.apartment.apartment-building-type|нет                       |SingleSelect|Тип дома<br/>- **brick** (Кирпич)<br/>- **monolith** (Монолит)<br/>- **pane** (Панель)<br/>- **brick-monolith** (Кирпич-Монолит)<br/>- **concrete** (Бетон)<br/>Только если `sub-category = apartment`                                                                                                                                                                                                        |
|building.apartment.apartment-floors-total |да                        |Integer     |Количество этажей<br/>Только если `sub-category = apartment`                                                                                                                                                                                                                                                                                                                                                                  |
|building.house.house-type                 |да                        |SingleSelect|Дом<br/>- **full** (Отдельный дом)<br/>- **partial** (Часть дома)<br/>- **townhouse** (Таунхаус)<br/>- **duplex** (Дуплекс)<br/>Только если `sub-category = house`                                                                                                                                                                                                                                               |
|building.house.house-building-type        |нет                       |SingleSelect|Тип дома<br/>- **brick** (Кирпич)<br/>- **monolith** (Монолит)<br/>- **pane** (Панель)<br/>- **brick-monolith** (Кирпич-Монолит)<br/>- **concrete** (Бетон)<br/>- **reinforced-concrete** (Железобетон)<br/>- **stone** (Камень)<br/>Только если `sub-category = house`                                                                                                                                 |
|facilities.nearby                         |нет                       |MultiSelect |Рядом<br/>- **park** (Парк)<br/>- **water** (Водоем)<br/>- **metro-station** (Станция метро)<br/>- **shopping-mall** (Торговый центр)<br/>- **fitness** (Фитнес)<br/>- **playground** (Детская площадка)<br/>- **restaurants** (Кафе и рестораны)<br/>- **shops** (Магазины)<br/>- **kindergarten** (Детский сад)<br/>- **school** (Школа)<br/>- **public-transport** (Общественный транспорт)|
|facilities.apartment.apartment-parking    |нет                       |SingleSelect|Парковка<br/>- **closed** (Закрытая)<br/>- **open** (Открытая)<br/>- **underground** (Подземная)<br/>Только если `sub-category = apartment`                                                                                                                                                                                                                                                                        |
|facilities.apartment.apartment-facilities |нет                       |MultiSelect |Удобства<br/>- **internet** (Интернет)<br/>- **elevator** (Лифт)<br/>- **service-elevator** (Грузовой лифт)<br/>- **garbage-chute** (Мусоропровод )<br/>- **concierge** (Консьерж)<br/>- **closed-area** (Закрытая территория)<br/>Только если `sub-category = apartment`                                                                                                                                  |
|facilities.house.house-parking            |нет                       |MultiSelect |Парковка<br/>- **garage** (Гараж)<br/>- **parking-slot** (Место перед домом)<br/>Только если `sub-category = house`                                                                                                                                                                                                                                                                                                                                             |
|facilities.house.house-supply             |нет                       |MultiSelect |Инфраструктура<br/>- **electricity** (Электричество)<br/>- **gas** (Газ)<br/>- **sewerage** (Канализация)<br/>- **heating** (Отопление)<br/>- **water** (Водопровод)<br/>Только если `sub-category = house`                                                                                                                                                                                                                                            |
|facilities.house.house-facilities         |нет                       |MultiSelect |Удобства<br/>- **billiards** (Бильярд)<br/>- **sauna** (Сауна)<br/>- **pool** (Бассейн)<br/>- **kitchen** (Кухня)<br/>Только если `sub-category = house`                                                                                                                                                                                                                                                                                                  |
|promotions.promotion-installment          |нет                       |Boolean     |Рассрочка                                                                                                                                                                                                                                                                                                                                                                                                                  |
|promotions.promotion-trade-in             |нет                       |Boolean     |Трейд-ин                                                                                                                                                                                                                                                                                                                                                                                                                   |
|promotions.promotion-cash-back            |нет                       |Boolean     |Кэшбэк                                                                                                                                                                                                                                                                                                                                                                                                                     |
|promotions.promotion-special-prices       |нет                       |Boolean     |Специальные цены                                                                                                                                                                                                                                                                                                                                                                                                           |
|contact.contact-sku                       |нет                       |String      |Внешний идентификатор закрепленного за объектом контакта для связи                                                                                                                                                                                                                                                                                                                                                         |
|contact.contact-name                      |нет                       |String      |Имя закрепленного за объектом контакта для связи                                                                                                                                                                                                                                                                                                                                                                           |
|contact.contact-phone                     |нет                       |String      |Номер телефона закрепленного за объектом контакта для связи                                                                                                                                                                                                                                                                                                                                                                |
|contact.contact-telegram                  |нет                       |String      |Аккаунт Телеграм закрепленного за объектом контакта для связи                                                                                                                                                                                                                                                                                                                                                              |


## Пример

```xml:
<?xml version="1.0"?>
<feed xmlns="http://penthauz.app/feed" version="1.0">
    <row>
        <sku>house1_sku</sku>
        <category>aftermarket</category>
        <sub-category>house</sub-category>
        <title>Beautiful House with Garden</title>
        <description>A spacious house with a lovely garden</description>
        <images>
            <url>image1.jpg</url>
            <url>image2.jpg</url>
        </images>
        <location>
            <latitude>40.7128</latitude>
            <longitude>-74.0060</longitude>
            <address>123 Main St, Anytown, USA</address>
            <precise-location>true</precise-location>
        </location>
        <deal>
            <price>500000</price>
            <aftermarket-deal-status>primary</aftermarket-deal-status>
        </deal>
        <object>
            <rooms>5-and-more</rooms>
            <total-space>300.50</total-space>
            <aftermarket-renovation>euro</aftermarket-renovation>
            <bathroom>3</bathroom>
            <house>
                <house-floors-count>2</house-floors-count>
                <house-lot-space>600.75</house-lot-space>
            </house>
        </object>
        <building>
            <housing-class>comfort</housing-class>
            <ceiling-height>10.5</ceiling-height>
            <built-date>2005</built-date>
            <house>
                <house-type>full</house-type>
                <house-building-type>brick</house-building-type>
            </house>
        </building>
        <facilities>
            <house>
                <house-parking>garage</house-parking>
                <house-supply>electricity</house-supply>
                <house-facilities>sauna</house-facilities>
            </house>
        </facilities>
        <promotions>
            <promotion-installment>true</promotion-installment>
            <promotion-special-prices>true</promotion-special-prices>
        </promotions>
        <contact>
            <contact-sku>house1_contact_sku</contact-sku>
            <contact-name>John Doe</contact-name>
            <contact-phone>123-456-7890</contact-phone>
            <contact-telegram>@john_doe</contact-telegram>
        </contact>
    </row>
    <row>
        <sku>apartment1_sku</sku>
        <category>aftermarket</category>
        <sub-category>apartment</sub-category>
        <title>Modern Apartment in City Center</title>
        <description>A sleek and modern apartment in the heart of the city</description>
        <images>
            <url>image5.jpg</url>
            <url>image6.jpg</url>
        </images>
        <location>
            <latitude>34.0522</latitude>
            <longitude>-118.2437</longitude>
            <address>789 Elm St, Downtown, USA</address>
            <precise-location>true</precise-location>
        </location>
        <deal>
            <price>200000</price>
            <aftermarket-deal-status>primary</aftermarket-deal-status>
        </deal>
        <object>
            <rooms>2</rooms>
            <total-space>100.75</total-space>
            <aftermarket-renovation>euro</aftermarket-renovation>
            <bathroom>combined</bathroom>
            <apartment>
                <apartment-floor>5</apartment-floor>
                <apartment-window-view>street</apartment-window-view>
            </apartment>
        </object>
        <building>
            <housing-class>comfort</housing-class>
            <ceiling-height>9.0</ceiling-height>
            <built-date>2010</built-date>
            <apartment>
                <apartment-building-type>monolith</apartment-building-type>
                <apartment-floors-total>10</apartment-floors-total>
            </apartment>
        </building>
        <facilities>
            <apartment>
                <apartment-parking>open</apartment-parking>
                <apartment-facilities>internet elevator</apartment-facilities>
            </apartment>
        </facilities>
        <promotions>
            <promotion-trade-in>true</promotion-trade-in>
            <promotion-cash-back>true</promotion-cash-back>
        </promotions>
        <contact>
            <contact-sku>apartment1_contact_sku</contact-sku>
            <contact-name>Michael Johnson</contact-name>
            <contact-phone>555-123-4567</contact-phone>
            <contact-telegram>@michael_j</contact-telegram>
        </contact>
    </row>
</feed>
```

## Файлы для скачивания

[Схема данных](schemes/feed-aftermarket-scheme.xml)

[Пример](examples/feed-aftermarket-example.xml)