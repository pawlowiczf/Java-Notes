---
title: Spring Core
layout: default
---

## Wstrzykiwanie zależości przez konstruktor
W celu oznaczenia klasy, jako kandydata do wstrzyknięcia, należy oznaczyć go anotacją `@Component`. Przykładowo:
```java
@Component 
public class MercedesMechanic implements Mechanic {
    @Override 
    public String fixCar() {
        return "Fixing Mercedes";
    }
}
```
Następnie, gdy potrzebujemy obiekt tej klasy w innej, tworzymy konstruktor i oznaczamy go anotacją `@Autowired`.
```java
@Autowired 
public DemoController(Mechanic mechanic)
```

## Wstrzykiwanie zależności przez setter