# Глава 8.2. Подготовка за практически изпит – част II

В настоящата глава ще разгледаме един **практически изпит по основи на програмирането**, проведен в СофтУни на 18 декември 2016 г. Задачите дават добра представа какво можем да очакваме на приемния изпит по програмиране в СофтУни. Изпитът покрива изучавания учебен материал от настоящата книга и от курса "Programming Basics" в СофтУни.

## Изпитни задачи

Традиционно приемният изпит в СофтУни се състои от **6 практически задачи по програмиране**:
 - Задача с прости сметки (без проверки).
 - Задача с единична проверка.
 - Задача с по-сложни проверки.
 - Задача с единичен цикъл.
 - Задача с вложени цикли (чертане на фигурка на конзолата).
 - Задача с вложени цикли и по-сложна логика.
 
Да разгледаме една **реална изпитна тема**, задачите в нея и решенията им.


## Задача: разстояние

Напишете програма, която да пресмята **колко километра изминава кола**, за която знаем **първоначалната скорост** \(км/ч\), **времето** в минути, след което **увеличава скоростта с 10%**, **второ време**, след което **намалява скоростта с 5%**, и **времето до края** на пътуването. За да намерите разстоянието трябва да **превърнете минутите в часове** \(например 70 минути = 1.1666 часа\).

### Входни данни

От конзолата се четат **4 реда**:
* **Първоначалната скорост в км/ч** – цяло число в интервала [**1 … 300**].
* **Първото време в минути** – цяло число в интервала [**1 … 1000**].
* **Второто време в минути** – цяло число в интервала [**1 … 1000**].
* **Третото време в минути** – цяло число в интервала [**1 … 1000**].

### Изходни данни

Да се отпечата на конзолата едно число: **изминатите километри**, форматирани до **втория символ след десетичния знак**.

### Примерен вход и изход

|Вход|Изход|Обяснения|
|-----|-----|-----|
|90<br>60<br>70<br>80|330.90|**Разстояние с първоначална скорост**: 90 км/ч \* 1 час (60 мин) = **90 км**<br>**След увеличението**: 90 + 10% = 99.00 км/ч \* 1.166 часа (70 мин) = **115.50 км**<br>**След намаляването**: 99 - 5% = 94.05 км/ч \* 1.33 часа (80 мин) = **125.40 км**<br>**Общо изминати**: **330.9 км**|

|Вход|Изход|Обяснения|
|-----|-----|-----|
|140<br>112<br>75<br>190|917.12|**Разстояние с първоначална скорост**: 140 км/ч \* 1.86 часa (112 мин) = **261.33 км**<br>**След увеличението**: 140 + 10% = 154.00 км/ч \* 1.25 часа (75 мин) = **192.5 км**<br>**След намаляването**: 154.00 - 5% = 146.29 км/ч \* 3.16 часа (190 мин) = **463.28 км**<br>**Общо изминати**: **917.1166 км**|

### Насоки и подсказки

Вероятно е подобно условие да изглежда на пръв поглед **объркващо** и непълно, което **придава** допълнителна **сложност** на една лесна задача. Нека **разделим** заданието на няколко **подзадачи** и да се опитаме да **решим** всяка една от тях, което ще ни отведе и до крайния резултат:

* Нека **първата** подзадача бъде да **прочетем входните данни**, които потребителя въвежда, и да ги **запазим в подходящи променливи**.
* **Изпълнение** на основната програмна **логика**, което в нашия случай се свежда до прости пресмятания на данните, които вече имаме.
* **Пресмятане** и оформяне на крайния **резултат**.

**Съществената** част от програмната логика **се изразява** в това да **пресметнем** какво ще бъде **изминатото разстояние след всички промени** в скоростта. Тъй като по време на **изпълнението** на програмата, част от **данните**, с които разполагаме, **се променят**, то бихме могли да **разделим** програмния **код** на няколко **логически** обособени **части**:

* **Пресмятане** на изминатото **разстояние** с първоначална скорост.
* Промяна на **скоростта** и пресмятане на изминатото **разстояние**.
* Последна промяна на **скоростта** и **пресмятане**.
* **Сумиране**.

За **прочитането** на данните от **конзолата** използваме следната **функция**:

![](assets/chapter-8-2-images/01.Distance-01.png)

По условие **входните данни** се въвеждат на **четири** отделни реда, по тази причина следва да изпълним **предходния** код общо **четири** пъти.

![](assets/chapter-8-2-images/01.Distance-02.png)

За **извършване** на **пресмятанията** избираме да използваме тип **`decimal`**.

<table>
<tr>
<td width=10%><img src="/assets/alert-icon.png" style="max-width:50px" /></td>
<td>Типът данни за реални числа с десетична точност в <b>C#</b> е 128-битовият тип <b><code>decimal</code></b>. Той има <b>точност</b> от <b>28 до 29</b> десетични цифри. <b>Минималната</b> му стойност е <b>-7.9×10^28</b>, а <b>максималната</b> е <b>+7.9×10^28</b>. Стойността му по подразбиране е <b>0.0m</b> или <b>0.0M</b>. Символът <b><code>m</code></b> накрая указва изрично, че числото е от тип <b><code>decimal</code></b> (по <b>подразбиране</b> всички реални числа са от тип <b><code>double</code></b>). Най-близките до <b>0</b> числа, които могат да бъдат записани в <b><code>decimal</code></b>, са <b>±1.0 × 10^-28</b>. Видно е, че <b><code>decimal</code> не може</b> да съхранява <b>много големи</b> положителни и отрицателни числа (например със стотици цифри), нито стойности <b>много близки до 0</b>. За сметка на това този тип почти <b>не прави грешки</b> при финансови пресмятания, защото представя числата като <b>сума от степени на числото 10</b>, при което <b>загубите</b> от закръгляния са много <b>по-малки</b>, отколкото когато се използва двоично представяне. Реалните числа от тип <b><code>decimal</code></b> са изключително <b>удобни за пресмятания с пари</b> – изчисляване на приходи, задължения, данъци, лихви и т.н.
</td>
</tr>
</table>

**Повече** за различните **типове** данни в езика C# може да прочетете тук:

[http://www.introprogramming.info/intro-csharp-book/read-online/glava2-primitivni-tipove-i-promenlivi/\#\_Toc298863935](http://www.introprogramming.info/intro-csharp-book/read-online/glava2-primitivni-tipove-i-promenlivi/#_Toc298863935)

По този начин успяхме да се справим успешно с **първата подзадача**. **Следващата** стъпка е да **преобразуваме входните данни** в подходящи **типове**, за да можем да извършим необходимите пресмятания. Избираме да използваме тип **`Int32`** или **`int`**, тъй като в условието на задачата e упоменато, че входните данни ще бъдат в **определен интервал**, за който този тип данни е напълно достатъчен. **Преобразуването** извършваме по следния начин:

![](assets/chapter-8-2-images/01.Distance-03.png)

Първоначално **запазваме** една **променлива**, която ще използваме многократно. Този подход на централизация ни дава **гъвкавост** и **възможност** да **променяме** цялостния резултат на програмата с минимални усилия. В случай, че се наложи да променим стойността, трябва да го направим само на **едно място в кода**, което ни спестява време и усилия. 

![](assets/chapter-8-2-images/01.Distance-04.png)

<table>
<tr>
<td width=10%><img src="/assets/alert-icon.png" style="max-width:50px" /></td>
<td><strong>Избягването на повтарящ се код</strong> (централизация на програмната логика) в задачите, които разглеждаме в настоящата книга, изглежда на пръв поглед излишна, но този подход е от съществено значение при изграждането на мащабни приложения в реална работна среда и упражняването му в начален стадий на изучаване само ще подпомогне усвояването на един качествен стил на програмиране.
</td>
</tr>
</table>

**Изминалото време** (в часове) пресмятаме като **разделим времето на 60** (минутите в един час). **Изминатото разстояние** намираме като **умножим началната скорост с изминалото време** (в часове). След това променяме скоростта, като я увеличаваме с **10%** по условие. Пресмятането на **процентите**, както и следващите изминати **разстояния**, извършваме по следния начин:

* **Интервалът от време** (в часове) намираме като **разделим** зададения интервал в минути на минутите, които се съдържат в един час (60).
* **Изминатото** разстояние намираме като **умножим** интервала (в часове) по скоростта, която получихме след увеличението.
* Следващата стъпка е да **намалим скоростта** с **5%**, както е зададено по условие.
* Намираме **оставащото разстояние** по описания начин в първите две точки.

![](assets/chapter-8-2-images/01.Distance-05.png)

До този момент успяхме да **изпълним две** от **най-важните подзадачи**, а именно **приемането на данните** и **тяхната обработка**. Остава ни само да **пресметнем крайния резултат**. Тъй като по условие се изисква той да бъде **форматиран** до **2** символа след десетичния знак, можем да го направим по следния **начин**:

![](assets/chapter-8-2-images/01.Distance-06.png)

В случай че сте работили правилно и изпълните програмата с входните данни от условието на задачата, ще се уверите, че тя работи коректно.

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.bg/Contests/Practice/Index/517#0](https://judge.softuni.bg/Contests/Practice/Index/517#0).


## Задача: смяна на плочки

Хараламби има **събрани пари**, с които иска да **смени плочките на пода в банята**. Като **подът е правоъгълник**, а **плочките са триъгълни**. Напишете **програма**, която да **пресмята дали събраните пари ще му стигнат**. **От конзолата се четат широчината и дължината на пода**, както и **едната страна на триъгълника с височината към нея**. Трябва да **пресметнете колко плочки са нужни,** за да се покрие пода. **Броят** на плочките **трябва да се закръгли към по-високо цяло число** и **да се прибавят още 5 броя** за фира. **От конзолата се четат** още – **цената на плочка** и **сумата за работата** на майстор.

### Входни данни

От конзолата се четат 7 реда:
* **Събраните пари**.
* **Широчината на пода**.
* **Дължината на пода**.
* **Страната на триъгълника**.
* **Височината на триъгълника**.
* **Цената на една плочка**.
* **Сумата за майстора**.

**Всички** числа са реални числа в интервала [**0.00 … 5000.00**].

### Изходни данни

На конзолата трябва да се отпечата на **един ред**:

* Ако парите **са достатъчно**:
   * “{Оставащите пари} lv left.”
* Ако парите **НЕ СА достатъчно**:
   * “You'll need {Недостигащите пари} lv more.”

Резултатът трябва да е **форматиран до втория символ** след десетичния знак.

### Примерен вход и изход

|Вход|Изход|Обяснения|
|-----|-----|-----|
|500<br>3<br>2.5<br>0.5<br>0.7<br>7.80<br>100|25.60 lv left.|**Площ на пода** &rarr; 3 \* 2.5 = **7.5**<br>**Площта на плочка** &rarr; 0.5 \* 0.7 / 2 = **0.175**<br>**Необходими плочки** &rarr; 7.5 / 0.175 = 42.857… = **43 + 5 фира** = **48**<br>**Обща сума** &rarr; 48 \* 7.8 + 100 (майстор) = **474.4**<br>**474.4 < 500** &rarr; **остават 25.60 лева**|

|Вход|Изход|Обяснения|
|-----|-----|-----|
|1000<br>5.55<br>8.95<br>0.90<br>0.85<br>13.99<br>321|You'll need 1209.65 lv more.|**Площ на пода** &rarr; 5.55 \* 8.95 = **49.67249**<br>**Площта на плочка** &rarr; 0.9 \* 0.85 / 2 = **0.3825**<br>**Необходими плочки** &rarr; 49.67249 / 0.3825 = 129.86… = **130 + 5 фира** = **135**<br>**Обща сума** &rarr; 135 * 13.99 + 321 (майстор) = **2209.65**<br>**2209.65 > 1000** &rarr; **не достигат 1209.65 лева**|

### Насоки и подсказки

Следващата задача изисква от нашата програма да приема повече входни данни и извърши по-голям брой изчисления, въпреки че решението е **идентично**. Приемането на данните от потребителя извършваме по добре **познатия ни начин**. Обърнете внимание, че в раздел **Вход** в условието е упоменато, че всички входни данни ще бъдат **реални числа** и поради тази причина бихме използвали тип **`decimal`**.

След като вече разполагаме с всичко необходимо, за да изпълним програмната логика, можем да пристъпим към следващата част. Как бихме могли да **изчислим** какъв е **необходимият** брой плочки, които ще бъдат достатъчни за покритието на целия под? Условието, че плочките имат **триъгълна** форма, би могло да доведе до объркване, но на практика задачата се свежда до съвсем **прости изчисления**. Бихме могли да пресметнем каква е **общата площ на пода** по формулата за намиране на площ на правоъгълник, както и каква е **площта на една плочка** по съответната формула за триъгълник.

За да пресметнем какъв **брой плочки** са необходими, **разделяме площта на пода на площта на една плочка** (като не забравяме да прибавим 5 допълнителни броя плочки, както е по условие).

<table>
<tr>
<td width="10%"><img src="/assets/alert-icon.png" style="max-width:50px" /></td>
<td>Обърнете внимание, че в условието е упоменато да закръглим броя на плочките, получен от делението, до по-високо цяло число, след което да прибавим 5. Потърсете повече информация за системната функционалност за това: <code><strong>Math.Ceiling(…)</strong></code>.
</td>
</tr>
</table>

До крайния резултат можем да стигнем, като **пресметнем общата сума**, която е необходима, за да бъде покрит целия под, като **съберем цената на плочките с цената за майстора**, която имаме от входните данни. Можем да се досетим, че **общият разход** за плочките можем да получим, като **умножим броя плочки по цената за плочка**. Дали сумата, с която разполагаме, ще бъде достатъчна, разбираме като сравним събраните до момента пари (от входните данни) и общите разходи.

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.bg/Contests/Practice/Index/517#1](https://judge.softuni.bg/Contests/Practice/Index/517#1).


## Задача: магазин за цветя

Магазин за цветя предлага 3 вида цветя: **хризантеми**, **рози** и **лалета**. Цените зависят от сезона.

|Сезон|Хризантеми|Рози|Лалета|
|:---:|:---:|:---:|:---:|
|пролет / лято<br>есен / зима|2.00 лв./бр.<br>3.75 лв./бр.|4.10 лв./бр.<br>4.50 лв./бр.|2.50 лв./бр.<br>4.15 лв./бр.|

В празнични дни цените на всички цветя се **увеличават с 15%.** Предлагат се следните **отстъпки**:
* За закупени повече от 7 лалета през пролетта – **5% от цената** на целия букет.
* За закупени 10 или повече рози през зимата – **10% от цената** на целия букет.
* За закупени повече от 20 цветя общо през всички сезони – **20% от цената** на целия букет.

**Отстъпките се правят по така написания ред и могат да се наслагват! Всички отстъпки важат след оскъпяването за празничен ден!**

Цената за аранжиране на букета винаги е **2 лв.** Напишете програма, която изчислява **цената за един букет**.

### Входни данни

Входът се чете от **конзолата** и съдържа **точно 5 реда**:
* На първи ред е **броят на закупените хризантеми** – цяло число в интервала [**0 … 200**].
* На втория ред е **броят на закупените рози** – цяло число в интервала [**0 … 200**].
* На третия ред е **броят на закупените лалета** – цяло число в интервала [**0 … 200**].
* На четвъртия ред е посочен **сезонът** – [**Spring, Summer, Autumn, Winter**].
* На петия ред е посочено **дали денят е празник** – [**Y - да / N - не**].

### Изходни данни

Да се отпечата на конзолата 1 число – **цената на цветята**, форматирана до втория символ след десетичния знак.

### Примерен вход и изход

|Вход|Изход|Обяснения|
|---|---|---|
|2<br>4<br>8<br>Spring<br>Y<br>|46.14|**Цена**: 2\*2.00 + 4\*4.10 + 8\*2.50 = 40.40 лв.<br>**Празничен ден**: 40.40 + 15% = 46.46 лв.<br>**5% намаление** за повече от 7 лалета през пролетта: 44.14<br>Общо цветята са 20 или по-малко: **няма намаление**<br>44.14 + 2 **за аранжиране** = 46.14 лв.|

|Вход|Изход|Обяснения|
|---|---|---|
|3<br>10<br>9<br>Winter<br>N<br>|69.39|**Цена**: 3\*3.75 + 10\*4.50 + 9\*4.15 = 93.60 лв.<br>**Не е празничен ден**: няма увеличение<br>**10% намаление** за 10 или повече рози през зимата: 84.24<br>Общо цветята са повече от 20: **20% намаление** = 67.392<br>67.392 + 2 **за аранжиране** = 69.392 лв.|

|Вход|Изход|
|---|---|
|10<br>10<br>10<br>Autumn<br>N|101.20|

### Насоки и подсказки

След като прочитаме внимателно условието разбираме, че отново се налага да извършваме **прости пресмятания**, но с разликата, че този път ще са необходими и **повече** логически **проверки**. Следва да обърнем повече **внимание** на това в какъв момент се **извършват промените** по крайната цена, за да можем правилно да изградим логиката на нашата програма. Отново, удебеленият текст ни дава достатъчно **насоки** как да подходим. Като за начало, отделяме вече **дефинираните** стойности в **променливи**, както направихме и в предишните задачи:

![](assets/chapter-8-2-images/03.Flowers-01.png)

Правим същото и за останалите вече дефинирани стойности:

![](assets/chapter-8-2-images/03.Flowers-02.png)

Следващата ни подзадача е да **прочетем** правилно **входните** данни от конзолата. Подхождаме по добре познатия ни вече начин, но този път **комбинираме две** отделни функции – една за **прочитане** на ред от конзолата и друга за **преобразуването** му в числен тип данни:

![](assets/chapter-8-2-images/03.Flowers-03.png)

Нека помислим кой е най-подходящият начин да **структурираме** нашата програмна логика. От условието става ясно, че пътят на програмата се разделя основно на две части: **пролет / лято** и **есен / зима**. Разделението правим с условна конструкция, като преди това заделяме променливи за **цените** на отделните цветя, както и за **крайния резултат**.

![](assets/chapter-8-2-images/03.Flowers-04.png)

Остава ни да извършим **няколко проверки** относно **намаленията** на различните видове цветя, в зависимост от сезона, и да модифицираме крайния резултат. 

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.bg/Contests/Practice/Index/517#2](https://judge.softuni.bg/Contests/Practice/Index/517#2).


## Задача: оценки

Напишете програма, която да **пресмята статистика на оценки** от изпит. В началото програмата получава **броя на студентите**, явили се на изпита и за **всеки студент неговата оценка**. На края програмата трябва да **изпечата процента на студенти** с оценка между 2.00 и 2.99, между 3.00 и 3.99, между 4.00 и 4.99, 5.00 или повече, както и **средният успех** на изпита.

### Входни данни

От конзолата се четат **поредица от числа, всяко на отделен ред**:
* На първия ред – **броят на студентите явили се на изпит** – цяло число в интервала [**1 … 1000**].
* За **всеки един студент** на отделен ред – **оценката от изпита** – реално число в интервала [**2.00 … 6.00**].

### Изходни данни

Да се отпечатат на конзолата **5 реда**, които съдържат следната информация:
* "Top students: {процент студенти с успех 5.00 или повече}%".
* "Between 4.00 and 4.99: {между 4.00 и 4.99 включително}%".
* "Between 3.00 and 3.99: {между 3.00 и 3.99 включително}%".
* "Fail: {по-малко от 3.00}%".
* "Average: {среден успех}".

### Примерен вход и изход

|Вход|Изход|Обяснения|
|---|---|---|
|10<br>3.00<br>2.99<br>5.68<br>3.01<br>4<br>4<br>6.00<br>4.50<br>2.44<br>5<br>|Top students: 30.00%<br>Between 4.00 and 4.99: 30.00%<br>Between 3.00 and 3.99: 20.00%<br>Fail: 20.00%<br>Average: 4.06|5 и повече - **трима** = 30% от 10<br>Между 4.00 и 4.99 - **трима** = 30% от 10<br>Между 3.00 и 3.99 - **двама** = 20% от 10<br>Под 3 - **двама** = 20% от 10<br>Средният успех е: 3 + 2.99 + 5.68 + 3.01 + 4 + 4 + 6 + 4.50 + 2.44 + 5 = 40.62 / 10 = 4.062|

|Вход|Изход|
|---|---|
|6<br>2<br>3<br>4<br>5<br>6<br>2.2|Top students: 33.33%<br>Between 4.00 and 4.99: 16.67%<br>Between 3.00 and 3.99: 16.67%<br>Fail: 33.33%<br>Average: 3.70|

### Насоки и подсказки

От условието виждаме, че **първо** ще ни бъде подаден **броя** на студентите, а едва **след това оценките** им. По тази причина **първо** в една променлива от тип **`int`** ще прочетем **броя** на студентите. За да прочетем и обработим самите оценки, ще използваме **`for`** цикъл. Стойността на променливата **`int`** ще бъде **крайната** стойност на променливата **`i`** от цикъла. По този начин **всички** итерации на цикъла ще прочетат **всяка една оценка**. 

![](assets/chapter-8-2-images/05.Grades-01.png)

Преди да се изпълни кода от `for` цикъла заделяме променливи, в които ще пазим **броя на студентите** за всяка група: слаби резултати (до 2.99), резултати от 3 до 3.99, от 4 до 4.99 и оценки над 5. Ще ни е необходима и още една променлива, в която да пазим **сумата на всички оценки**, с помощта на която ще изчислим средната оценка на всички студенти.

![](assets/chapter-8-2-images/05.Grades-02.png)

Завъртаме **цикъла** и в него **декларираме още една** променлива, в която ще запазваме **текущата** въведена оценка. Променливата ще е от тип **`double`** и на всяка итерация проверяваме **каква е стойността ѝ**. Според тази стойност, **увеличаваме** броя на студентите в съответната група с **1**, като не забравяме да увеличим и **общата** сума на оценките, която също следим.

![](assets/chapter-8-2-images/05.Grades-03.png)

Какъв **процент** заема дадена **група студенти** от общия брой, можем да пресметнем като **умножим броя на студентите** от съответната група по **100** и след това разделим на **общия брой студенти**. 

<table>
<tr>
<td width="10%"><img src="/assets/alert-icon.png" style="max-width:50px" /></td>
<td>Обърнете внимание с какъв числен тип данни работите при извършване на тези пресмятания.
</td>
</tr>
</table>

**Крайният** резултат оформяме по добре познатия ни начин **до втория символ** след десетичния знак.

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.bg/Contests/Practice/Index/517#3](https://judge.softuni.bg/Contests/Practice/Index/517#3).


## Задача: коледна шапка

Да се напише програма, която прочита от конзолата **цяло число `n`** и чертае **коледна шапка** с ширина **4 \* `n` + 1 колони** и височина **2 \* `n` + 5 реда** като в примерите по-долу.

### Входни данни

Входът се чете от конзолата – едно **цяло число `n`** в интервала [**3 … 100**].

### Изходни данни

Да се отпечата на конзолата **коледна шапка**, точно както в примерите.

### Примерен вход и изход

|Вход|Изход|
|:-----:|:-----:|
|4|<code>......./&#124;\\.......</code><br><code>.......\\&#124;/.......</code><br><code>.......\*\*\*.......</code><br><code>......\*-\*-\*......</code><br><code>.....\*--\*--\*.....</code><br><code>....\*---\*---\*....</code><br><code>...\*----\*----\*...</code><br><code>..\*-----\*-----\*..</code><br><code>.\*------\*------\*.</code><br><code>\*-------\*-------\*</code></br><code>\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</code><br><code>\*.\*.\*.\*.\*.\*.\*.\*.\*</code><br><code>\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</code>|

|Вход|Изход|
|:-----:|:-----:|
|7|<code>............./&#124;\\.............</code><br><code>.............\\&#124;/.............</code><br><code>.............\*\*\*.............</code><br><code>............\*-\*-\*............</code><br><code>...........\*--\*--\*...........</code><br><code>..........\*---\*---\*..........</code><br><code>.........\*----\*----\*.........</code><br><code>........\*-----\*-----\*........</code><br><code>.......\*------\*------\*.......</code><br><code>......\*-------\*-------\*......</code><br><code>.....\*--------\*--------\*.....</code><br><code>....\*---------\*---------\*....</code><br><code>...\*----------\*----------\*...</code><br><code>..\*-----------\*-----------\*..</code><br><code>.\*------------\*------------\*.</code><br><code>\*-------------\*-------------\*</code><br><code>\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</code><br><code>\*.\*.\*.\*.\*.\*.\*.\*.\*.\*.\*.\*.\*.\*.\*</code><br><code>\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</code><br>|

### Насоки и подсказки

При задачите за **чертане** с конзолата, най-често потребителят въвежда **едно цяло число**, което е свързано с **общата големина на фигурката**, която трябва да начертаем. Тъй като в условието е упоменато как се изчисляват общата дължина и широчина на фигурката, можем да ги използваме за **отправни точки**. От примерите ясно се вижда, че без значение какви са входните данни, винаги имаме **първи два реда**, които са с почти идентично съдържание.

<code>......./\|\\.......</code><br><code>.......\\\|/.......</code>

Забелязваме също така, че **последните три реда** винаги присъстват, **два** от които са напълно **еднакви**.

<code>\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</code><br><code>\*.\*.\*.\*.\*.\*.\*.\*.\*</code><br><code>\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</code>

От тези наши наблюдения можем да изведем **формулата** за **височина на променливата част** на коледната шапка. Използваме зададената по условие формула за общата височина, като изваждаме големината на непроменливата част. Получаваме **`(2 * n + 5) – 5`** или **`2 * n`**.

За **начертаването** на **динамичната** или променлива част от фигурката ще използваме **цикъл**. Размерът на цикъла ще бъде от **0** до **широчината**, която имаме по условие, а именно **`4 * n + 1`**. Тъй като тази формула ще използваме на **няколко места** в кода, е добра практика да я изнесем в **отделна променлива**. Преди изпълнението на цикъла би следвало да **заделим променливи** за **броя** на отделните символи, които участват в динамичната част: **точки** и **тирета**. Чрез изучаване на примерите можем да изведем формули и за **стартовите стойности** на тези променливи. Първоначално **тиретата** са **0**, но броя на **точките** ясно се вижда, че можем да получим като от **общата широчина** извадим **3** (броя символи, които изграждат върха на коледната шапка) и след това **разделим на 2**, тъй като броя точки от двете страни на шапката е еднакъв.

<code>.......\*\*\*.......</code><br><code>......\*-\*-\*......</code><br><code>.....\*--\*--\*.....</code><br><code>....\*---\*---\*....</code><br><code>...\*----\*----\*...</code><br><code>..\*-----\*-----\*..</code><br><code>.\*------\*------\*.</code><br><code>\*-------\*-------\*</code>

Остава да изпълним тялото на цикъла, като **след всяко** начертаване **намалим** броя на точки с **1**, а **тиретата увеличим** с **1**. Нека не забравяме да начертаем и по една **звездичка** между тях.
Последователността на чертане в тялото на цикъла е следната:

* Символен низ от точки
* Звезда
* Символен низ от тирета
* Звезда
* Символен низ от тирета
* Звезда
* Символен низ от точки

В случай че сме работили правилно получаваме фигурки, идентични на тези от примерите.

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.bg/Contests/Practice/Index/517#4](https://judge.softuni.bg/Contests/Practice/Index/517#4).


## Задача: комбинации от букви

Напишете програма, която да принтира на конзолата **всички комбинации от 3 букви** в зададен интервал, като се пропускат комбинациите, **съдържащи зададена от конзолата буква**. Накрая трябва да се принтира броят отпечатани комбинации.

### Входни данни

Входът се чете от **конзолата** и съдържа **точно 3 реда**:
* Малка буква от английската азбука за начало на интервала – от **'a'** до **'z'**.
* Малка буква от английската азбука за край на интервала – от **първата буква** до **'z'**.
* Малка буква от английската азбука – от **'a'** до **'z'** – като комбинациите, съдържащи тази буква се пропускат.

### Изходни данни

Да се отпечатат на един ред **всички комбинации**, отговарящи на условието, следвани от **броя им**, разделени с интервал.

### Примерен вход и изход

|Вход|Изход|Обяснения|
|---|---|---|
|a<br>c<br>b|aaa aac aca acc caa cac cca ccc 8|Всички възможни комбинации с буквите '**а**', '**b**' и '**c**' са:<br>aaa aab aac aba abb abc aca acb acc baa bab bac bba bbb bbc bca bcb bcc caa cab cac cba cbb cbc cca ccb ccc<br>Комбинациите, **съдържащи 'b', не са валидни**.<br>Остават **8** валидни комбинации.|

|Вход|Изход|
|---|---|
|f<br>k<br>h|fff ffg ffi ffj ffk fgf fgg fgi fgj fgk fif fig fii fij fik fjf fjg fji fjj fjk fkf fkg fki fkj fkk gff gfg gfi gfj gfk ggf ggg ggi ggj ggk gif gig gii gij gik gjf gjg gji gjj gjk gkf gkg gki gkj gkk iff ifg ifi ifj ifk igf igg igi igj igk iif iig iii iij iik ijf ijg iji ijj ijk ikf ikg iki ikj ikk jff jfg jfi jfj jfk jgf jgg jgi jgj jgk jif jig jii jij jik jjf jjg jji jjj jjk jkf jkg jki jkj jkk kff kfg kfi kfj kfk kgf kgg kgi kgj kgk kif kig kii kij kik kjf kjg kji kjj kjk kkf kkg kki kkj kkk 125|

|Вход|Изход|
|---|---|
|a<br>c<br>z|aaa aab aac aba abb abc aca acb acc baa bab bac bba bbb bbc bca bcb bcc caa cab cac cba cbb cbc cca ccb ccc 27|

### Насоки и подсказки

За последната задача имаме по условие входни данни на **3 реда**, които са представени от по един символ от **ASCII таблицата** ([http://www.asciitable.com/](http://www.asciitable.com/)). Бихме могли да използваме вече **дефинирана функция** в езика C#, като преобразуваме входните данни в тип данни **`char`** по следния начин:

![](assets/chapter-8-2-images/06.Letters-01.png)

Нека помислим как бихме могли да стигнем до **крайния резултат**. В случай че условието на задачата e да се принтират всички от началния до крайния символ (с пропускане на определена буква), как бихме постъпили? 

Най-лесният и удачен начин е да използваме **цикъл**, като преминем през **всички символи** и принтираме тези, които са **различни** от **буквата**, която трябва да пропуснем. Едно от предимствата на езика C#, е че имаме възможност да използваме различен тип данни за циклична променлива:

![](assets/chapter-8-2-images/06.Letters-02.png)

Резултатът от изпълнението на кода е всички букви от **а** до **z** включително, принтирани на един ред и разделени с интервал. Това прилича ли на крайния резултат от нашата задача? Трябва да измислим **начин**, по който да се принтират по **3 символа**, както е по условие, вместо по **1**. Изпълнението на програмата много прилича на игрална машина. Там най-често печелим, ако успеем да наредим няколко еднакви символа. Да речем, че на машината имаме места за три символа. Когато **спрем** на даден **символ** на първото място, на останалите две места **продължават** да се изреждат символи от всички възможни. В нашия случай **всички възможни** са буквите от началната до крайната такава, зададена от потребителя, а решението на нашата програма е идентично на начина, по който работи игралната машина.

Използваме **цикъл**, който минава през **всички символи** от началната до крайната буква включително. На **всяка итерация** на **първия** цикъл пускаме **втори** със същите параметри (но **само ако** буквата на първия цикъл е валидна, т.е. не съвпада с тази, която трябва да изключим по условие). На всяка итерация на **втория** цикъл пускаме още **един** със **същите параметри** и същата **проверка**. По този начин ще имаме три вложени цикъла, като в тялото на **последния** ще принтираме символите.

![](assets/chapter-8-2-images/06.Letters-03.png)

Нека не забравяме, че се изисква от нас да принтираме и **общия брой валидни комбинации**, които сме намерили, както и че те трябва да се принтират на **същия ред**, разделени с интервал.

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.bg/Contests/Practice/Index/517#5](https://judge.softuni.bg/Contests/Practice/Index/517#5).