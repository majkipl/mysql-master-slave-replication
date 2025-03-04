## Opis

Fundament pod mechanizm replikacji Master-Slave w MySQL przy użyciu Docker i Docker Compose.

## Wymagania

- Docker
- Docker Compose

## Struktura projektu

- `docker-compose.yaml`: Plik konfiguracji Docker Compose.
- `docker/`: Katalog zawierający pliki Dockerfile i konfiguracje MySQL.
    - `Dockerfile_Mysql_Master`: Dockerfile dla kontenera master MySQL.
    - `Dockerfile_Mysql_Slave1`: Dockerfile dla pierwszego kontenera slave MySQL.
    - `Dockerfile_Mysql_Slave2`: Dockerfile dla drugiego kontenera slave MySQL.
    - `Dockerfile_PhpMyAdmin`: Dockerfile dla kontenerów PhpMyAdmin.
    - `mysql/conf/`: Katalog zawierający pliki konfiguracyjne MySQL.
        - `master.cnf`: Konfiguracja dla serwera master.
        - `slave_1.cnf`: Konfiguracja dla pierwszego serwera slave.
        - `slave_2.cnf`: Konfiguracja dla drugiego serwera slave.
    - `mysql/sql/`: Katalog zawierający skrypty SQL.
        - `replication_user.sql`: Skrypt tworzący użytkownika replikacji.
        - `replication_slaves.sql`: Skrypt konfigurujący replikację na serwerach slave.
- `.env`: Plik konfiguracyjny z zmiennymi środowiskowymi.

## Konfiguracja

1. Skopiuj plik `.env.example` do `.env` i dostosuj zmienne środowiskowe według potrzeb.
2. Opcjonalnie aby zbudować obrazy bez użycia pamięci podręcznej:
   ```sh
   docker-compose build --no-cache
   ```
2. Uruchom Docker Compose:
   ```sh
   docker-compose up -d