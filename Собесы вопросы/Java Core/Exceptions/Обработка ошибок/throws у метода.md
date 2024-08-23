**`throws`** - _Ключевое слово_, используемое для объявления, что _метод может выбросить исключение_. Метод, который вызывает метод с **`throws`** должен _обработать_ его при помощи try catch _либо прокинуть наверх_

###### Пример прокидывания эксепшена  
```java
public void readFile(String fileName) throws IOException {
    FileReader fileReader = new FileReader(fileName);
    BufferedReader bufferedReader = new BufferedReader(fileReader);
    String line = bufferedReader.readLine();
    bufferedReader.close();
}
```
###### Обработка прокинутого эксепшена
```java
public void processFile(String fileName) {
    try {
        readFile(fileName);
    } catch (IOException e) {
        System.out.println("Ошибка при чтении файла: " + e.getMessage());
    }
}
```
