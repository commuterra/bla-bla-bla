# **"Анализ статей в ScienceDirect по поисковому запросу" aka "Падение Юпитера" (×﹏×)**

В настоящее время второй курс активно страдает над написанием обзорной главы в курсовой работе. Её главная и неотъемлемая составляющая - анализ существующих статей на тему исследования. Однако в наш информационный век на заданную тему или по ключевым словам может существовать несколько тысяч статей, каждую из которых учесть просто невозможно ＼(〇_ｏ)／. 

Чтобы упростить поиск наиболее релевантных статей, изначально мы составляли графы в VOSviewer (пример см. ниже), отражающиеся связанность статей по ключевым словами или связанность наиболее цитируемых авторов. Для построения графа мы скачивали из ScienceDirect метаданные статей, соответствующих нашему запросу (например, при поиске по ключевым словам). Метаданные содержали информацию о названии, авторах, ключевых словах, аннотации, годах и месте публикации и др. 

Однако мы столкнулись с проблемой: скачивать данные можно было только по одной странице. При этом на одной странице выводилось не более 100 статей, поэтому довольно затратно по времени было скачивать информацию о паре тысяч статей 〜(＞＜)〜. 
В связи с чем мы решили написать код, который бы парсил все имеющиеся метаданные и выводил по ним некую статистику.

![Без имени-1](https://github.com/user-attachments/assets/d240d508-0088-4240-b04a-1ca43f996ba3)


**Какие основные задачи были реализованы в ходе проекта?**

1.	Написание кода для обращения к  ScienceDirect Search V2 API, который скачивал бы метаданные всех статей по запросу, с учетом особенностей синтаксиса запроса и ответа.
2.	Создание на основе скачанных данных трех словарей: где ключами являются имена авторов, а значениями - количество их публикаций, года и количество публикаций, авторы и года, в которые он публиковались.
3.	Нахождение общих статистических данных.
4.	Визуализация полученных данных с помощью различных графиков (bar, scatterplot).

### Как мы искали данные?
При работе с ScienceDirect мы столкнулись с большим количеством трудностей: к данным, которые нам необходимо было парсить, было очень сложно подступиться из-за качественной защиты сайта от автоматизированных запросов, поэтому наши запросы постоянно упирались в ошибку 400. Ключом к успеху стало использование одного из официальных API ScienceDirect - ScienceDirect Search V2 API. Однако его использование привело к появлению новых ограничений: по одному запросу можно выгрузить только первые 6100 статей. Обращение к разработчикам API - Elsevier Developer Portal - не помогло: они ответили, что у них лапки и данное API уже старое, а ограничение количества статей является особенностью его архитектуры. За неимением лучшего варианта мы остановили свой выбор на API, и парсили данные с его помощью. Как нам кажется, выборка из более чем 6 тысяч статей является достаточно подробной.

## Результаты работы:

Одним из результатов нашего проекта является то, что по запросу пользователя (ключевые слова через запятую), программа выводит список авторов с наибольшими количеством публикаций по заданным словам и количество их публикаций. 

Такжи визуализируется распределение количества публикаций по годам (похоже на [Google Books Ngram Viewer](https://books.google.com/ngrams/)). В ходе построения этих графиков мы выявили интересную особенность: дата публикации в метаданных может относится и к будущему, например, к 2025 году. Скорее всего, это характрено для популярных журналов, где публикации по выпускам расписаны на год вперед. Поэтому не пугайтесь, если наш график уведет вас в будущее (⁀ᗢ⁀).

![изображение](https://github.com/user-attachments/assets/d5ec6000-e07a-47c6-afc4-b95281b6b821)

Кроме того, на графике выводятся года с наибольшим количеством публикаций и их количество.

![изображение](https://github.com/user-attachments/assets/17bde0ae-11e8-488b-a6eb-3009ddf2b1d5)

Кульминацией нашего проекта является распределение по годам публикаций наиболее продуктивных авторов (т.е. с наибольшим количеством публикаций). Может быть так, что в один год автор публикуют сразу несколько статей (завидуем продуктивности этого человека (-_-)). Но мы предусмотрели и это: на скаттерплоте размер пунсона отражает количество публикаций.

![Без имени-1](https://github.com/user-attachments/assets/1656a0c8-04c9-47b9-91fd-2f4f6505c591)

Поэтому если вам нужна будет помощь в подборе литературы к литобзору в вашей курсовой, вы всегда можете обратиться к нашему коду ☆*:.｡.o(≧▽≦)o.｡.:*☆! Однако остерегайтесь китайцев, которые в последние годы заполонили все журналы! ..・ヾ(。＞＜)シ

Помимо этого, если вы введете запрос, который подразумевает ответ больше чем на 3000 статей Джупитер улетит в стратосферу и перестанет подавать признаки жизни пару минут (ﾒ﹏ﾒ) (авторы проекта столкнулись с этим пару раз). Будьте осторожны.
 
### Авторы проекта:

Диденко Игорь – главный программист, специалист по парсингу и DDoS атакам на ScienceDirect Σ(￣。￣ﾉ)

Лалетина София – идейный вдохновитель, рисовальщик графиков ＼(٥⁀▽⁀ )／
