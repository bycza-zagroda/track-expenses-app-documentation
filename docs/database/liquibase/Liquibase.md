# Liquibase

**Liquibase** is an open-source database-independent library for tracking, managing and applying database schema changes. It was started in 2006 to allow easier tracking of database changes, especially in an agile software development environment.  
Liquibase is a database migration tool, not a data insertion tool. It is used to manage changes to the database schema, such as creating tables, altering column types, and modifying constraints. 

## Informacje
W projekcie ustaliliśmy, że baza deweloperska będzie zawierała przykładowe dane. Ponieważ używamy Liquibase do 
zarządzania schematem bazy zdecydowaliśmy, że wykorzystamy to narzędzie także do wprowadzania tych danych. Czy jest to zgodne ze sztuką? Czy można użyć Liquibase do wstawiania przykładowych danych w bazie developerskiej tak jak zrobiliśmy to w przypadku tabeli `wallets`?
  
W takim razie nic nie stoi na przeszkodzie, żeby dodać changeset-a z danym.
Myślę, że na czas development-u może to być wygodniejsze niż wrzucanie danych ręcznie do bazy czy pisanie w tym celu 
skryptów.

Obecnie liquibase jest tak skonfigurowany, że każde uruchomienie aplikacji robi drop-a bazy i tworzy ją od początku. 
Będzie to zmienione na późniejszym etapie prac, aby w pełni wykorzystać możliwości tego narzędzia.

Dane dla środowiska testowego są wprowadzane za pomocą skryptów SQL bez Liquibase. Natomiast dla środowiska 
produkcyjnego nie wprowadzamy danych, mamy tam Liquibase, aby zarządzał zmianami w bazie produkcyjnej.

### Links

- [Liquibase](https://www.liquibase.org/)
- [Liquibase - Wikipedia](https://en.wikipedia.org/wiki/Liquibase)
- [Liquibase – zarządzanie zmianami w bazach danych @Przemek Bykowski](https://bykowski.pl/liquibase-zarzadzanie-zmianami-w-bazach-danych/)
- [Liquibase – zarządzanie zmianami w bazach danych @Przemek Bykowski](https://www.youtube.com/watch?v=yemZz8FgAgQ)
- [Liquibase – automatyczne zarządzanie schematem bazy danych](https://nullpointerexception.pl/liquibase-automatyczne-zarzadzanie-schematem-bazy-danych/)