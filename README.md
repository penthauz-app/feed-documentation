# Технические требования Penthauz для XML-выгрузки

## Общие требования к XML-файлам

* URL фида должен быть постоянным и доступным по протоколу HTTP
* Фид должен быть в кодировке UTF-8 
* XML-файл должен иметь стандартизированную структуру

## Структура фида

* Фид должен начинаться с тега `feed` и содержать версию фида
* Данные отдельных объектов находятся в теге `row`


```
<feed xmlns="http://penthauz.app/feed" version="1.0">
	<row>... object 1 ... </row>
	<row>... object 2 ... </row>
	...
</feed>
```


## Виды фидов

На данный момент поддерживается три типа фидов:

* Фиды жилых комплексов
* Фиды жилых объекток
* Фиды жилых объектов в новостройках


## Фиды жилых комплексов

### Описание элементов


| Элемент                   | Обязательно для заполнения | Значение | Описание                                                                                                                      |
| ------------------------- | -------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------- |
| sku                       | да                         | String   | Внешний идентификатор объявления                                                                                              |
| title                     | да                         | String   | Заголовок, будет отображаться на карточке объекта                                                                             |
| description               | нет                        | String   | Описание объекта. Поддерживается разметка MARKDOWN.                                                                           |
| logo.url                  | нет                        | String   | Ссылка на логотип объекта                                                                                                     |
| images.url                | нет                        | String[] | Массив ссылок на фотографии объекта                                                                                           |
| location.latitude         | да                         | Decimal  | Широта                                                                                                                        |
| location.longitude        | да                         | Decimal  | Долгота                                                                                                                       |
| location.address          | да                         | String   | Адрес объекта                                                                                                                 |
| location.precise-location | нет                        | Boolean  | - true: местоположение объекта на карте будет точным<br/>- false: местоположение объекта на карте будет приблизительным |

### Пример

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