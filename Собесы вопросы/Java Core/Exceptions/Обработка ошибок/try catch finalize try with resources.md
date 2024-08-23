**`try-catch`** - это конструкция _для обработки исключений в Java_. Она позволяет программе продолжать выполнение после возникновения исключения.

**`finally`** -  _Опциональный_ блок, который _выполняется всегда_, независимо от того, было ли исключение или нет. Обычно используется для освобождения ресурсов.

**`try-with-resources`** -  улучшенная конструкция `try-catch-finally`, _автоматически закрывает ресурсы_ после завершения блока `try`. Для этого ресурсы должны реализовывать интерфейс `AutoCloseable`.

###### Пример `try-with-resources`
```java
try (FileReader reader = new FileReader("file.txt")) {
    // Чтение файла
} catch (IOException e) {
    System.out.println("Ошибка чтения файла: " + e.getMessage());
}```

###### Переопределение метода `close()` из интерфейса `AutoCloseable`
```java
@Override
public void close() {
    try {
        if (fileWriter != null) {
            fileWriter.close(); // Освобождение ресурса
            System.out.println("FileWriter closed.");
        }
    } catch (IOException e) {
        System.out.println("Failed to close FileWriter: " + e.getMessage());
    }
}
```

