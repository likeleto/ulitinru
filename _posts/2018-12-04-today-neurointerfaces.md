---
title: Нейроинтерфейсы сегодня
tags: Article, BCI
---

![image](https://habrastorage.org/webt/v4/ay/vr/v4ayvrp9j_sduy_2oezomr_pzbi.jpeg)

Со времён изобретения манипулятора "мышь" прошло полвека, и это по-прежнему один из основных способов взаимодействия человека с компьютером. Я поехал на [конференцию](https://neuro.hse.ru/cccp2018/program) в Институт когнитивных нейронаук ВШЭ, чтобы узнать о последних достижениях в области BCI, которая находится за горизонтом, и поэтому так интересна.

<!--more-->

Отчет о конференции я переработал в статью для связанного повествования. Какие-то моменты упрощаю и опускаю, а какие-то дополняю из своих наблюдений и отчетов с других мероприятий. Прочитав ее, я надеюсь, у вас появятся общие понимания подходов к BCI и текущего состояния в этой области. За оригинальными трактовками лучше обращаться к оригинальным статьям, к счастью, почти все в открытом доступе.

## История
История BCI началась в 1973 году с публикации Toward direct brain-computer communication [1], где Jacques Vidal изложил  идеи в коммуникации между человеком и машиной и описал лабораторию по анализу EEG сигнала для таких целей. Спустя десятилетие Wolpaw сфокусировал применение BCI на помощи парализованным людям и описал принципиальную схему BCI [2]:

![image](https://habrastorage.org/webt/g0/t-/w0/g0t-w0hlvvbeilwbsfiqr8w0qps.png)

Основные реализации BCI давали возможность вводить текст людям c [синдромом изоляции](https://ru.wikipedia.org/wiki/%D0%A1%D0%B8%D0%BD%D0%B4%D1%80%D0%BE%D0%BC_%D0%B7%D0%B0%D0%BF%D0%B5%D1%80%D1%82%D0%BE%D0%B3%D0%BE_%D1%87%D0%B5%D0%BB%D0%BE%D0%B2%D0%B5%D0%BA%D0%B0). Это были  сложные в использовании системы, потому что пользователь должен проходить долгую тренировку [3], в противовес, появились "спеллеры" на основе распознавания [P300](https://en.wikipedia.org/wiki/P300_(neuroscience)) - компонента, который возникает в момент, когда человек совершает выбор, которые снизили требования к пользователю [4].
 
В 90-е тема все более становится известной, особенно с появлением техник машинного обучения [5]. С увеличением надежности BCI люди интересуются расширением применения в новые области.

[Thorsten Zander](https://www.researchgate.net/profile/Thorsten_Zander) предложил следующую классификацию BCI [6]:
- Активные BCI – пользователь инициирует команду безусловно
- Реактивные BCI – пользователь инициирует команду в ответ на воздействие системы
- Пассивные BCI – пользователь не дает команду, но система считывает и анализирует его состояние

Отдельно стоит рассмотреть вопрос стимуляции мозга, эта тема, хоть и не относится напрямую к BCI, но представляет собой связанную технологию, которая расширяет возможности BCI для контроля.
 
Также BCI можно классифицировать по способу получения сигнала:
- Инвазивные (вживленные электроды, [ECoG](https://en.wikipedia.org/wiki/Electrocorticography) и другие)
- Неинвазивные ([EEG](https://en.wikipedia.org/wiki/Electroencephalography), [NIRS](https://en.wikipedia.org/wiki/Near-infrared_spectroscopy) и другие)

EEG самый распространённый способ получения сигнала, поэтому, если не указано обратное, я имею его в виду по умолчанию.
 
## Активные  BCI 
### Basketparadigm
Это условное обозначение возможности контроля путем активации воображаемых движений. Дело в том, что моторная кора компактно расположена в центре головы, поэтому воображаемые движения разных частей тела хорошо классифицируются и используются для построения BCI. Пользователю, для работы с такими BCI, необходимо мысленно представлять как он совершает движения разными частями тела.

![image](https://habrastorage.org/webt/ad/bt/i7/adbti7bpfvnn1xs_u03niahtt0o.png)

Для облегчения проведения экспериментов ученые разрабатывают собственные фреймворки, например, [BCILAB](https://github.com/sccn/BCILAB). С его помощью провели эксперимент, чтобы продемонстрировать скептику возможность управления c помощью воображаемых движений. Результат составил 80% – так себе результат в условиях, когда у человека есть привычные альтернативы, но заслуживает высокой оценки, особенно, для неподготовленного респондента [7].
 
Этот же подход применили для управления горизонтом для авиасимулятора. Результаты неоднозначные, для 3-х респондентов удалось добиться результата в 94%, еще для 4-х 64% и меньше 60% еще для троих. Успех заключается в том, что первая троица управляла самолетам так же, как это делается штурвалом. Остальные пилоты недостаточно сосредоточились на внутреннем состоянии и совершали мускульные движения, что вносило негативный вклад в управление.
 
### Системы реабилитации
BCI, которые распознают моторные команды, хорошо изучены и уже используются для реабилитации пациентов переживших инсульт: для восстановления разорванных связей необходимых для управления парализованными конечностями. [Павел Бобров](https://www.researchgate.net/profile/Pavel_Bobrov) продемонстрировал результаты клинических испытаний реабилитационного комплекса для восстановления моторных функций рук, которые доказали эффективность использования. Причем, есть значимая разница для пациентов, кто начал реабилитацию спустя месяц и спустя 6 месяцев после инсульта, чем раньше начинается реабилитация, тем лучше эффект. [11]
 
Глава g.tec [Gunter Edlinger](https://www.researchgate.net/profile/Guenter_Edlinger) рассказал о работе специальных тренажерных залов для реабилитации, интересный момент, что в процесс реабилитации добавлена электростимуляция конечностей, и если выше использовалась электро-механическая установка, то здесь стимуляция током, что снижает стоимость комплекса.
<video>https://www.youtube.com/watch?v=oZCRRQh4S2A</video>
 
Если добавить в процесс элементы игры и соревнования, вовлечение будет выше, а значит пациент лучше пройдет через реабилитацию. В центре биоэлектрических интерфейсов ВШЭ под руководством [Алексея Осадчего](https://www.researchgate.net/profile/Alexei_Ossadtchi) разработали прототипы для улучшения процесса реабилитации. На видео демонстрируется прототип системы для двух человек, где они управляют сосудом, выполняя воображаемые моторные команды, пытаясь склонить сосуд в свою сторону:
<video>https://www.youtube.com/watch?v=GgGvYGjbuDE</video>
 
Однопользовательская игра:
<video>https://www.youtube.com/watch?v=lcK49Pt35Fc</video>
 
Или, например, алгоритм распознавания почерка по мышечной активности с помощью компактного массива электродов позволяет реконструировать написанное: [12]
![image](https://www.researchgate.net/publication/283974060/figure/fig5/AS:296597922566149@1447725863219/Within-Group-Reconstruction-several-reconstructed-trials-of-each-symbol-from.png)
 
Вершина в их работе – это работа над BCI в проекте [ExoAtlet](https://www.exoatlet.com), который позволяет людям с ограниченными возможностями передвигаться самостоятельно или использовать его для реабилитации.
<video>https://www.youtube.com/watch?v=w3tHfk1kPHs</video>
 
Инвазивные BCI – это более сложная тема, и сейчас эксперименты проводятся на животных или на людях, которым электроды установлены по медицинским показаниям. Была освещена серия исследований, которая показала, что возможно определять не только единичные компоненты (имеются ввиду все те же вымышленные движения), но и разделять движение, внимание, направление взгляда между собой. Доступна [запись](https://www.youtube.com/watch?v=vD7xRcgjNeQ) аналогичного доклада с конференции в Самаре.
 
## Реактивные BCI
![image](https://camo.githubusercontent.com/860b85bfa9b0b31fe66b446686c42470ed104794/68747470733a2f2f6d656469612e67697068792e636f6d2f6d656469612f395076614f76644276394f585466786647592f67697068792e676966)

Классический пример реактивного BCI это "спеллер" на эффекте P300, это "волна", которая появляется в ответ на выбор показанного стимула, ну а в "спеллере", таким стимулом служит определенным образом кодированные символы алфавита или команды. Пользователь должен мысленно взаимодействовать со стимулами, которые показывает система – считать количество вспышек выбранного символа.

Нельзя не упомянуть о проекте [Нейрочат](http://neurochat.pro/), который позволяет общаться людям с ограниченными возможностями:
<video>https://youtu.be/2wacB6Vsms0?t=104</video>

## Пассивные BCI
Базовая идея пассивных BCI – это оценка состояния человека, например, оценка когнитивной нагрузки (workload), она может быть применена в системах обучения, было проведено исследование, чтобы решить эту задачу.

Классификатор тренировали на следующих задачах:
- Для высокой нагрузки - респондент вычитал из 3-4 значных чисел 1-2 значные исключая простые варианты с десятками.
- Для легкой нагрузки - просили сосредоточится респондента на приятном воспоминании.

Точность алгоритма составила 70%. Классификатор протестировали на других задачах (умножение, игра в скрембл), и получили аналогичную точность, тем самым подтвердили факт, что можно сделать независимым классификатор от человека и задач.  [13]
Эту идею можно применить для контроля хирурга во время операции [14]. Решалась задача определения нагрузки на хирурга во время выполнения разных по сложности манипуляций на тренажере. Система научилась определять каким способом хирург выполняет операцию с высокой точностью.
 
Еще один вариант – это измерение степени расслабления. На основе состояния посетителя интерактивной инсталляции  в "[Музее молчания](https://www.facebook.com/pg/museumderstille/posts/)" создавалась живая картина, которая отражала его внутреннее состояние. [15]

![image](https://scontent.fhel3-1.fna.fbcdn.net/v/t31.0-8/11807436_866487846773980_3239282622646006842_o.jpg?_nc_cat=100&_nc_ht=scontent.fhel3-1.fna&oh=f49c03d6f9a1644cba1df962ac09697f&oe=5CA0B4E3)
  
Пассивные BCI можно использовать и для задач управления, довольно оригинальный подход предоставить человеку не непосредственный контроль за курсором, а лишь право судить о том, движется ли курсор по правильному пути к цели. Эксперимент был проведен на небольших матрицах размером 4х4 и 6х6 точек. Сначала систему тренировали на произвольном движении точки, и задача человека была определять в правильную ли сторону движется точка, далее тестировали в живом режиме и получили, что результат близок к оптимальному пути. [16] Можно посмотреть [демонстрацию](http://movie-usa.glencoesoftware.com/video/10.1073/pnas.1605155114/video-3).

### Midas touch problem и E-BCI интерфейсы

Управление курсором с помощью направления взгляда – простая задача, которая решается с помощью eye-tracker'инга (он же видеоокулография). Но в этих интерфейсах есть проблемы, например, непроизвольные движения глаз и проблема выбора, к слову, весьма символично ее называют проблемой прикосновения Мидаса – фригийского царя, любое прикосновение которого, обращало предмет в золото. Применений пассивных BCI позволяет решать эти проблемы.

Подход, где активный BCI использовался для совершения выбора при управлении с помощью eye-tracker'а, известен давно, но не отличается быстродействием. Исследование, где респонденты оценивали разные способы выбора по шкале [NASA TLX](https://en.wikipedia.org/wiki/NASA-TLX), показало, что вариант с BCI не быстрее по времени, чем вариант с долгой фиксацией для выбора объекта, но при этом BCI вызывает меньшую степень фрустрации [10].
 
Дальнейшая работа команды Торстена Цандера показала, что можно отличать сознательную фиксацию на объекте от бессознательной с точностью 90%[17]. Для эксперимента использовалась парадигма "Oddball" – респондент просматривал серию из фигур, содержащих фигуру, которую он хочет выбрать в сочетании с отвлекающими фигурами.

[Сергей Шишкин](http://brain.bio.msu.ru/shishkin.htm) рассказал о улучшении вышеописанного подхода [8]. Существенный плюс их решения – это снижение скорости выбора до 300мс-500мс, что требует очень быстрой классификации, для этого использовали EEGNet [9].



Механизмы внимания – это отдельная тема, которая может расширить области применения BCI и создавать системы для реабилитации пациентов с СДВГ, о базовой идее рассказывает [Mehdi Ordikhani](https://www.researchgate.net/profile/Mehdi_Ordikhani-Seyedlar) в своем [Tedtalk](https://www.ted.com/talks/mehdi_ordikhani_seyedlar_what_happens_in_your_brain_when_you_pay_attention#t-380226)
<video>https://www.youtube.com/watch?v=qKJv4S5peJQ</video>
 
## Стимуляция
Вопрос этики проведения экспериментов весьма остро стоит для нейроисследований, и животные принимают основной удар для исследований находящихся за гранью. Что если мы хотим воздействовать на какой-то определенный участок в глубине мозга? Сейчас это возможно только с помощью вживленных электродов. Но, например, в природе есть существа, которые чувствительны к магнитному полю, команда [Galit Pelled](https://www.researchgate.net/profile/Galit_Pelled) из Мичиганского университета выделили этот ген у рыб, внедрили крысам и научились контролировать их поведение действием магнитного поля [18]. Таким образом, возможно оказывать адресное воздействие на нужные участки, например, останавливать эпилептические припадки.
 
И целая группа исследований инвазивных интерфейсов от [Михаила Лебедева](https://www.researchgate.net/profile/Mikhail_Lebedev2) на макаках-резус: был построен интерфейс мозг-компьютер-мозг, который позволял, управляя виртуальными конечностями, получать тактильную обратную связь. Можно подробнее посмотреть отрывок из лекции "[Интерфейс между мозгом и компьютером](https://youtu.be/7gwb6TW5D6Q?t=2308)".
 
## Царство Deep Learning
Кроме того, что алгоритмы "глубокого обучения" позволяют добить и так уже высокую точность "машинного обучения", можно отметить то, что люди работают над "обратной задачей". Основываясь на быстрых данных EEG и MEG можно попытаться восстановить реальную активацию нейронов в мозге, которую сейчас показывает, например, метод fMRI, но с очень низким временным разрешением. Можно только порадоваться оптимизму и верить в скорый успех этой работы.
 
Еще одна проблема BCI на основе EEG или MEG – это то что результаты активности в разных областях мозга для одних и тех же компонент различаются среди пользователей, приходится учить нейросеть для каждого пользователя и задачи, что усложняет работу с системой и делает ее дороже. Тем не менее, здесь возможны изменения с "переносом обучения", когда нейросеть использует данные разных пользователей/в разных задачах и дообучивается онлайн, в результате этап калибровки может быть пропущен. [19]
 
## Hardware
Наконец-то, мы добрались до железок!

Тут важно сказать про 2 момента, с одной стороны, оборудование для BCI довольно громоздкое, человек в нем привлекает внимание, в одном из выступлений были продемонстрированы миниатюрные электроды, такие что человек в них ничем не выделяется. [20]

![image](https://ars.els-cdn.com/content/image/1-s2.0-S1388245710000866-gr2.sml)![image](https://ars.els-cdn.com/content/image/1-s2.0-S1388245710000866-gr1.sml)

К сожалению, вставить фото большего размера возможности нет, но вы можете посмотреть через [гугл фото](https://www.google.ru/search?q=Miniaturized+electroencephalographic+scalp+electrode+for+optimal+wearing+comfort&newwindow=1&source=lnms&tbm=isch&sa=X&ved=0ahUKEwjyuZqMtvreAhWOp4sKHWpgCxoQ_AUIDigB&biw=1440&bih=706#imgrc=YCsYr4QW7AERkM:).

Несмотря на всю миниатюрность, устанавливать эти электроды не удобно, придется приклеивать каждый отдельный электрод. Для ускорения используют различные приспособления:
-  EEG шапочки, в которых размечены отверстия под электроды
-  Обручи и шлемы различной конструкции, где в основном положение электродов фиксированное, только OpenBCI выделяется Ultracortex'ом, в котором электроды можно переставлять в зависимости от задач.

![image](https://habrastorage.org/webt/w-/1_/gu/w-1_gu1icslpibo8fmai7cdvjj0.jpeg)

Относительно свежая идея – это массивы из электродов [CeeGrid](http://ceegrid.com/home/concept/), для крепления в области уха, которые одновременно и невидимы, и легко устанавливаются, но существенный минус это ограниченность применения, хотя есть работы, которые показывают, что использовать этот вариант для ERP BCI реально [21].

![image](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b0/CeeGRID.jpg/800px-CeeGRID.jpg)

И вторая проблема – это необходимость в токопроводящем геле для качественного сигнала, тут показано, что различия допустимые, и использование сухих электродов оправдано [22], но все зависит от количества волос. Над этим вопросом так же работают, например, недавно Florida Research Instruments начала продавать удлинненный сухой электрод (на картинке ниже он слева), который отличается от первоначальной версии большей округлостью пинов и, как вы понимаете, вызывает меньше негативных ощущений у пользователей. Еще более продвинутые варианты – когда сами пины на электродах снабжены амортизацией, благодаря материалу или с помощью пружин (на картинке ниже они в центре и справа).

![image](https://habrastorage.org/webt/0j/hr/t5/0jhrt5qmurklbehrlbupoehw07e.jpeg)

## Заключение
Распространение BCI в массы не будет быстрым и легким, сейчас открыты весьма ограниченные возможности по пониманию состояний мозга, но прогресс в этой области нельзя игнорировать. Главное, что есть правильная тенденция на снижение стоимости устройств/предоставление устройств по подписке и появление проектов, которые ориентированы на энтузиастов.

Лично меня очень радует то, что среди раскрученных Emotive, MUSE, OpenBCI начинают появляться и российские проекты. На недавнем Нейрофоруме, который прошел в Петербурге, были продемонстрированы:
- [Нейроинтерфейс Опторитмограф](http://www.telebiomet.ru/ru/method/oborudovanie.html)
- [Нейролаборатория «Юный нейрофизиолог-инженер»](https://robotrack-rus.ru/1laboratory/)
- Проект [FreeEEG32](http://neuroidss.ru/FreeEEG32)
- Реабилитационный комплекс [iBrain](https://i-brain.tech/ru/) на основе EEG [SmartBCI](http://smartbci.com/)

Расширение доступных устройств делает область интерфейсов привлекательной для изучения и экспериментов. Порог вхождения низкий, всегда можно найти адекватную задачу, а улучшать алгоритмы можно до упора, приобретая новые знания и навыки. Чего я вам и желаю.

Такой я увидел область BCI, посмотрим, что интересного будет в следующем году.

## Источники
1 [Toward direct brain-computer communication](http://web.cs.ucla.edu/~vidal/BCI.pdf)
2 [Brain–computer interfaces for communication and control](http://www.cs.cmu.edu/~tanja/BCI/BCIreview.pdf)
3 [A spelling device for the paralysed](https://portal.ikw.uni-osnabrueck.de/~nbp/PDFs_Publications/Birbaumer_Nature_99.pdf)
4 [Talking off the top of your head: toward a mental prosthesis utilizing event-related brain potentials](http://www.farwellbrainfingerprinting.com/pdf/Farwell-Donchin-1988-Talking-Off-the-Top-of-Your-Head-BCI-brain-computer-interface.pdf)
5 [Classifying Single Trial EEG: Towards Brain Computer Interfacing](http://doc.ml.tu-berlin.de/bbci/publications/BlaCurMue02.pdf)
6 [Towards passive Brain–Computer interfaces: applying Brain–Computer interface technology to human-machine systems in general](https://www.researchgate.net/publication/50850896_Towards_passive_Brain-Computer_interfaces_applying_Brain-Computer_interface_technology_to_human-machine_systems_in_general)
7 [Team PhyPA: Brain-computer interfacing for everyday human-computer interaction ](https://www.researchgate.net/publication/317752429_Team_PhyPA_Brain-computer_interfacing_for_everyday_human-computer_interaction)
8 [The Expectation Based Eye-Brain-Computer Interface: An Attempt of Online Test ](https://dl.acm.org/citation.cfm?id=3038446)
  [EEG Negativity in Fixations Used for Gaze-Based Control: Toward Converting Intentions into Actions with an Eye-Brain-Computer Interface](https://www.frontiersin.org/articles/10.3389/fnins.2016.00528/full)
9 [EEGNet: A Compact Convolutional Network for EEG-based Brain-Computer Interfaces](https://arxiv.org/abs/1611.08024)
10 [Combining Eye Gaze Input With a Brain–Computer Interface for Touchless Human–Computer Interaction](https://www.researchgate.net/publication/220302370_Combining_Eye_Gaze_Input_With_a_Brain-Computer_Interface_for_Touchless_Human-Computer_Interaction)
11 [Роботизированные устройства в реабилитации после инсульта](https://www.researchgate.net/publication/319535393_Robotizirovannye_ustrojstva_v_reabilitacii_posle_insulta)
12 [A dynamical model improves reconstruction of handwriting from multichannel electromyographic recordings](https://www.researchgate.net/publication/283974060_A_dynamical_model_improves_reconstruction_of_handwriting_from_multichannel_electromyographic_recordings)
13 [Team PhyPA: Brain-Computer Interfacing for Everyday HumanComputer Interaction ](https://noctifer.net/files/zander2017pp-phypa.pdf)
14 [Automated Task Load Detection with Electroencephalography](https://doi.org/10.1142/S2424905X17500039)
15 [Passive Brain-Computer Interfacing in the Museum of Stillness ](https://www.researchgate.net/publication/324983673_Passive_Brain-Computer_Interfacing_in_the_Museum_of_Stillness)
16 [Neuroadaptive technology enables implicit cursor control based on medial prefrontal cortex activity ](https://www.researchgate.net/publication/311627969_Neuroadaptive_technology_enables_implicit_cursor_control_based_on_medial_prefrontal_cortex_activity)
17 [A Passive Brain-Computer Interface for Supporting Gaze-Based Human-Machine Interaction](https://link.springer.com/chapter/10.1007/978-3-642-39188-0_71)
18 [Wireless control of cellular function by activation of a novel protein responsive to electromagnetic fields](https://www.researchgate.net/publication/325652728_Wireless_control_of_cellular_function_by_activation_of_a_novel_protein_responsive_to_electromagnetic_fields)
19 [Robust and highly adaptable brain-computer interface with convolutional net architecture based on a generative model of neuromagnetic measurements](https://www.researchgate.net/publication/325413648_Robust_and_highly_adaptable_brain-computer_interface_with_convolutional_net_architecture_based_on_a_generative_model_of_neuromagnetic_measurements)
20 [Miniaturized electroencephalographic scalp electrode for optimal wearing comfort](https://www.semanticscholar.org/paper/Miniaturized-electroencephalographic-scalp-for-Nikulin-Kegeles/b1afab643782dbd95ba34230000b52462c3b408e)
21 [Event-Related Potentials Measured From In and Around the Ear Electrodes Integrated in a Live Hearing Device for Monitoring Sound Perception](https://www.semanticscholar.org/paper/Event-Related-Potentials-Measured-From-In-and-the-a-Denk-Grzybowski/92d6ff906db1850426b3d472d0c14b3a09719b41)
22 [A dry EEG-system for scientific research and brain–computer interfaces](https://dx.doi.org/10.3389%2Ffnins.2011.00053)

