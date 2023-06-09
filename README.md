Здравствуйте, сегодня мы поговорим о начальной модификации 3д принтеров ЕНДЕР 3 С1 ПЛЮС и ПРО версий. 
Данная инструкция хоть и сделана на версии ПЛЮС но полностью совместима с версией ПРО. 

Сейчас я расскажу о нескольких самых необходимых и базовых модификация, с которыми качество и скорость печати многократно возрастут, при этом вложений потребуют только некоторые из модификаций. 

Начнем с ухода от базового Программного обеспечения к ПО от МАРЛИН (https://github.com/ThomasToka/MarlinFirmware)  в котором уже присутствует очень нужный нам АЛГОРИТМ LA Linear advance. О котором я расскажу немного позже. 

Тут я не буду рассматривать саму сборку принтера из коробки, так как Подробнейшая инструкция в ВИДЕО формате уже идет в комплекте с принтером, а именно записана на 8 гиговую флешку идущую в комплекте, для ознакомления с ней, ее просто необходимо вставить в компьютер, через адаптер, который тоже есть в комплекте. 

Для того чтобы установить ПО совместимое с вашим принтером, вам необходимо включить питание принтера дождаться полной загрузки штатного ПО, после, в правом нижнем углу нажать на шестеренку, после в правом верхнем углу нажать на «О», как ни странно это информация о принтере.

![EcO0IwrKNpo](https://user-images.githubusercontent.com/128589691/232246713-871c6113-1098-43ed-8bfc-5349d3c09097.jpg)

На фото вы видите информацию о принтере до прошивки, с низу сайт www.creality.com/ и так далее.
Внимание, для того чтобы прошивка установилась необходимо обновить прошивку экрана до версии 1.0.2 или выше, это третья строчка на фото. Для этого вам необходимо посетить официальный сайт 
 
 (https://www.creality.com/pages/download-ender-3-s1-plus?spm=..page_1934481.products_display_1.1&spm_prev=..page_1936959.header_1.1) 
 
и скачать последнюю прошивку для своей модели принтера.
Для определения модели нам необходимо найти 2 строчку в которой написано F/W BEP и цифро-буквенный код, далее нам нужно запомнить 2 последних символа, у меня это F4 что означает что у меня последняя версия чипа на плате. Всего их 2 типа F1 и F4, и для каждой своя прошивка. Все отличие заключается в том, что для прошивки платы с индексом F4, на заранее отформатированной флешке в формате 4096, необходимо создать папку с названием STM32F4_UPDATE,  в корне и уже в нее поместить файл (***.bin) с прошивкой. На F1 достаточно на отформатированную в тот же формат флешку закинуть файл (***.bin). Чтобы завершить установку нового ПО на 3д принтер, достаточно вставить влешку с прошивкой в 3д принтер и включить его. При включении, принтер немножко притормозит и если всё было сделано правильно, прошивка установиться и принтер заработает. Чтобы понять что прошивка установилась откройте настройки, сведение о принтере, там должен измениться сайт и номер прошивки во второй строчке. 

Хотелось бы заметить что предлагаемое мной ПО имеет поправки по размеру стола, а именно 310х315х300, поэтому рекомендуется установить такие же значения в ВАШ слайсер (ЭТО ВАЖНО!!!).

Теперь рассмотрим алгоритм LA (Linear advance). Это очень полезный алгоритм который позволяет увеличить скорость печати без потери качества печатаемого изделия. К примеру со стандартных 20-30 мм/с можно без потери качества достичь скоростей 60-80 мм/с. 
Для начала этот самый коэффициент нужно найти (у меня на PLUS версии для пластика PLA он составил 0.075). Для этого, очень хороший и уважаемый мною человек Дмитрий Сорокин (https://www.youtube.com/@SorkinDmitry) сделал сайт с генератором теста для определения этого самого коэффициента, не буду рассказывать как он работает, так как работает он отлично, лишь оставлю ссылку на сайт 

(https://k3d.tech/calibrations/la/k3d_la.html) 
и видео инструкцию от Дмитрия (https://youtu.be/XBlaabitjvg).

После успешного заимствования моего коэффициента или калибровки и нахождения своего собственного коэффициента, кстати он меняется в зависимости от вязкости пластика, можно продолжать рассматривать следующие модификации. 

У принтеров данной модели существует автокалибровка стола, чтобы она заработала, в окне (стартовый gcod) необходимо ввести команду М420(подгружает из памяти карту неровностей), после команды G28(парковка всех осей), тогда и только тогда принтер начнет использовать карту неровностей стола.

Рассмотрим модификацию охлаждения:
Так как штатный обдув хоть и не очень жуткий, он имеет очень большой недостаток, а именно то что он односторонний, тоесть модель будет охлаждаться только с одной стороны, из за этого требовательные к обдуву пластики будут печататься с одной стороны хорошо, а с другой будут большие температурные наплывы от недостатка охлаждения. Для решения данной проблемы люди изобрели свои радикально другие решения по охлаждению сопла экструдера 

(https://cults3d.com/ru/3d-model/instrument/air-duct-ender-3-s1-pro).

![8WkHYkPSdio](https://user-images.githubusercontent.com/128589691/232246745-53c30544-2d0a-4af6-b088-c6b142f3c439.jpg)

На просторе  интернета если и много других решений связанных с обдувом, но лично мой выбор пал на этот и его аналог от этого же создателя.
Тут выбрана система охлаждения от вентилятора 5015 с возможностью обдува сопла со всех сторон. Выбор фирмы изготовителя вентиляторов оставлю за вами, но рекомендую брать японский SUNON 5015 на 24v, он дорогой, но имеет отличное качество и тихий при работе, у остальных разница будет в стоимости, долговечности и шуме при работе самого охлаждения.

Замена термобарьера :
Я рекомендую сразу заказывать биметалический термобарьер 
(https://aliexpress.ru/item/1005004147655342.html?spm=a2g2w.orderdetail.0.0.55df4aa6e2MzdI&sku_id=12000032831701425) 
от компании Trianglelab. Подробную разборку данной модификации я рассмотрю на видео, где установлю данный термобарьер на штатную голову и расскажу об этом уже наглядно  и подробно, но так как сама замена не является чем то сложным, вы без проблем можете попробовать сделать все  сами.

![a6mAdxsPtjA](https://user-images.githubusercontent.com/128589691/232246784-24173612-f7f0-41f5-b94e-6ed57d64fa0c.jpg)

Данную инструкцию не спонсировали ни одни из вышеперечисленных магазинов и людей, все сделано на чистом энтузиазме и личном опыте, для того чтобы помочь в решении проблемы тем многим, которые все таки решились на покупку данных принтеров. 
Поддержать автора можно лайком и репостом =))
Ну и через сайт (https://www.donationalerts.com/r/zaterok_zette) 
