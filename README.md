Тестовое задание для веб-разработчика

Используя php 5.3, напишите программу, которая:

импортирует данные о комплектующих с xml-файла в бд mysql
отображает эти данные
Пример xml файла:

<?xml version="1.0" encoding="UTF-8"?>
<items>
  <item>
    <category>Motherboard</category>
    <name><![CDATA[ MB Biostar G31M /s775/Intel G31+ ICH7/2xDDR2 800/FSB 1333(1600o.c.)/1 x PCI-E x16/VGA/LAN/mATX ]]></name>
    <price>41</price>
  </item>
  <item>
    <category>Motherboard</category>
    <name><![CDATA[ Biostar G31M,LGA775,intel G31,1333Mhz,2DDR2 PC6400,1PCI-E16X,1PCI,int VGA,Sound6CH,LAN,2SATA & 1ATA,mATX,8USB ]]></name>
    <price>40.5</price>
  </item>
  <item>
    <category>HDD</category>
    <name><![CDATA[ Seagate 200GB 7200rpm 8MB SATAII/SATA EM200AA001 ]]></name>
    <price>34</price>
  </item>
  <item>
    <category>HDD</category>
    <name><![CDATA[ HDD 200 Gb Seagate 7200 rpm (SATA, EM200AA001) ]]></name>
    <price>34.5</price>
  </item>
</items>
Структура БД mysql:

create table `categories`
(
 `id` int UNSIGNED NOT NULL AUTO_INCREMENT ,
 `name` varchar (255) NOT NULL ,
 PRIMARY KEY (`id`)
);
create table `items`
(
 `id` int UNSIGNED NOT NULL AUTO_INCREMENT ,
 `category_id` int UNSIGNED NOT NULL ,
 `name` varchar (255) ,
 `price` decimal(30,2) ,
 PRIMARY KEY (`id`)
);
Импорт данных

На этой странице должна быть отображена форма загрузки xml-файла. После успешной загрузки xml-файла данных о комплектующих происходит импорт этих данных в базу данных mysql следующим образом:

Для каждого элемента item в xml-файле должна быть добавлена запись в таблицу items.
При этом в поле category_id должна быть записана ID категории.
ID категории брать с таблицы categories, если в таблице нет такой категории, то ее нужно добавить.
После успешного импорта данных вывести сообщение о количестве симпортированных данных.
Обработка ошибок:

При импорте должна быть проверка на валидность xml файла - если загружаемый xml-файл не валидный, то вывести об этом сообщение и ничего не импортировать.
Отображение данных

Разметка страницы следующая:

[MENU]
Categories
Motherboard
HDD
...
Import Data
[CONTENT AREA]
Блок [MENU] содержит 2 блока:

Categories - в этом блоке отображаются список всех категорий. Каждый элемент является ссылкой, при нажатии на которую в блоке [CONTENT AREA] показывается список комлектующих в этой категории. Список комплектующих выводить таблицей в 2 колонки: item name, price.
Import Data - ссылка на страницу импорта данных
Где брать реквизиты доступа к БД MySQL?

В корневой директории приложения должен быть конфигурационный файл с именем config.ini, где будут указаны хост, имя базы данных, пользователь и пароль. Пример:

dbhost=localhost
dbname=test
dbuser=test
dbpassword=test