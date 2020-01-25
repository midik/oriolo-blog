---
path: "/izmenenie-razmerov-input-cherez-css"
title: "Изменение размеров input через CSS"
date: "2012-01-18"
excerpt: ""
category: "front-end"
tags: ""
series: ""
---

В этом посте рассмотрена стилизация тега input, а именно, изменение размера. Иногда бывает необходимо изменить размер поля input через CSS. Это можно сделать при помощи следующего кода:

```
input[type=text]{
   width:200px;
}
```

Вместо type=text надо вписать необходимый атрибут type. Он может принимать здесь следующие значения (информация с сайта [htmlbook.ru](http://htmlbook.ru/html/input/type)):

Тип

Описание

button

Кнопка.

file

Поле для ввода имени файла, который пересылается на сервер.

password

Обычное текстовое поле, но отличается от него тем, что все символы показываются звездочками. Предназначено для того, чтобы никто не подглядел вводимый пароль.

reset

Кнопка для возвращения данных формы в первоначальное значение.

submit

Кнопка для отправки данных формы на сервер.

text

Текстовое поле. Предназначено для ввода символов с помощью клавиатуры.