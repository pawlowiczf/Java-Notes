---
title: Spring Core
layout: default
---

## Wstrzykiwanie zależości przez konstruktor
W celu oznaczenia klasy, jako kandydata do wstrzyknięcia, należy oznaczyć go anotacją `@Component`. Przykładowo:
```
@Component 
public class MercedesMechanic implements Mechanic {
    @Override 
    public String fixCar() {
        return "Fixing Mercedes";
    }
}
```
Następnie, gdy potrzebujemy obiekt tej klasy w innej, tworzymy konstruktor i oznaczamy go anotacją `@Autowired`.
```
@Autowired 
public DemoController(Mechanic mechanic)
```

## Wstrzykiwanie zależności przez setter
To samo, ale wstrzykujemy przez settery:
```
@Autowired
void setMechanic(Mechanic mechanic) {
    this.mechanic = mechanic;
}
```

## Problem niejednoznaczności 

### Adnotacja `@Qualifier`
Co jeśli, mamy więcej implementacji danego interfejsu? Którą klasę wstrzyknąć? Możemy być dokładniejsi i napisać:
```
@Autowired
void setCoach(@Qualifier("mercedesMechanic") Mechanic mechanic) {}
```
Podany string to `beanID` - taki sam, jak nazwa klasy, ale z małej litery. 

### Adnotacja `@Primary`
Możemy implementację danego interfejsu oznaczyć adnotacją `Primary` - taka adnotacja może być tyko jedna. Taka klasa będzie domyślnie wstrzykiwana, w przypadku braku jawnego określenia innej. 