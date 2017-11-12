---
lang: ru
layout: article_with_sidebar
updated_at: '2017-11-08 16:26 +0400'
identifier: ref_65Cs4QwQ
title: Расчет стоимости доставки вручную
order: 20
published: true
---
Принимая решения о стоимости доставки товаров покупателям, важно учесть, сколько доставка обходится вашему бизнесу. Наиболее точную {% link "оценку стоимости доставки" ref_BqJi1vAR %} предоставляют онлайн службы транспортных компаний. Также, можно установить и настроить свои расценки на доставку. 

В X-Cart можно задать уникальные ставки расчета стоимости доставки:

*   по промежуточной сумме заказа (стоимость доставки будет зависеть от промежуточной суммы заказа);
*   по весу (стоимость доставки будет зависеть от веса продуктов в заказе);
*   по количеству продуктов в заказе (стоимость доставки будет зависеть от количества продуктов в заказе);
*   по любой комбинации промежуточной суммы заказа, веса и количества продуктов (стоимость доставки будет зависеть нескольких параметров).

Как создать способ доставки с настраиваемыми ставками:

1.  В панели управления магазина откройте раздел Способы доставки (страница **Настройка магазина / Доставка**):
    ![1.jpg]({{site.baseurl}}/attachments/ref_65Cs4QwQ/1.jpg)
2.  Нажмите **Добавить способ доставки**:
    ![2.jpg]({{site.baseurl}}/attachments/ref_65Cs4QwQ/2.jpg)
    Откроется диалоговое окно, в котором можно выбрать тип стоимости доставки:
    ![3.jpg]({{site.baseurl}}/attachments/ref_65Cs4QwQ/3.jpg)
3.  Перейдите на вкладку **Ручная настройка**:
    ![4.jpg]({{site.baseurl}}/attachments/ref_65Cs4QwQ/4.jpg)
4.  Укажите общую информацию о способе доставки:
    ![5.jpg]({{site.baseurl}}/attachments/ref_65Cs4QwQ/5.jpg)

    *   **Название**: название способа доставки, которое будут видеть покупатели.
    *   **Время доставки**: предположительное время доставки.
    *   **Зона доставки**: зона адресов, внутри которой будет действовать способ доставки. Если вы еще не создали эту адресную зону, пройдите по ссылке Управление зонами и нажмите Создать зону.
    *   **База для расчета**: в поле _Тариф на основе_ выберите один или несколько параметров, на базе которых будет рассчитываться стоимость доставки.
        *   _Подытог заказа_ - для расчета стоимости доставки по сумме заказа. Пример: фиксированная плата за доставку RUB 500 при промежуточной сумме заказа до RUB 3000 и бесплатная доставка при сумме выше RUB 3000.
        *   _Вес_ - для расчета стоимости доставки по весу продуктов в заказе. Пример:  фиксированная плата за доставку RUB 500 при весе заказа до 5 кг и RUB 200 за 1 кг при весе заказа выше 5 кг. Чтобы использовать этот тип расчета, необходимо указать точный вес в настройках всех продуктов, для которых действует этот способ доставки.
        *   _Продукты в  заказе_ - для расчета стоимости доставки по количеству продуктов в заказе. Пример: фиксированная стоимость доставки RUB 300, если в заказе 5 или менее продуктов, и RUB 50 за продукт, если в заказе 6 или более продуктов.
        *   _Подытог заказа, вес, продукты_ - для расчета стоимости доставки нескольким параметрам. Пример: фиксированная стоимость доставки RUB 500 при промежуточной сумме заказа до RUB 3000 и весе до 5 кг; бесплатная доставка при промежуточной сумме заказа RUB 300 и выше и весе до 5 кг, и фиксированная стоимость доставки RUB 600 при весе заказа выше 5 кг. Для использования этого способа расчета доставки необходимо указать вес в настройках  всех продуктов, для которых действует этот способ доставки.

5.  Как составить таблицу расценок на доставку для нового способа доставки:

    В диалоговом окне, где вы вносили общую информацию о новом способе доставки, можно настроить и расценки. Форма расчета в нижней части этого окна - это первая строка таблицы расценок. 
    ![6.jpg]({{site.baseurl}}/attachments/ref_65Cs4QwQ/6.jpg)
    Параметры в этой строке могут быть различными в зависимости от настроек поля Тариф на основе выше. Например, если вы выбрали Стоимость, вес и количество товаров, то полей в этой строке будет больше, и они будут расположены в два ряда, т.к. не умещаются в один:
    ![7.jpg]({{site.baseurl}}/attachments/ref_65Cs4QwQ/7.jpg)
    Не смотря на то, что поля расположены в два ряда, они составят только первую строку таблицы расценок на доставку и только первый тариф.
    Чтобы создать тариф на доставку, задайте значения в этих полях. Вы получите правило, по которому будет рассчитываться стоимость доставки для нового метода. 
    Можно задать несколько тарифов. Когда все данные внесены, нажмите **Сохранить**.

    Пример:
    *   фиксированная стоимость доставки RUB 500 при сумме заказа до RUB 3000 и весе  до 5 кг, 
    *   бесплатная доставка при сумме заказ RUB 3000 и выше и весе до 5 кг,
        и 
    *   фиксированная стоимость доставки RUB 600 при весе заказа более 5 кг.

    Для настройки первого тарифа _фиксированная стоимость доставки RUB 500 при сумме заказа до RUB 3000 и    весе до 5 кг_ поля таблицы должны быть заполнены следующим образом:
    ![8.jpg]({{site.baseurl}}/attachments/ref_65Cs4QwQ/8.jpg)
  
    *   стоимость товаров: RUB 0.00 - RUB 2999, 
    *   вес товаров: 0 - 5 кг,
    *   фиксированный тариф: RUB 500.
    
    Первый тариф настроен. 
    Добавьте еще две строки таблицы для тарифов _бесплатная доставка при сумме заказ RUB 3000 и выше и весе до 5 кг_ и _фиксированная стоимость доставки RUB 600 при весе заказа более 5 кг_.  Чтобы добавить новые строки, нажмите значок [+]:
    ![9.jpg]({{site.baseurl}}/attachments/ref_65Cs4QwQ/9.jpg)
    Две новые строки будут настроены следующим бразом:
    ![10.jpg]({{site.baseurl}}/attachments/ref_65Cs4QwQ/10.jpg)

 _Бесплатная доставка при сумме закаа RUB 3000 и выше и весе до 5 кг_:
    *   стоимость товаров: RUB 3000 - RUB  ∞
    *   вес товаров: 0 - 5 кг
    *   фиксированный тариф: RUB 0

 _Фиксированная стоимость доставки RUB 600 при весе заказа более 5 кг_:
    *   стоимость товаров: RUB 0 - RUB  ∞
    *   вес товаров: 5 кг - ∞ 
    *   фиксированный тариф: RUB 600

Теперь можно сохранить таблицу.

Новый способ доставки создан. Убедитесь, что новый способ доставки активирован. В настройках всех продуктов, для которых работает новый способ доставки, опция **Требуется доставка** должна быть включена.

Настройка завершена. Теперь для заказов, для которых выбран новый способ доставки, стоимость доставки будет рассчитана по созданной таблице.