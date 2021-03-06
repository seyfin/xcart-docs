---
lang: ru
layout: article_with_sidebar
updated_at: '2017-11-29 15:25 +0400'
identifier: ref_XEdis9sU
title: Типы атрибутов продуктов по области применения
order: 20
published: true
---
Атрибуты можно разделить на три группы на основе области их применения: атрибуты продукта, атрибуты класса продуктов и глобальные атрибуты. 

Атрибуты продукта - это свойства, настраиваемые на уровне одного отдельного продукта.

Глобальные атрибуты - это свойства, которыми могут обладать любые или все продукты в магазине. 

Чтобы настроить атрибуты продукта, нужно определить, какие качества этого продукта могут быть полезны покупателям, а также, есть ли такие же качества у других продуктов в магазине. Это поможет понять, какой тип атрибутов лучше настроить для продукта. 

Например, если вы продаете футболки, полезно будет настроить такие атрибуты, как _Размер_ (S, M, L, XL), _Цвет_ (красный, синий, желтый и т.п.), _Ткань_ (хлопок, лен и .п.) и т.д. Если футболки - это все, что вы продаете, то все эти свойства нужно настроить как глобальные атрибуты. Таким образом, вы сможете применять эти атрибуты ко всем артикулам в магазине. Если помимо футболок вы продаете другие продукты, например, сумки, атрибуты _Размер_, _Цвет_ и _Материал_ могут не подойти. Например, размер важен при выборе сумки, но для покупателя намного полезнее знать габариты в сантиметрах, чем просто размер S, M или L. Аналогично, сумка может быть сделана не только из материи, но и из кожи, пластика, замши, соломы, т.е. для сумок подходит атрибут _Материал_, а не _Ткань_. В этом случае, следует создать отдельный класс для каждого типа продуктов (_Одежда_ для футболок и _Сумки_ для сумок) и свои атрибуты для каждого класса (_Размер_, _Цвет_ и _Ткань_ для класса _Одежда_ и _Стиль_, _Материал_ и _Размеры_ для класса _Сумки_).

Если у какого-то продукта есть свойство, которым не обладает ни один другой продукт в магазине, следует создать атрибут именно для этого продукта. Например, если всего одна футболка в магазине с вышивкой, для нее можно задать доступные варианты рисунка, создав атрибут продукта _Вышивка_ (Бабочка, Цветок и т.п.)

_Дополнительная информация:_

*   {% link "Работа с классами продуктов" ref_oNqyWK0N %}
*   {% link "Работа с атрибутами продуктов" ref_d0BOqdWu %}
*   {% link "Работа с атрибутами классов продуктов" ref_79cWvxmm %}
*   {% link "Работа с глобальными атрибутами" ref_o3s6sQgq %}