---
path: "/twenty-eleven-comments-form"
title: "Совершенствуем форму комментариев в теме Twenty Eleven"
date: "2012-02-26"
excerpt: ""
category: "wordpress"
tags: ""
series: ""
---

Привет всем читателям блога **"Записки о WordPress"**! Многие блогеры используют в качестве шаблона для своего блога стандартные Wordpress темы Twenty Eleven или Twenty Ten. Эти темы выбирают, потому что они стильные, красивые, минималистичные. Но вот форма комментирования выглядит громоздкой. В этой статье я расскажу, как **поменять вид формы комментирования** в теме Twenty Eleven.

Вот так форма комментирования в теме Twenty Eleven выглядит по-умолчанию. При нажатии на картинку можно посмотреть ее в 100% масштабе. Не кажется ли вам, что если сделать поля ввода "имя", "email" и "сайт" в одну строку, то форма станет намного компактнее?

[![Twenty Eleven форма комментариев](images/screenshot_004.jpeg)](http://oriolo.ru/wp-content/uploads/2012/01/screenshot_004.jpeg)

Конечно, про **изменение формы комментариев** писали уже много, но для современных тем, таких как Twenty Eleven и Twenty Ten, не подходят рекомендации для других, более старых тем.

### Шаг 1. Разбираем стандартный код формы

Вывод формы комментирования в теме Twenty Eleven осуществляется функцией `<?php comment_form(); ?>` из файла comments.php.

Стилизация осуществляется строками с 2039 по 2191 файла стилей.

Давайте с помощью FireBug посмотрим html-код формы комментариев:

[![код формы комментариев](images/screenshot_006.jpeg)](http://oriolo.ru/wp-content/uploads/2012/02/screenshot_006.jpeg)

Как можно заметить, поля ввода `input` заключены внутрь тегов `p`. Именно эти теги нам и надо стилизовать.

### Шаг 2. Редактируем CSS

Сначала найдем и удалим ненужный код:

```

#respond p {
	margin: 10px 0;
}
```

Теперь удалим отступы, добавив `margin: 0` для полей ввода. Установим ширину поля в 85% от ширины тега p, в котором оно находится. При необходимости, поменяйте высоту input'а.

```

#respond input[type=text] {
	display: block;
	height: 24px;
	margin: 0;
	width: 85%;
}
```

Изменим ширину полей input до 30%, добавим следующий код после 2187 строки:

```

p.comment-form-author,
p.comment-form-email,
p.comment-form-url {
	display: block;
	float: left;
	margin: 0 10px 0 5px;
	width: 30%;
}
```

Мы создали стили для полей ввода, задали для них обтекание по левому краю, установили ширину в 30%, и отступы между полями ввода.

Теперь форма комментирования выглядит почти как надо. Правда, лейбл "Комментарий" не на месте. Давайте это исправим.

### Шаг 3. Редактируем вывод формы комментариев

В файле comments.php найдите функцию `comment_form`, о которой я говорила в начале статьи. Замените ее на следующее:

```

'
```