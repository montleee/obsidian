- На один уровень выше JDBC
- __Абстракция над ORM__
- __Спецификация для ORM,__ _упрощает работу с базами данных,_ скрывая SQL-запросы за объектно-ориентированными интерфейсами.

- __Использование JPA без ORM невозможно,__ она задает правила и стандарты для ORM

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