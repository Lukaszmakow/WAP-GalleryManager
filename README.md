# Photo Gallery Manager

## Opis

Photo Gallery Manager to aplikacja backendowa udostępniająca REST API do
zarządzania galerią zdjęć. System umożliwia przechowywanie obrazów,
zarządzanie metadanymi, tagowanie oraz analizę trendów (np. popularność
tagów).

## Stack technologiczny

-   Java
-   Spring Boot
-   Spring Web (REST API)
-   Hibernate (JPA)
-   MySQL
-   Maven

## Struktura projektu

    photo-gallery-manager/
    ├── src/
    │   ├── main/
    │   │   ├── java/com/example/gallery/
    │   │   │   ├── controller/      # Endpointy REST
    │   │   │   ├── service/         # Logika biznesowa
    │   │   │   ├── repository/      # Warstwa dostępu do danych (JPA)
    │   │   │   ├── model/           # Encje (Image, Tag, Metadata)
    │   │   │   └── dto/             # Obiekty transferowe
    │   │   └── resources/
    │   │       ├── application.yml  # Konfiguracja aplikacji
    │   │       └── data.sql         # Dane początkowe (opcjonalnie)
    ├── pom.xml                     # Konfiguracja Maven
    └── README.md

## Instalacja i uruchomienie

### 1. Wymagania

-   Java 17+
-   Maven
-   MySQL

### 2. Konfiguracja bazy danych

Utwórz bazę danych w MySQL:

``` sql
CREATE DATABASE gallery_db;
```

Zaktualizuj plik `application.yml`:

    spring:
      datasource:
        url: jdbc:mysql://localhost:3306/gallery_db
        username: root
        password: your_password
      jpa:
        hibernate:
          ddl-auto: update
        show-sql: true

### 3. Budowanie projektu

    mvn clean install

### 4. Uruchomienie aplikacji

    mvn spring-boot:run

### 5. Dostęp do API

Domyślny adres:

    http://localhost:8080/api

## Główne funkcjonalności

-   Upload i zarządzanie zdjęciami
-   Przechowywanie metadanych (np. data, lokalizacja)
-   Tagowanie zdjęć
-   Wyszukiwanie po tagach
-   Analiza trendów (najczęściej używane tagi)

## Przykładowe endpointy

-   `GET /images` -- lista zdjęć
-   `POST /images` -- dodanie zdjęcia
-   `GET /images/{id}` -- szczegóły zdjęcia
-   `DELETE /images/{id}` -- usunięcie zdjęcia
-   `GET /tags/trending` -- popularne tagi
