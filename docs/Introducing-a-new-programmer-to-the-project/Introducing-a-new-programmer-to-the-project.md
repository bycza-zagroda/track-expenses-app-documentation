
# Projekt *Track Expenses App*

- - -

### Osobowa struktura organizacyjna projektu.
   - Owner [ _Przemek Bykowski_ ]
   - Management  
Iwona `Iwona007`, Mirek `mirekgab`
   - Liders
     - Back-end  
Dawid `dawciobiel` Bielecki, Piotr `odzio33`, Krzysztof `Krisu`
     - Front-end  
Paweł `purbanski-deftcode`
   - Developers
   - Coach, administrative technician
- - -

## Repozytorium projektu

   - <https://github.com/bycza-zagroda>
   - <https://github.com/bycza-zagroda/track-expenses-app-backend>
   - <https://github.com/bycza-zagroda/track-expenses-app-documentation>
   - <https://github.com/bycza-zagroda/track-expenses-app-frontend>

## Dokumentacja

  - <https://github.com/bycza-zagroda/track-expenses-app-documentation>

### Sekcje dokumentacji

  - [Docs]
    - <https://github.com/bycza-zagroda/track-expenses-app-documentation/tree/develop/docs>
  - [GitHub work]
    - <https://github.com/bycza-zagroda/track-expenses-app-documentation/tree/develop/githubwork>
  - [Architecture Decision Record (ADR)]
    - <https://adr.github.io/>
    - <https://github.com/joelparkerhenderson/architecture-decision-record> 
    - <https://github.com/bycza-zagroda/track-expenses-app-documentation/tree/develop/architecture/decisions>

[//]: # (  - [Request for comments - czyli nasz odpowiednik ADR])

[//]: # (     - <https://en.wikipedia.org/wiki/Request_for_Comments>)

[//]: # (     - <https://www.rfc-editor.org/rfc/>)

[//]: # (     - <https://en.wikipedia.org/wiki/Request_for_Comments>)

[//]: # (     - <https://wiki.wireshark.org/RFC.md>)
- - -

## Do której sekcji chcesz dołączyć?

   - Back-end
   - Front-end
   - Fullstack
   - Database
   - [DevOps](https://pl.wikipedia.org/wiki/DevOps)
- - -

## Dodać nowego developera do rozpiski `contributors` na `#os-liders`.

- - -

## Jakie masz doświadczenie z programowaniem?

   - Ile czasu zajmujesz się programowaniem?
   - Ile czasu hobbystycznie, ile zawodowo z Java SE/ Java EE?
   - Czy już znasz w jakimś stopniu Spring Framework / Spring Boot?
   - Czy znasz bazy danych relacyjne, jeżeli tak to jakie?
   - Czy miałeś doświadczenie z JPA najlepiej z Hibernate?

- - -

## Jak pracować z git, github, konwencja commit-ów

<https://github.com/bycza-zagroda/track-expenses-app-documentation/tree/develop/githubwork>

Przed `push-em` konieczne jest:
   - Aktualizacja własnego fork-a z głównym repozytorium back-end-u bycza-zagroda.
   - Aktualizacja swojego lokalnego repozytorium kodu z branch-em `develop` na swoim fork-u.
W ten sposób twoje lokalne repozytorium jest aktualne, a to oznacza, że nie powstaną konflikty ani u Ciebie lokalnie,
     ani na byczej-zagrodzie. 

### Procedura aktualizacji

1. Najpierw aktualizujesz swojego fork-a na GitHub za pomocą GitHub-owego interfejsu WWW.
2. a) Pod IDE (np. IntelliJ IDEA) wybierz z menu _Git -> pull_. Następnie wybierasz branch `develop` oraz dodajesz 
   opcję 
   'rebase'.

   b) W konsoli wpisz `git pull --rebase develop`

## Konfiguracja bazy danych

Nazwa bazy danych: ***trackexpensesapp***  
Użytkownik: ***root***  
Hasło: ***password*** lub ***root***  
Adres IP dla bazy zainstalowanej jako standalone: ***127.0.01***  
Adres IP bazy danych pod docker-em: ***172.17.0.1***  
&nbsp;&nbsp;&nbsp; Może się okazać, że adres bazy danych pod Docker-em będzie minimalnie inny.

### Konfiguracja baza danych zainstalowana jako standalone
```bash
mysql> CREATE DATABASE trackexpensesapp;
mysql> CREATE USER 'root'@'localhost' IDENTIFIED BY "password";
mysql> GRANT ALL PRIVILEGES ON trackexpensesapp.* TO 'root'@'localhost';
mysql> FLUSH PRIVILEGES;
mysql> exit
```

### Konfiguracja baza danych zainstalowana pod Docker-em
```bash
docker pull mysql

docker run --name track-expenses-database -e MYSQL_ROOT_PASSWORD=password -p 3308:3306 -d mysql

# Połączenie z kontenerem:
docker exec -it track-expenses-database mysql -u root -p

# Tworzenie user-a:
create user 'root'@'172.17.0.1' identified by 'root';

# Nadawanie uprawnień:
grant all on *.* to 'root'@'172.17.0.1';
```

- - -
