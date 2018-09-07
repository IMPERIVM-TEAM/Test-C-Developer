# Test C++ Developer

Требуется реализовать хранение информации о физических и юридических лицах. Данные следующие.
Для физлиц:
```
{
  id : <GUID>,
  ИНН : <строка>,
  имя, отчество (опционально), фамилия : <строка>,
  адрес : <строка>
}
```
Для юрлиц:
```
{
  id : <GUID>,
  ИНН : <строка>,
  полное наименование, сокращенное наименование : <строка>,
  юридический адрес, фактический адрес : <строка>,
  банковские реквизиты : <соответствующая структура>,
  контактное лицо : <ссылка на физлицо>
}
```

Все данные должны храниться в одном файле. Требуется реализовать:
* Запись в файл
* Чтение из файла
* Выборку по `id`
* Выборку по ИНН

При решении исходить из следующих условий:

* Количество записей может быть большим:
  * Данные гарантированно помещаются в файл на диске;
  * Данные не помещаются в оперативную память.
* Вспомогательные файлы использовать можно, но данные полностью должны содержаться в одном 
  основном, т.е. если удалить все вспомогательные, они могут быть полностью восстановлены
  из данных основного файла.
* Обращения к данным могут приходить из разных потоков (threads) одновременно. Решение должно
  быть threadsafe.
  
* Базы данных использовать нельзя.
* Сторонние библиотеки нежелательны, в то же время нежелательно придумывать велосипеды для того,
  что уже есть в стандартной библиотеке C++.
* Решение должно собираться компилятором C++ из GCC с ключом `-std=c++11` (`g++ -std=c++11 -O2 ...`).

## Задача + (требует значительно больше времени)

На тех же данных реализовать поисковую выборку по подстроке в имени/названии и/или адресах,
с сортировкой по имени/названию и разбивкой на страницы (т.е. получаем N записей, начиная 
с некоторого номера K).
