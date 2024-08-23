__Низкоуровневый__ API для Java, позволяющий _напрямую выполнять SQL-запросы_ и управлять соединениями с реляционными базами данных

**Производительность**: Требует ручного управления соединениями и ресурсами, что может усложнить код и повлиять на производительность.

_Репозиторий_ при помощи `JDBC`, использование `try with resources` 
```java
public class EmployeeRepository {
    private DataSource dataSource;
    
    public EmployeeRepository(DataSource dataSource) {
        this.dataSource = dataSource;
    }

    public void save(Employee employee) {
        String sql = "INSERT INTO employees (name) VALUES (?)";
        try (Connection connection = dataSource.getConnection();
             PreparedStatement statement = connection.prepareStatement(sql)) {
            statement.setString(1, employee.getName());
            statement.executeUpdate();
        } catch (SQLException e) {
            throw new RuntimeException(e);
        }
    }

    public Employee findById(Long id) {
        String sql = "SELECT * FROM employees WHERE id = ?";
        try (Connection connection = dataSource.getConnection();
             PreparedStatement statement = connection.prepareStatement(sql)) {
            statement.setLong(1, id);
            try (ResultSet resultSet = statement.executeQuery()) {
                if (resultSet.next()) {
                    Employee employee = new Employee();
                    employee.setId(resultSet.getLong("id"));
                    employee.setName(resultSet.getString("name"));
                    return employee;
                }
            }
        } catch (SQLException e) {
            throw new RuntimeException(e);
        }
        return null;
    }
}

```