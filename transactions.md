---
title: Transactions
layout: default
---

## Informacje 

Domyślnie, `connection` wykonujje każde zapytanie od razu, po kolei. W celu stworzenia transakcji należy zmienić tę domyślną opcję. Przykładowo:
```java 
conn.setAutoCommit(false)
try {
    statement.executeUpdate("DELETE FROM students WHERE first_name='Dominik'")
    statement.executeUpdate("DELETE FROM university WHERE course_id = 1")
    conn.comit();
} catch (SQLException e) {
    conn.rollback()
}
conn.setAutoCommit(true)
```
Zamiast wykonywać wiele zapytań do bazy, można je połączyć w jedno:
```java
statement.addBatch(queryA);
statement.addBatch(queryB);
statement.executeBatch();
```
Trzeba uważać, gdyż wiele sterowników różnie obsługuje zapytania batchowe. Gdy jakieś zapytanie w środku, skończy się błędem, pozostałe nadal będą wykonane - takie zachowanie w przypadku transakcji nie jest dobre. Aby to zmienić, podaj parametr w połączeniu:
`jdbc:mysql://localhost:3306/students?continueBatchOnError=false`

