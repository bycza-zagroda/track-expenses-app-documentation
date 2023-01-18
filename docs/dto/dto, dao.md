# Data Transfer Object (DTO), Data Access Object (DAO)

**Data Transfer Object** – Obiekt transferu danych (DTO, ang. Data transfer object) − w programowaniu obiektowym 
obiekt, który przechowuje tylko pola publiczne, bez metod. Często używany do komunikacji z bazami danych np. w bibliotekach ORM.

W dziedzinie programowania obiekt przesyłania danych (DTO) to obiekt, który przenosi dane między procesami. 
Motywacją do jego użycia jest to, że komunikacja między procesami odbywa się zwykle za pośrednictwem zdalnych 
interfejsów (np. usług sieciowych), gdzie każde wywołanie jest kosztowną operacją. Ponieważ większość kosztów 
każdego połączenia jest związana z czasem podróży w obie strony między klientem a serwerem, jednym ze sposobów 
zmniejszenia liczby połączeń jest użycie obiektu (DTO), który agreguje dane, które zostałyby przesłane przez kilka 
wezwań/żądań, ale jest to obsługiwane tylko przez jedno wezwanie/żądanie.

Różnica między obiektami przesyłania danych a obiektami biznesowymi lub obiektami dostępu do danych polega na tym, że DTO nie zachowuje się inaczej niż przechowywanie, pobieranie, serializacja i deserializacja własnych danych (mutatory, akcesory, parsery i serializatory). Innymi słowy, DTO to proste obiekty, które nie powinny zawierać żadnej logiki biznesowej, ale mogą zawierać mechanizmy serializacji i deserializacji do przesyłania danych przez sieć.

Autora tego wzorce powtarza on, że **celem DTO jest przenoszenie danych w kosztownych połączeniach zdalnych.**


## Should DTOs use inheritance or composition

The "one DTO class" approach is almost certainly bad. It smells like a God Class. Many pundits excoriate DTOs altogether. You could inherit from some base class, but for value objects it's not really sensible. Same for composition. It makes your code more complicated. When debugging the "DocReview" flow, you'd have to look at two, three, or more DTO classes to understand it with either approach. Bleagh! Also, each DTO is typically in a separate semantic domain: "Doc" is not "DocReview". So the apparent "common" elements are not actually common at all. They just share an implementation type; their meanings are quite different.

When the member type is inherently composite, for example if many domains share the concept of an Identifier, you could make that a type for composition into the DTOs for those domains. In your example, you might have

```java
    public class Identifier {
        long id; // should be a 'String', actually
        String name;
    }

    public class Doc {
        private Identifier identifier;
        private String docType;
    }
    
    public class DocReview {
        private Identifier identifier;
        private String status;
        private String comment;
    }
```

The key here is that Identifier is semantically equivalent in both domains, so it makes sense to have it as a common type. Otherwise you wouldn't do that.

Sidebar: "DTO" as a suffix is not good naming, really.

### Links

- [The DTO Pattern (Data Transfer Object)](https://clockworkjava.pl/2020/12/obiekt-domenowy-dto-dao/)
- [Obiekt domenowy, DTO, DAO](https://www.baeldung.com/java-dto-pattern)