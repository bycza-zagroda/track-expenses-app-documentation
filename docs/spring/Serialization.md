# Serialization in Java, Serialization in Spring Boot

**Serializacja** to wbudowany mechanizm zapisywania obiektów, który pozwala na binarny zapis całego drzewa obiektów. Oznacza to tyle, że jeśli mamy obiekt X, który posiada referencję do obiektu Y to serializując X również Y zostanie automatycznie zapisany w strumieniu wyjściowym.

Tak zapisany obiekt możesz później otworzyć przy kolejnym uruchomieniu programu. Jednak serializacja ma więcej zastosowań.

Dzięki temu mechanizmowi można na przykład przesyłać obiekty przez sieć. Obiekt, który stworzyliśmy na jednym komputerze (wewnątrz pamięci jednej wirtualnej maszyny Java) może być zserializowany, przesłany przez sieć i zdeserializowany na drugim komputerze tworząc nową instancję obiektu (wewnątrz pamięci drugiej wirtualnej maszyny Javy). Na obu tych komputerach wirtualna maszyna Javy musi mieć dostęp do skompilowanej wersji klasy.

Zserializaowany obiekt może być również przesłany przez sieć i zdeserializowany na drugim komputerze w przeglądarce WWW — a ta np. odpowiednio wyświetli jego dane. 

### Warunki wymagane do serializacji

Chociaż serializacja dostępna jest automatycznie dla większości obiektów z biblioteki standardowej to jeśli chcesz móc serializować instancje klas, które sam napiszesz musisz spełnić kilka warunków.
Interfejs java.io.Serializable

Jest to tak zwany interfejs znacznikowy, innymi słowy nie zawiera on żadnej metody. Służy on do pokazania wirtualnej 
maszynie, że instancje danej klasy implementującej ten interfejs mogą być serializowane. Musisz implementować ten 
interfejs jeśli chcesz aby twoje klasy były serializowalne. Jeśli będziesz próbował zserializować klasę, która nie 
implementuje tego interfejsu zostanie rzucony wyjątek typu [NotSerializableException](https://docs.oracle.com/en/java/javase/12/docs/api/java.base/java/io/NotSerializableException.html).

### Pole serialVersionUID

Dodatkowo musisz wiedzieć o statycznym polu w klasie o nazwie `serialVersionUID`. Jego pełna definicja wygląda następująco:

```java
private static long serialVersionUID;
```

Pole to ma specyficzne zastosowanie. Mechanizm serializacji używa go do upewnienia się, że deserializowany obiekt „pasuje” do danych zapisanych w strumieniu. Wie o tym na podstawie wartości tego pola. Jeśli w zdeserializowanym obiekcie wartość tego pola jest taka sama jak aktualnej definicji klasy wówczas można bezpiecznie przeprowadzić deserializację.

Kiedy taka sytuacja może wystąpić? Załóżmy, że dzisiaj napiszesz klasę `Human`, zdeserializujesz jej instancję i zapiszesz w pliku na dysku. Po jakimś czasie wprowadzisz zmiany w klasie i będziesz chciał odczytać starą wersję z pliku. W niektórych przypadkach taka operacja nie będzie dozwolona. Właśnie wtedy pole `serialVersionUID` może pomóc w wykryciu takiej sytuacji.

Pole to możesz ustawić samodzielnie, jeśli tego nie zrobisz kompilator wygeneruje tę wartość za Ciebie na podstawie definicji klasy.


## Links

- [Serializable (Java SE 18 & JDK 18)](https://docs.oracle.com/en/java/javase/18/docs/api/java.base/java/io/Serializable.html)
- [Serializacja w języku Java](https://www.samouczekprogramisty.pl/serializacja-w-jezyku-java/)
- [Introduction to Java Serialization | Baeldung](https://www.baeldung.com/java-serialization/)
- [JPA Entities and the Serializable Interface | Baeldung](https://www.baeldung.com/jpa-entities-serializable/)
