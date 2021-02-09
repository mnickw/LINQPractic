# Практики «Median & Bigrams», «Чтение файла» и «Статистика»
Репозиторий содержит решения [этой](https://ulearn.me/course/basicprogramming2/Praktika_Median_Bigrams__aa32b282-f8b0-47e2-a16b-510f566f36e5), [этой](https://ulearn.me/course/basicprogramming2/Praktika_Chtenie_fayla__0217848c-5227-415f-a9d2-4c7e41111601) и [этой](https://ulearn.me/course/basicprogramming2/Praktika_Statistika__5181e761-87e7-4914-a963-6fe78c5c7fbc) задачи с ulearn.me.
Задачи прошли код-ревью у преподавателя (баллы: 50/50, 50/50, 100/100). Все решения курса на максимальный балл также выложены в других репозиториях.
Ветка unsolved содержит изначальный проект.

Конечное приложение - парсинг и анализ данных, поступающих через входящие текстовые файлы.

## Практика «Median & Bigrams»

В файле ExtensionsTask реализуйте два метода расширения: для вычисления медианы и для вычисления списка биграмм.

Эти методы пригодятся в будущем. Вы сможете их использовать на ряду и в перемешку с остальными методами LINQ.

Есть важное замечание по деталям реализации.

Создавая методы, работающие с  `IEnumerable`  стоит придерживаться следующих рекомендаций:

1.  Если это возможно, не перечисляйте входной IEnumerable до конца. Потому что IEnumerable может теоретически быть бесконечным.
2.  Не перечисляйте больше элементов, чем нужно для работы IEnumerable. Возможно, при перечислении лишнего элемента случится ошибка или другой нежелательный побочный эффект.
3.  Не полагайтесь на то, что  `IEnumerable`  можно будет перечислить дважды. Этого никто не гарантирует. Кстати, некоторые IDE, автоматически находят нарушение этого пункта. Например, подобные предупреждения умеют показывать JetBrains Rider и Visual Studio с установленным Resharper.

## Практика «Чтение файла»

В этой серии задач вам нужно будет проанализировать статистику посещения слайдов этого курса студентами.

Исходные данные содержатся в двух файлах:

1.  slide.txt содержит информацию про каждый из слайдов — идентификатор, тип слайда (теория, задача или тест), и тема соответствующей недели. Пример файла slides.txt:
    
    ```
    SlideId;SlideType;UnitTitle
    0;theory;Первое знакомство с C#
    1;quiz;Первое знакомство с C#
    2;theory;Первое знакомство с C#
    3;exercise;Первое знакомство с C#
    ```
    
2.  visits.txt содержит по одной записи на первое посещение слайда каждым пользователем. Запись состоит из идентификатора пользователя, идентификатора слайда, даты и времени посещения этим пользователем этого слайда. Пример файла visits.txt:
    
    ```
    UserId;SlideId;Date;Time
    0;5;2014-09-03;12:20:28
    1;6;2014-09-03;12:25:09
    1;4;2014-09-03;12:25:24
    ```
    

В этой задаче в классе ParsingTask нужно реализовать методы чтения этих файлов.

Не используйте циклы в решении. Вместо этого используйте LINQ.

Обратите внимание, что в разных методах предлагается реализовать разную реакцию на некорректные строки файлов: в одном случае — игнорировать их, а в другом — выбрасывать исключение на первой же ошибочной строке. Это сделано исключительно в учебных целях — в реальных проектах стоит, конечно, придерживаться какой-то одной выбранной стратегии.

## Практика «Статистика»
В файле StatisticsTask реализуйте метод GetMedianTimePerSlide. Он должен работать так.

Обозначим T(U, S) время между посещением пользователем U слайда S и ближайшим следующим посещением тем же пользователем U какого-то другого слайда S2 != S.

T(U, S) можно считать примерной оценкой того, сколько времени пользователь U провел на слайде S.

Метод должен для указанного типа слайда, считать медиану значений T(U, S) по всем пользователям и всем слайдам этого типа.

Нужно игнорировать значения меньшие 1 минуты и большие 2 часов при расчете медианы.

Гарантируется, что в тестах и реальных данных отсутствуют записи, когда определенный пользователь заходит на один и тот же слайд более одного раза.

Время нужно возвращать в минутах.

Воспользуйтесь реализованными ранее методами Bigrams и Median.
