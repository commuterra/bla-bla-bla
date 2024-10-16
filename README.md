# Построение годового гидрографа реки по данным ежедневных расходов воды

*Как мы докатились до такой темы?* Когда-то давно в рамках практической по гидрологии нам задали построить годовой гидрограф по данным с гидрометеорологического поста о среднесуточных расходах воды. У меня эта работа оставила неизгладимое впечатление, поскольку я потратила уйму времени и сил, чтобы обработать эти данные в Ecxel. Поэтому сейчас, немного освоив питон, я предложила Глебу эту тему в качестве проекта. К сожалению, Глеб согласился. И вот мы *здесь* 〜(＞＜)〜

Для начала поясню, как в прошлом году мы строили гидрограф *ручками* [ ± _ ± ]:

1.	С сайта [автоматизированной информационной системы государственного мониторинга водного мониторинга](https://gmvo.skniivh.ru/index.php?id=505) мы скачивали данные для обработки. Для этого мы указывали интересующие нас года, бассейновый округ, бассейн, подбассейн и водохозяйственный участок. Если на выбранной реке находилось несколько гидрометеорологических постов, выбирали один из них.

![изображение](https://github.com/user-attachments/assets/75df81a5-b4c0-4295-8837-26a939d5fb6e)

2.	Затем для выбранного поста мы скачивали таблицу формата xls, где данные были оформлены в следующем виде. Чтобы построить гидрограф (= линейный график), необходимо было удалить все вспомогательные символы (например, ^, _, ю), а также перенести все данные в одну колонку.

![изображение](https://github.com/user-attachments/assets/18aedf14-83c8-415d-a147-35d0f06f0e91)

3.	Кроме того, мы расчленяли гидрограф (×_×) по типам питания (подземное, снеговое, дождевое), а также считали долю каждого из них. В итоге в Ecxel гидрограф выглядел следующим образом.

![изображение](https://github.com/user-attachments/assets/b67d3206-ce30-4708-bd1b-94fc573a5235)

Но вернемся к нашему проекту. 
Во время написания код тестировался на данных по реке Амур (в исходном файле содержалась информация сразу о 12 годах). Затем программа несколько раз проверялась на других реках России, выбранных случайным образом. 

**В ходе работы были реализованы следующие задачи:**

1.	Подбор данных для апробирования кода.
2.	Первичная обработка скачанных данных (перевод из формата xls в txt).
3.	Создание двумерного массива с датами в виде списка [ММ, ДД] и создание списка с данными о среднесуточных расходах воды в году.
4.	Нахождение даты начала и окончания половодья на основе среднего значения расхода в году.
5.	Визуализация полученных данных с помощью библиотеки Matplotlib.
6.	Анализ полученных результатов.

## Результаты работы:

Мы смогли перевести данные в читаемый вид и построить гидрограф ☆*:.｡.o(≧▽≦)o.｡.:*☆, а также освоили много новых библиотек и инструменты работы в них, поэтому мы большие молодцы! ＼(￣▽￣)／ Кроме того, мы можем выделить дату начала и окончания половодья.

![изображение](https://github.com/user-attachments/assets/f2e30a80-d164-4ffd-8231-d6539774acca)

Актуальна ли наша работа? Нет (￣︿￣)
Оказалось, что сайт АИС ГМО может сразу генерировать гидрографы (◕‿◕)

![изображение](https://github.com/user-attachments/assets/c630d49d-bee0-464d-a957-c9682e69d55c)

![zastavki-gas-kvas-com-ye6r-p-zastavki-robert-veid-7](https://github.com/user-attachments/assets/3dfbb821-ed1e-41c4-a3f3-a6f2d3dba9de)

Однако построенный на сайте гидрограф не расчленен по типам питания. Нами была предпринята попытка расчленить наш гидрограф на два типа питания: снеговое (во время паводка) и дождевое (весь остальной период) на основе известных дат начала и окончания половодья, однако мы не достигли успехов на этом поприще ┐(￣ヘ￣;)┌. Вероятно, это слишком сложная задача, поскольку только в России существует несколько типов рек по гидрологическому режиму, для которых затруднительно написать единый код даже для выделения даты начала и окончания паводка. Например, у рек причерноморского и крымского типа половодье может в принципе отсутствовать, компенсируясь многочисленным паводками.
Но мы попытаемся когда-нибудь написать код для расчленения, наверное... (￢_￢). А пока что студентам Вышки придется расчленять гидрограф ручками в Excel Σ(￣。￣ﾉ).
 
Авторы проекта:

Поляков Глеб – главный программист (*^‿^*)
Лалетина София – идейный вдохновитель ＼(٥⁀▽⁀ )／
