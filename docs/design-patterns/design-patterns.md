# Design patterns
**Wzorzec projektowy** – uniwersalne, sprawdzone w praktyce rozwiązanie często pojawiających się, powtarzalnych problemów projektowych. Pokazuje powiązania i zależności pomiędzy klasami oraz obiektami i ułatwia tworzenie, modyfikację oraz utrzymanie kodu źródłowego. Jest opisem rozwiązania, a nie jego implementacją.

## Wzorce projektowe - przykłady

### Singleton

**Singleton** to kreacyjny wzorzec projektowy gwarantujący istnienie tylko jednego obiektu danego rodzaju. Udostępnia też pojedynczy punkt dostępowy do takiego obiektu z dowolnego miejsca w programie.

**Przykład implementacji kodu działającego w aplikacji jednowątkowej**
```java
public class Singleton {

    private static Singleton instance = null;

    private Singleton() {}

    public static Singleton getInstance() {
        if(instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}

```

**Przykład implementacji kodu działającego w aplikacji wielowątkowej**
```java
public class Singleton {

    private static volatile Singleton instance = null;

    private Singleton() {}

    public static Singleton getInstance() {
        if(instance == null) {
            synchronized (Singleton.class) {
                if(instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}

```

- https://www.javappa.com/kurs-wzorce-projektowe/singleton
- https://refactoring.guru/pl/design-patterns/singleton/java/example

### Builder (Budowniczy)

- https://www.javappa.com/kurs-wzorce-projektowe/builder
- https://refactoring.guru/design-patterns/builder

### Links
- [Refactoring.guru - Design-patterns](https://refactoring.guru/pl/design-patterns)
- [Jinkubator #27 - Wzorce projektowe — Krzysztof Jelski](https://www.youtube.com/watch?v=RADOhncoohY&t=3s)
