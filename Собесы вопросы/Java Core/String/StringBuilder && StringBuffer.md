- `String` _иммутабельны_, а значит, что _при изменении_ строки мы _создаем новую_, частые операции со `String` могут сильно забить память

- `StringBuilder` _решает эту проблему_, он мутабелен 
###### Использование  `StringBuilder` в цикле 
```java 
        StringBuilder sb = new StringBuilder();
        // Цикл добавляет строки
        for (int i = 1; i <= 5; i++) {
            sb.append("Item ").append(i).append("\n");
        }
        // Преобразуем StringBuilder в String и выводим результат
        String result = sb.toString();
        System.out.println(result);
}```

- ` StringBuffer` - В отличие от `StringBuilder`, __потокобезопасен__ 