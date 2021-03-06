---
lang: ru
layout: article_with_sidebar
updated_at: '2017-11-21 14:07 +0400'
identifier: ref_RTng7mcS
title: 'Обновление свойств продуктов (цен, количества в наличии и т.д.) путем импорта'
order: 30
published: true
---
Импорт - это мощный инструмент, который позволяет не только создавать новые продукты, но и обновлять существующие. Импортом можно воспользоваться при обновлении свойств продуктов в магазине, включая их цены и количество в наличии.

В X-Cart есть две модели импорта:

*   Создание новых и обновление существующих продуктов;
*   Обновление существующих продуктов без создания новый продуктов.

![1.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/1.jpg)

Вариант **Создание новых и обновление существующих продуктов** позволяет одновременно создавать новые продукты и обновлять существующие. Если в CSV файле есть продукты, которые еще не созданы в магазине, они появятся в магазине после импорта этим способом.

Новые продукты создаются на основании следующих идентификаторов::

*   атрибуты: _product, name, class, group_
*   категории: _path_
*   продукты: _sku_
*   покупатели: _login_
*   атрибуты продуктов: _productSKU, type, name, class, group, owner, value_
*   отзывы: _product, additionDate, reviewerName, email_

Вариант **Обновление существующих продуктов без создания новых продуктов** позволяет обновлять существующие продукты без создания новых. 

Обратите внимание, что при обоих способах импорта в магазине создаются недостающие единицы, связанные с существующими. Например, если продукт обновляется путем импорта и он не входит ни в какую категорию, будет создана категория.

Рассмотрим процесс обновления цен и запасов продуктов на основе следующих случаев:

*   [Обновление цен и количества простых продуктов](#обновление-цен-и-количества-простых-продуктов);
*   [Обновление цен продуктов с опциями, настроенными с помощью модификаторов цены](#обновление-цен-продуктов-с-опциями-настроенными-с-помощью-модификаторов-цены);
*   [Обновление цен и количества вариантов продуктов](#обновление-цен-и-количества-вариантов-продуктов);
*   [Обновление цен продуктов с оптовым ценами](#обновление-цен-продуктов-с-оптовым-ценами).

## Обновление цен и количества простых продуктов

Например, цену продукта  _12033 Форменные Поло Звездный Путь_ нужно снизить с RUB 500 до RUB 400, а для продукта _12032 Форменная Футболка Звездный Путь: Следующее поколение_ нужно увеличить размер запаса с 11 до 15. Для начала рассмотрим случай, когда это простые продукты без опций и вариантов.

Как это сделать:

1.  Экспортируйте продукты на странице **Каталог / Экспорт**:
    ![2.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/2.jpg)
2.  Скачайте созданный файл экспорта и импортируйте его в редактор электронных таблиц, где содержимое файла будет распределено по столбцам. Для примера, воспользуемся таблицами Google.
3.  В созданном файле много столбцов, и те из них, которые не требуют обновления, лучше удалить. Будьте внимательны, чтобы не удалить столбцы, данные в которых следует обновить. Чтобы узнать, какие столбцы должны присутствовать в файле, обратитесь к статье {% link "Импорт CSV: Продукты" ref_inLgAwMe %}. В таблице, показывающей формат данных для импорта продуктов, можно увидеть только два обязательных поля (они отмечены звездочкой): **sku** и **name**. Эти два столбца нужно обязательно оставить в файле. Цена, требующая обновления, находится в столбце **price**, а количество продукта - в столбце **stockLevel**. Эти столбцы тоже следует оставить в файле. В общем, можно удалить все столбцы, кроме **price**, **name**, **sku** и **stockLevel**. После удаления лишних столбцов файл будет выглядеть так:
    ![3.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/3.jpg)
    (На скриншоте видно, что название столбца с именами продуктов - name_ru. Это потому, что вся информация в файле на русском языке.  Если информация о продуктах на другом языке, в названиях столбцов будут другие языковый коды).
4.  В строках артикулов, для которых нужно изменить цены и количество запасов, впишите актуальные значения в столбцах **price** и **stockLevel**. 
    ![4.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/4.jpg)
5.  Сохраните файл и импортируйте его в магазин в разделе **Импортировать в CSV** на странице **Каталог / Импорт**. 

Когда импорт завершится, проверьте продукты в магазине, их данные должны быть уже обновлены.

## Обновление цен продуктов с опциями, настроенными с помощью модификаторов цены

Рассмотрим случай, когда для продукта настроены {% link "многозначные атрибуты" ref_SuWz9rmN#многозначные-атрибуты-опции-продукта %}, и цена некоторых опций продукта устанавливается из цены основного продукта с применением {% link "модификатора цены" ref_SuWz9rmN#модификаторы-цены-и-веса %}.  Возьмем продукт _12032 Форменная Футболка Звездный Путь: Следующее поколение_, это футболка. Доступно несколько размеров футболки: S, M, L и XL. Основная цена продукта RUB 500, эта же цена распространяется на размерные опции S, M и L, а для размера XL цена повышена на RUB 50,00:

![5.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/5.jpg)

Например, необходимо изменить цену товара так, чтобы задать разные цены для разных размеров:

S - RUB 400,

M - RUB 450,

L - RUB 500,

XL - RUB 500. 

Это можно легко сделать с помощью экспорта и импорта. Чтобы задать такие цены, достаточно поменять модификаторы цены:

1.  В разделе **Экспорт в CSV** на странице **Каталог / Экспорт** выберите **Значения атрибутов продуктов**:
    ![6.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/6.jpg)
2.  Скачайте файл экспорта и загрузите его в редактор таблиц. 
3.  Удалите столбцы, данные в которых не требуют изменения. Будьте внимательны и не удалите нужные столбцы. Как сказано в статье {% link "Импорт CSV: Значения атрибутов продуктов" ref_gc6c4yTb %}, обязательные столбцы для импорта значений атрибутов продуктов - это **productSKU**, **type**, **name** и **value**. Не удаляйте эти столбцы. Также, для обновления модификаторов цен вам понадобится столбец **priceModifier**. Теперь, если посмотреть на строки, относящиеся к артикулу _12032 _, можно увидеть следующее:
    ![7.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/7.jpg)
4.  Внесите значения в столбец **priceModifier**:
    *   Добавьте модификатор цены _-100_ для размерной опции S (RUB 500 - 100 = RUB 400)
    *   Добавьте модификатор цены _-50_ для размерной опции M (RUB 500 - 50 = RUB 450)
    *   Значение модификатора цены для размерной опции L должно быть нулевым (= RUB 500)
    *   Удалите модификатор цены _+10_ для размерной опции XL, чтобы значение модификатора цены для XL тоже было нулевым (= RUB 500).![8.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/8.jpg)
5.  Сохраните файл и импортируйте его в магазин в разделе **Экспорт в CSV** на странице **Каталог / Импорт**. 

Когда импорт завершится, вы увидите обновленные цены продуктов в магазине.

## Обновление цен и количества вариантов продуктов

Рассмотрим, как изменить цены и размер запаса вариантов продуктов. Возьмем продукт _12033 Форменные Поло Звездный Путь_, это футболка, и у этого продукта есть варианты.

![9.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/9.jpg)

Например, нужно повысить цену вариантов _12034_ и _12037_, чтобы цена этих вариантов была RUB 400 - как у вариантов _12038_ и _12039_. Также, нужно изменить размер запаса варианта _12040_ с 8 на 6. 

Как это сделать:

1.  Экспортируйте продукты в разделе **Экспорт в CSV** на странице **Каталог / Экспорт**:
    ![10.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/10.jpg)
2.  Скачайте файл экспорта и загрузите его в редактор таблиц.
3.  Удалите столбцы, данные в которых не требуют изменения. Будьте внимательны и не удалите нужные столбцы. Как сказано в статье {% link "Импорт CSV: Продукты" ref_inLgAwMe %}, обязательные столбцы для импорта продуктов - это **sku** и **name**. Не удаляйте эти столбцы. Т.к. мы обновляем не простые продукты, а варианты, также, понадобится столбец **variantSKU**, его значения помогают идентифицировать варианты. Также, понадобятся столбцы **variantPrice** и **variantQuantity**. Теперь строки, представляющие варианты продукта выглядят так:
    ![11.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/11.jpg)
4.  Впишите в файл новые значение:

    *   Для вариантов _12034_ и _12037_ напишите RUB 400 в столбце **variantPrice**.
    *   Для варианта _12040_ измените количество в наличии на 6. После изменений файл будет выглядеть так:
    ![12.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/12.jpg)
5.  Сохраните файл и импортируйте его в магазин через раздел **Импортировать в CSV** на странице **Каталог / Импорт**. 

Когда импорт завершится, у продуктов в магазине будут новые цены и количество.

## Обновление цен продуктов с оптовым ценами

Предположим, что в магазине установлен модуль **Оптовые цены**. Оптовые цены должна быть доступны покупателям определенной группы и при заказе определенного количества продукта. Это можно настроить в разделе оптовых цен на странице продукта. Но если необходимо задать несколько диапазонов цен, удобнее использовать импорт/экспорт. Рассмотрим, как это сделать. Например, для продукта _12030 Женская Футболка Сэлфи Человека Паука_ с ценой RUB 500 нужно настроить оптовые цены:

*   1-4 единицы (для всех групп покупателей) - RUB 500
*   5 и более единиц (для всех групп покупателей) - RUB 400
*   10 и более единиц (для группы Оптовый закупщик) - RUB 350
*   10 и более единиц (для группы VIP покупатель) - RUB 300

Так выглядят настройки в разделе Оптовые цены:

![13.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/13.jpg)

То же самое можно сделать, не редактируя отповые цены продукта:

1.  Экспортируйте продукты в разделе **Экспорт в CSV** на странице **Каталог / Экспорт**:
    ![14.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/14.jpg)
2.  Скачайте файл экспорта и загрузите его в редактор таблиц. 
3.  Удалите столбцы, данные в которых не требуют изменения. Как сказано в статье {% link "Импорт CSV: Продукты" ref_inLgAwMe %}, обязательные столбцы для импорта продуктов с оптовыми ценами - это **sku** и **name** (для продукта), а также, **wholesalePrices** и **variantWholesalePrices** (столбцы, добавленные модулем **Оптовые цены**). Не удаляйте эти столбцы. Также, не стоит удалять столбцы **price** и **stockLevel**, что видеть базовые цены продуктов и размер запасов. Все остальные столбцы можно удалить. Теперь строка продукта _12030_ выглядит так:
    ![15.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/15.jpg)
4.  Задайте диапазоны оптовых цен. В нашем примере _12030 Женская Футболка Сэлфи Человека Паука_ - это простой продукт без вариантов. Значит, оптовые цены должны быть внесены в столбец **wholesalePrices**. Диапазон оптовых цен вносится в файл в таком формате:
    **N1**(**Membership1**)=**Price1**&&**N2**(**Membership2**)=**Price2**,
    где: 
    *   **N** - это минимальное количество продукта для заказа, с которого начинает действовать оптовая цена, 
    *   **Membership ** - это название группы покупателей, для которой действует оптовая цена (если ничего не указано, цена будет доступна покупателям, не входящим ни в какую группу),
    *   **Price** - это цена, соответствующая указанному количеству продуктов и группе,
    *   **&&** - это разделитель, отделяющий один диапазон цен от другого.

        В соответствии с форматом, цена для продукта _12030 Женская Футболка Сэлфи Человека Паука_ задается так: “5=400&&10(Оптовый покупатель)=350&&10(VIP)=300”
    ![16.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/16.jpg)

5.  Сохраните файл и импортируйте его в магазин через раздел **Импортировать в CSV** на странице **Каталог / Импорт**.

По завершении импорта в разделе Оптовые цены появятся новые оптовые цены.

Для продуктов с вариантами оптовые цены задаются так же, но в другом столбце - **variantWholesalePrices**. Ниже показано, как задать отповые цены для вариантов продукта _100ewl_ (артикулы _101ewl_, _102ewl_ и _103ewl_):

![17.jpg]({{site.baseurl}}/attachments/ref_RTng7mcS/17.jpg)

_Дополнительная информация:_

*   {% link "Импорт данных" ref_AwaMbiEf %}
*   {% link "Формат CSV файла для разных видов данных" ref_IbLL2XAb %}

