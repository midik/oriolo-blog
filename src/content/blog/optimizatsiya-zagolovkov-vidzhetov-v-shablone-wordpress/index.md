---
path: "/optimizatsiya-zagolovkov-vidzhetov-v-shablone-wordpress"
title: "Оптимизация заголовков виджетов в шаблоне WordPress"
date: "2012-01-31"
excerpt: ""
category: "wordpress"
tags: ""
series: ""
---

Вчера скачала [учебник по SEO-оптимизации](http://www.seobuilding.ru/seo-forum/poiskovaya_optimizaciya_v_obshih_chertah/seo_poiskovaya_optimizaciya_ot_a_do_ya/) и долго его изучала.

А потом посмотрела на шаблон своего блога - и ужас-ужас! - названия виджетов выделены заголовками h3, а в тексте предыдущих постов я использовала h4. Самое обидное, что бот гугла это уже заметил, и теперь, по его мнению, ключевые слова моего блога это "комментарии" с 94 вхождениями и "записи" с 62 :(. Непорядок, надо исправлять. Поэтому этом посте я расскажу, как **оптимизировать заголовки виджетов**.

Заголовками должен выделяться наиболее значимый текст, к которому не относится название виджетов. К тому же, оно повторяется на всех страницах блога, тем самым влияя на результаты индексирования страниц. Из-за этого я решила **заменить h3 на p в названиях виджетов**.

При помощи дополнения Firebug для Firefox я определила, какой стиль отвечает за вывод заголовков виджетов. У меня это `widget-title`.

Далее, идем в файл style.css. Ищем в нем что-то похожее на `h3.widget-title`, и заменяем на `div.widget-title`. Так мы создадим стиль оформления для новых заголовков виджетов, который будет в точности повторять предыдущий.

Теперь осталось заменить тег `h3` на `p` в файле functions.php вашего шаблона. Находим там вот такой код:

```

register_sidebar(array(
	'name'=>'Left Sidebar',
	'before_widget' => '',
	'after_widget' => '',
	'before_title' => '',
	'after_title' => '',
));

```

и вместо `h3` пишем `div`, и добавляем `<p>`.

В итоге, у меня получилось следующее:

```

register_sidebar(array(
	'name'=>'Left Sidebar',
	'before_widget' => '',
	'after_widget' => '',
	'before_title' => '',
	'after_title' => '',
));

```

Проделываем те же самые операции с другими сайдбарами, если они есть.

Теперь ненужные заголовки не будут отвлекать поискового робота от содержимого вашего сайта.

\[info\] **Обновление от 07.03.2014:** Если на вашем сайте используется HTML5, то заголовки удалять не нужно, если сайдбар находится внутри тега `section`. Это необходимо для семантики веб-страницы. Подробнее об этом можно почитать здесь (по-английски):

- [The Truth About Multiple H1 Tags in the HTML5 Era](http://webdesign.tutsplus.com/articles/the-truth-about-multiple-h1-tags-in-the-html5-era--webdesign-16824)
- [The section element](http://html5doctor.com/the-section-element/)

Чтобы проверить, правильно ли вы используете теги `section` и `h1-h6`, можно использовать [этот онлайн-инструмент](http://gsnedders.html5.org/outliner/). \[/info\]