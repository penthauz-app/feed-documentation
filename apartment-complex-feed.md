# Фиды жилых комплексов

## Описание элементов


| Элемент                   | Обязательно для заполнения | Тип данных | Описание и значения                                                                                                                      |
| ------------------------- | -------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------- |
| sku                       | да                         | String   | Внешний идентификатор объекта                                                                                              |
| title                     | да                         | String   | Заголовок, будет отображаться на карточке объекта                                                                             |
| description               | нет                        | String   | Описание объекта. Поддерживается разметка MARKDOWN.                                                                           |
| logo.url                  | нет                        | String   | Ссылка на логотип объекта                                                                                                     |
| images.url                | нет                        | String[] | Массив ссылок на фотографии объекта                                                                                           |
| location.latitude         | да                         | Decimal  | Широта                                                                                                                        |
| location.longitude        | да                         | Decimal  | Долгота                                                                                                                       |
| location.address          | да                         | String   | Адрес объекта                                                                                                                 |
| location.precise-location | нет                        | Boolean  | - true: местоположение объекта на карте будет точным<br/>- false: местоположение объекта на карте будет приблизительным. Значение по умолчанию: `true` |


## Пример

```
<?xml version="1.0"?>
<feed xmlns="http://penthauz.app/feed" version="1.0">
    <row>
        <sku>Complex001</sku>
        <title>Luxury Apartments Downtown</title>
        <description><![CDATA[A luxurious apartment complex offering modern amenities and stunning city views.]]></description>
        <logo>
            <url>https://example.com/complex001_logo.jpg</url>
        </logo>
        <images>
            <url>https://example.com/complex001_image1.jpg</url>
            <url>https://example.com/complex001_image2.jpg</url>
            <url>https://example.com/complex001_image3.jpg</url>
        </images>
        <location>
            <latitude>40.7128</latitude>
            <longitude>-74.0060</longitude>
            <address>123 Main St, CityA</address>
            <precise-location>true</precise-location>
        </location>
    </row>
</feed>

```

## Файлы для скачивания

[Схема данных](schemes/feed-apartment-complex-scheme.xml)
[Пример](examples/feed-apartment-complex-example.xml)