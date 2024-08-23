##### equals
`public boolean equals(Object obj)` - сравнивает текущий объект с другим объектом. По умолчанию проверяет, ссылаются ли оба объекта на одну и ту же область памяти.
##### правила переопределения
- __Самосравнение__:  `if (this == obj) return true;`
- __Проверка типа и на null__: 
- только такой же класс: `if (obj == null || getClass() != obj.getClass()) return false;`
- может быть класс наследник: `if (!(obj instanceof YourClass)) return false`;
- __Приведение типа__: `YourClass other = (YourClass) obj;`
- __Сравнение полей: return__ `Objects.equals(this.field, other.field);`

##### hashCode
**`public int hashCode()`** - возвращает хеш-код объекта используется в хеш-таблицах, таких как `HashMap` и `HashSet`
- Если его __не определить вернет хешкод основываясь на области в памяти__, для работы в коллекциях __нужно чтобы определял по полям__
##### пример переопределения 
`public class Person {
    `private String name;
    `private int age;``
    
    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }
`}