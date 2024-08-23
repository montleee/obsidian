ORM - набор инструментов, который позволяет работать с базами данных в терминах объектов и их свойств, а не SQL-запросов и таблиц. __Преобразует данные между объектно-ориентированными языками программирования и реляционными базами данных.__

**Hibernate** - _реализация JPA_ и популярный _фреймворк ORM_ для Java.

**Основные особенности**
- `Маппинг объектов: `Автоматически преобразует Java-объекты в реляционные данные и обратно.
- `Запросы:` Поддерживает HQL (Hibernate Query Language) для запросов к базе данных
- `Кэширование:`Включает механизмы кэширования для повышения производительности.
- `Транзакции:` Управляет транзакциями и обеспечивает целостность данных.
##### Пример репозитория с JPA и Hibernate
```java
public class EmployeeRepository {

    private EntityManagerFactory entityManagerFactory;
    private EntityManager entityManager;

    public EmployeeRepository() {
        entityManagerFactory = Persistence.createEntityManagerFactory("your-persistence-unit");
        entityManager = entityManagerFactory.createEntityManager();
    }

    public void save(Employee employee) {
        EntityTransaction transaction = entityManager.getTransaction();
        try {
            transaction.begin();
            entityManager.persist(employee);
            transaction.commit();
        } catch (RuntimeException e) {
            if (transaction.isActive()) {
                transaction.rollback();
            }
            throw e;
        }
    }
}```