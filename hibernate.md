---
title: Hibernate
layout: default
---

## Instalacja zależności 
Po stworzeniu projektu przez Mavena, należy dodać zależność Hibernate oraz sterownik np. PostgreSQL do pliku `pom.xml`:
```xml
<dependencies>
    <dependency>
        <groupId>org.postgresql</groupId>
        <artifactId>postgresql</artifactId>
        <version>42.7.4</version>
    </dependency>

    <dependency>
        <groupId>org.hibernate.orm</groupId>
        <artifactId>hibernate-core</artifactId>
        <version>7.0.0.Beta4</version>
    </dependency>
</dependencies>
```