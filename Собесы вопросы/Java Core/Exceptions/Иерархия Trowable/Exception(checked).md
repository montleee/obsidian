`Exception` -Класс для проверяемых исключений, которые должны быть обработаны или объявлены в методе. __Разработчик обязан их обработать __
- **Примеры**:
    - `IOException` — ошибка ввода/вывода
        Его _наследует_:
        - `FileNotFoundException` — файл не найден.
        - `UnknownHostException` - Хост не найден.
        - `InterruptedIOException` - Прерывание ввода/вывода.
    - `SQLException` —  при работе с _DB_.
        Его _наследует_:
        - `SQLIntegrityConstraintViolationException` — нарушение целостности данных.
        - `SQLSyntaxErrorException` — синтаксическая ошибка в SQL-запросе.
	- `ClassNotFoundException`-  класс не найден.
	- `NoSuchMethodException`-  метода не найдет.
