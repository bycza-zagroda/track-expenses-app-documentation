
# Projekt *Track Expenses App*

- - -

### Osobowa struktura organizacyjna projektu.
   - Owner [ _Przemek Bykowski_ ]
   - Management  
Iwona `Iwona007`, Mirek `mirekgab`
   - Liders
     - Back-end  
Dawid `dawciobiel` Bielecki, Piotr `odzio33`, Krzysztof `Krisu`, Kacper `poneciak57`
     - Front-end  
Paweł `purbanski-deftcode`, `Iselii`
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

**Link do dokumentacji**
<https://www.hostinger.com/tutorials/mysql/how-create-mysql-user-and-grant-permissions-command-line>

you need to precede the mysql command with sudo to invoke it with the privileges of the root Ubuntu user in order to gain access to the root MySQL user:

```bash
sudo mysql
```

Note: If your root MySQL user is configured to authenticate with a password, you will need to use a different command to access the MySQL shell. The following will run your MySQL client with regular user privileges, and you will only gain administrator privileges within the database by authenticating with the correct password:

```bash
mysql -u root -p
```

```bash
mysql> CREATE DATABASE trackexpensesapp;
mysql> CREATE USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password_MySQL2023';
mysql> GRANT ALL PRIVILEGES ON trackexpensesapp.* TO 'root'@'localhost';
mysql> FLUSH PRIVILEGES;
mysql> exit
```

### Konfiguracja baza danych zainstalowana pod Docker-em
```bash
docker pull mysql

docker run --name track-expenses-database -e MYSQL_ROOT_PASSWORD=password -p 3308:3306 -d mysql

# Połączenie z kontenerem:
   docker exec -it track-expenses-database mysql -u root
# lub z zapytaniem o hasło
   docker exec -it track-expenses-database mysql -u root -p

# Tworzenie user-a:
create user 'root'@'172.17.0.1' identified with mysql_native_password by 'password_MySQL2023';

# Nadawanie uprawnień:
grant all on *.* to 'root'@'172.17.0.1';
```

Remember your password for user 'root' is 'password_MySQL2023' and you have to set it in proper files in project.

- - -
