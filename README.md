# TimeSeriesForecasting | Применение методов авторегрессии в задачах прогнозирования временных рядов
Цель данной работы — рассмотреть применение методов авторегрессии в задачах прогнозирования временных рядов и рассмотреть два инструмента для прогнозирования: arima и fbprophet. 
Из поставленной цели вытекают следующие задачи: 
-	рассмотреть особенности задач прогнозирования временных рядов, его цели и задачи; 
-	рассмотреть метод авторегрессии; 
-	описать необходимые формулы и понятия; 
-	рассмотреть модели arima и fbprophet;
### ARIMA
Наиболее распространенной авторегрессионной моделью прогнозирования временных рядов является модель авторегрессионного интегрированного скользящего среднего — ARIMA. Эта модель, разработанная Боксом и Дженкинсом в 1976 году — проверенный, признанный многими экспертами метод, использующийся на протяжении многих лет.  

ARIMA — это класс моделей прогнозирования временных рядов, а название является аббревиатурой от AutoRegressive Integrated Moving 
Average. Основой ARIMA является математическая модель, которая представляет значения временного ряда, используя его прошлые значения. Эта модель основана на двух основных характеристиках: прошлые ценности и ошибки. Общий вид модели ARIMA для стационарного временного ряда задается формулой:   
![image](https://user-images.githubusercontent.com/99638036/227561554-2a2a22ff-08be-4b64-b882-5bd6b222f7ab.png)  

Для завершения описания модели ARIMA, стоит поговорить о ее преимуществах и недостатках.  

В качестве главного преимущества можно выделить то, что модель имеет четкое математическое обоснование. Это делает ее одной из наиболее научно обоснованных моделей из всего множества моделей прогнозирования тенденций во временных рядах.  

Еще одним преимуществом является формализованная и наиболее подробно разработанная методика, следуя которой можно подобрать модель, наиболее подходящую к каждому конкретному временному ряду. Формальная процедура проверки модели на адекватность достаточно проста, а разработанные методики по автоматическому подбору наилучшей ARIMA и вовсе значительно облегчает работу прогнозиста.  

Кроме того, точечные и интервальные прогнозы следуют из самой модели и не требуют отдельного оценивания.  

Один из явных недостатков моделей заключается в требовании к рядам данных: для построения адекватной модели ARIMA требуется не менее 40 наблюдений, что на практике не всегда возможно.
Вторым серьезным недостатком является неадаптивность моделей авторегрессии: при получении новых данных модель нужно периодически переоценивать, а иногда — переидентифицировать.
Третий недостаток заключается в том, что построение удовлетворительной модели ARIMA требует больших затрат ресурсов и времени. Само же построение модели требует большого опыта со стороны прогнозиста.
### FbProphet
Помимо ARIMA и некоторых других моделей, таких как экспоненциальное сглаживание, в кольце прогнозирования появились новые претенденты, из-за увеличения интереса в области науки о данных т. д., наблюдаемого в последние годы.  
Одним из этих новых претендентов является Prophet, модель временных рядов, разработанная мировой корпорацией Facebook. Компания использует эту модель в своих процессах прогнозирования. Также стоит сказать, что Prophet выпущена для общественности бесплатно, поскольку это один из проектов с открытым исходным кодом.   

Prophet — это процедура прогнозирования данных временных рядов на основе аддитивной модели, в которой нелинейные тренды соответствуют годовой, еженедельной и ежедневной сезонности, а также праздничным эффектам. Он лучше всего работает с временными рядами, которые имеют сильные сезонные эффекты и несколько сезонов исторических данных. Prophet устойчив к отсутствующим данным и сдвигам в тренде и обычно хорошо справляется с выбросами. Данная модель состоит из четырех компонентов и описывается формулой для расчета мультипликативной модели.  

Prophet не требует больших предварительных знаний или опыта прогнозирования данных временных рядов, поскольку он автоматически находит сезонные тренды по данным и предлагает набор «простых для понимания» параметров. Это позволяет людям, не связанным со статистикой и анализом данных, использовать данную модель и получать достаточно хорошие результаты.   

После рассмотрения основных определений и параметров модели Prophet стоит поговорить о ее преимуществах и недостатках.  

Prophet специально разработан для прогнозирования бизнес-временных рядов. Он дает очень хорошие результаты для данных о запасах, но он может эффектно потерпеть неудачу с наборами данных временных рядов из других областей. В частности, это справедливо для временных рядов, где понятие календарной даты неприменимо и мы не можем изучить какие-либо сезонные закономерности.   

Преимущество Prophet заключается в том, что он требует меньшей настройки гиперпараметров, поскольку он специально разработан для обнаружения закономерностей в бизнес-временных рядах. Одно ключевое различие между ARIMA и Prophet заключается в том, что модель Prophet учитывает «точки изменения» или конкретные сдвиги тренда во временном ряду. Хотя технически это возможно сделать с помощью ARIMA в R, для этого требуется использовать отдельный пакет под названием AEDForecasting.

Далее на примере наборов данных рассмотрим практическое применение данных двух моделей. Для наиболее полного сравнения мы возьмем сезонный и несезонный временной ряд. Это поможет нам увидеть, насколько хороши ARIMA и Prophet для разных наборов данных. 

## Практическая часть
Для того, чтобы показать отличия ARIMA и FBPROPHET на практике будем использовать два датасета — сезонный и несезонный. Рассматривая данные виды наборов данных, мы сможем с разных сторон посмотреть на модели и определить, какая из моделей лучшим образом работает с сезонными и несезонными данными.     

В качестве сезонных данных мы будем использовать данные международного аэропорта Сан-Франциско о ежемесячной статистике пассажиропотока по авиакомпаниям. Рассматривая несезонные данные, будем использовать информацию о числе зарегистрированных родившихся в Российской Федерации с 2008 по 2016 год.  

Прогнозирование временного ряда в данной курсовой работе будет выполняться в RStudio — свободной среде разработки программного обеспечения с открытым исходным кодом для языка программирования R, который предназначен для статистической обработки данных и работы с графикой.  

Начнем рассматривать сезонные данные. Для этого импортируем файл Air_Traffic_Passenger_Statistics.csv в рабочую область RStudio. Импортированный набор данных представлен на Рисунке


