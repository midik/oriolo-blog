---
path: "/kak-dobavit-k-blogu-na-wordpress-podderzhku-openid"
title: "Как добавить к блогу на WordPress поддержку OpenID"
date: "2012-02-09"
excerpt: ""
category: "wordpress"
tags: ""
series: ""
---

В этой статье я расскажу про **использование OpenID в WordPress**, а именно, как сделать OpenID-провайдером блог на WordPress, используя плагины, и разрешить комментирование постов в блоге по этому протоколу.

**OpenID** - это универсальная система авторизации. Он представляет собой URL, который можно использовать для входа на различные сайты, поддерживающие эту систему.

Это очень удобно, ведь не надо регистрироваться на каждом новом сайте только для того, чтобы оставить комментарий, и запоминать большое количество логинов и паролей. Сайтов, использующих эту технологию, очень много.

[![](images/OpenID_logo.png "OpenID")](http://oriolo.ru/wp-content/uploads/2012/02/OpenID_logo.png)

В результате, мы:

1. **получим собственный OpenID** вида http://oriolo.ru, который вы сможете использовать для авторизации на других сайтах. Например, этот протокол поддерживается популярной системой комментирования Disqus, которая установлена у многих блогеров.
2. на многопользовательских блогах - идентификатор вида http://oriolo.ru/author/user-name **для каждого автора**.
3. **возможность комментирования** ваших статей посетителями, у которых есть свой OpenID. При этом каждый комментарий, сделанный по этому протоколу, будет отмечен логотипом возле имени автора. Как это выглядит, можно посмотреть в первых двух комментариях [тут](http://oriolo.ru/wordpress/nado-li-ubirat-datu-v-blogah/ "Надо ли убирать дату в блогах").
4. привяжем Gravatar к вашему индетификатору.

Для начала, нам потребуется **установить плагин XRDS-Simple**. Это можно сделать через установщик плагинов, воспользовавшись поиском, либо [скачать](http://wordpress.org/extend/plugins/xrds-simple/ "XRDS-Simple") его со страницы плагинов WordPress, и распаковать в папку wp-content/plugins/.

После этого, надо **установить плагин OpenID** (скачать [можно тут](http://wordpress.org/extend/plugins/openid "OpenID") или найти через поиск плагинов), и настроить его следующим образом.

Основные **настройки плагина** появятся в меню "Плагины - OpenID".

В разделе Enable OpenID необходимо выбрать роли пользователей, которые смогут его использовать. Если вы - единственный автор блога, и регистрация на нем запрещена, то поставьте галочку напротив пункта Administrator.

В разделе Blog Owner выберите имя пользователя, который сможет использовать адрес блога как свой ID. На многопользовательском блоге остальные пользователи будут иметь адрес вида http://oriolo.ru/author/user-name.

Последний раздел Troubleshooting, посвящен решению проблем в работе плагина. Там можно посмотреть текущее состояние системы, и очистить кеш.

Теперь, после применения основных настроек, можно перейти в меню "Параметры - Обсуждение", и настроить возможность вашим посетителям **комментировать с использованием OpenID**. Внизу страницы, сразу над настройками аватаров, появился новый пункт. Там можно включить комментирование, разрешить не указывать имя и email для комментариев, сделанных по этому протоколу, и включить их автоматическое одобрение. У меня все галочки отмечены.

И последним шагом будет регистрация на сайте [paulisageek.com](http://paulisageek.com/openidavatar/site/login/ "openidavatar") для **привязки аватара с Gravatar к вашему OpenID**. Там надо нажать на логотип протокола, ввести адрес вашего блога, пройти процесс авторизации и указать email, который зарегистрирован в Gravatar.

Также следует отметить, что кроме применения плагина существует другой способ использовать свой домен в качестве OpenID, который был описан в [блоге Свободного вебмастера](http://www.webliberty.ru/kak-ispolzovat-svoy-domen-v-kachestve-openid/ "OpenID сервер"). Этот способ заключается в **подключении к своему блогу стороннего сервера**, такого как Яндекс, LiveJournal, или MyOpenID, через мета-теги. Но при этом у ваших посетителей не будет возможности добавлять свои комментарии с использованием своего идентификатора, на вашем блоге, и, кроме того, мне кажется, что это менее надежно, чем использовать плагин.