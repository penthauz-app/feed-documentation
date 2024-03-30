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

## Типы данных

### String

Строка в кодировке UTF-8

```
<!-- Определение в схеме -->
<xs:element name="title" type="xs:string"/>

<!-- Значение в XML-файле -->
<title>Spacious Family Home</title>
```

### String[]

Массив строк в кодировке UTF-8

```
<!-- Определение в схеме -->
<xs:element name="images" minOccurs="0">
	<xs:complexType>
		<xs:sequence>
	    	<xs:element name="url" type="xs:string" minOccurs="0" maxOccurs="unbounded"/>
	    </xs:sequence>
	</xs:complexType>
</xs:element>

<!-- Значение в XML-файле -->
<images>
    <url>image1.jpg</url>
    <url>image2.jpg</url>
</images>
```

### Decimal

Десятичное число

```
<!-- Определение в схеме -->
<xs:element name="latitude" type="xs:decimal"/>

<!-- Значение в XML-файле -->
<latitude>51.5074</latitude>
```

### Integer

Целое число

```
<!-- Определение в схеме -->
<xs:element name="apartment-floor" type="xs:integer"/>

<!-- Значение в XML-файле -->
<apartment-floor>5</apartment-floor>
```

### Boolean

Булевый тип данных, может иметь значения `true` или `false`

```
<!-- Определение в схеме -->
<xs:element name="discount" type="xs:boolean"/>

<!-- Значение в XML-файле -->
<discount>true</discount>
```

### SingleSelect

Выбор одного из возможных значений. Описывается в схеме как `simpleType` c вложенным узлом `restriction`.

```
<!-- Определение в схеме -->
<xs:simpleType name="ObjectRenovation">
    <xs:restriction base="xs:string">
    	<xs:enumeration value="fine"/>
      	<xs:enumeration value="turnkey"/>
      	<xs:enumeration value="rough"/>
    </xs:restriction>
</xs:simpleType>

<xs:element name="new-renovation" type="ObjectRenovation"/>

<!-- Значение в XML-файле -->
<new-renovation>turnkey</new-renovation>
```

### MultiSelect

Выбор нескольких из возможных значений. Описывается в схеме как `simpleType` c вложенным узлом `list`. Выбранные значения разделяются пробелом.

```
<!-- Определение в схеме -->
<xs:simpleType name="ObjectBalcony">
    <xs:list>
    	<xs:simpleType>
    		<xs:restriction base="xs:string">
		      	<xs:enumeration value="balcony"/>
		      	<xs:enumeration value="loggia"/>
		      	<xs:enumeration value="terrace"/>
		    </xs:restriction>
    	</xs:simpleType>
    </xs:list>
</xs:simpleType>

<xs:element name="balcony" type="ObjectBalcony"/>

<!-- Значение в XML-файле -->
<balcony>balcony loggia terrace</balcony>
```

## Опциональные данные

Данные, опциональные для заполнения помечаются аттрибутом `minOccurs="0"`.

```
<xs:element name="kitchen-space" type="xs:decimal" minOccurs="0"/>
```

## Зависимость данных от выбранного типа объекта.

В определенных случаях наличие или отсутствие полей в фиде зависит от типа экспортируемого объекта. Например, площадь участка (`house-lot-space`) нужна только для объектов из под-категории "дома".

Такие ограничения помечены в схеме комментарием

```
<!-- only for sub-category == "apartment|house" -->
```

А соответствующие поля будут сгруппированы.

```
<xs:element name="apartment" minOccurs="0">
	<xs:complexType>
		<xs:all>
			<xs:element name="apartment-floor" type="xs:integer"/>
      		<xs:element name="apartment-window-view" type="ObjectApartmentWindowView" minOccurs="0"/>
      	</xs:all>
	</xs:complexType>
</xs:element>
```

Аттрибут `minOccurs` у элемента `apartment` сигнализирует о том, что данный узел может быть опущен, если объект отностися к другой под-категории.


## Виды фидов

На данный момент поддерживается три типа фидов:

* [Фиды жилых комплексов](apartment-complex-feed.md)
* [Фиды жилых объектов в новостройках](new-buildings-feed.md)
* [Фиды жилых объектов - вторичное жилье](aftermarket-feed.md)


