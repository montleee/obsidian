**Контекст** в Spring Framework (ApplicationContext) — это основное средство для управления бинами и их жизненным циклом. Он является расширением интерфейса `BeanFactory`, предоставляя дополнительные возможности и функционал. Контекст управляет созданием, конфигурацией и внедрением бинов, а также предоставляет доступ к различным сервисам и функциям Spring.

### Основные типы контекста

1. **`ClassPathXmlApplicationContext`**:
    
    - Загружает контекст из `XML-файла`.
    - Пример:
        `ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
        
2. **`AnnotationConfigApplicationContext`**:
    
    - Используется для конфигурации на основе аннотаций.
        `ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);`
        
##### Дочерние контексты 
В Spring можно создавать дочерние контексты для разделения конфигурации и управления различными частями приложения. Это может быть полезно для:

- **Модульного разделения**: Разделение конфигурации по модулям или частям приложения.
- **Веб-приложений**: Разделение конфигурации между различными частями веб-приложения и основным приложением.
```java
// Создание родительского контекста
ApplicationContext parentContext = new ClassPathXmlApplicationContext("parentContext.xml");

// Создание дочернего контекста
GenericWebApplicationContext childContext = new GenericWebApplicationContext();
childContext.setParent(parentContext);
childContext.refresh();

```


##### Между контекстами можно меняться

Вы можете изменить контекст или его поведение разными способами:

- **Замена конфигурации**: Использование различных конфигурационных классов или XML-файлов для создания разных контекстов.
- **Использование профилей**: С помощью аннотации `@Profile` можно активировать разные конфигурации в зависимости от активного профиля.


```java 
@Configuration
@Profile("dev")
public class DevConfig {
    @Bean
    public MyService myService() {
        return new DevMyService();
    }
}

@Configuration
@Profile("prod")
public class ProdConfig {
    @Bean
    public MyService myService() {
        return new ProdMyService();
    }
}

```

Активировать профиль можно через параметр командной строки или конфигурационный файл
`spring.profiles.active=dev`