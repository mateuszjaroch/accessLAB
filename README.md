# accessLAB

Aplikacja webowa wspierająca ewidencję i zarządzanie sprzętem IT – połączenie systemów DCIM i ITAM w lekkiej, inżynierskiej formie.

## Opis
accessLAB umożliwia prowadzenie rejestru urządzeń laboratoryjnych oraz magazynowych. 
Projekt łączy koncepcje DCIM (zarządzanie infrastrukturą w szafach rack) i ITAM (zarządzanie aktywami IT).

## Funkcjonalności
Aplikacja accessLAB umożliwia prowadzenie ewidencji sprzętu laboratoryjnego i magazynowego w środowisku inżynierskim.
Stanowi połączenie systemów ITAM (IT Asset Management) oraz DCIM (Data Center Infrastructure Management), ale w uproszczonej, wewnętrznej formie, skierowanej do zespołów technicznych.

Zakres funkcjonalny:
- prowadzenie bazy urządzeń (chassis, karty, ONT, NT, routery, itp.)
- rozróżnienie środowisk:
  - LAB – urządzenia o statusie online
  - MAGAZYN – urządzenia o statusie offline
- definiowanie słowników systemowych (region, site, location, rack, status, role, manufacturer, asset type, product)
- możliwość przypisywania urządzeń do pracowników lub projektów (rola: in use / free)
- historia wypożyczeń i konfiguracji w rackach
- planowanie i odwzorowanie fizycznych setupów w rackach (chassis, półki, karty)
- zarządzanie dostępami (konto użytkownika, rola, dane kontaktowe, dane logowania do urządzenia)
- prosty system stanów (np. active, faulty, reserved, free)
- rozróżnienie lokalizacji logicznej i fizycznej (np. site → lab → rack → shelf)

Kierunek rozwoju:
- integracja z systemami zewnętrznymi (NetBox, Snipe-IT)
- dodanie API umożliwiającego automatyzację wpisów przez skrypty (FastAPI)
- integracja z Dockerem (dla szybkiego uruchamiania środowiska testowego)

## Struktura projektu
accessLAB/
 ├── front/              # Warstwa prezentacji (Flask + Jinja)
 │    ├── templates/
 │    ├── static/
 │    └── views/
 │
 ├── app/                # Warstwa aplikacji (logika biznesowa)
 │    ├── services/
 │    ├── utils/
 │    └── core/
 │
 ├── api/                # Warstwa API (FastAPI – endpointy)
 │    ├── routers/
 │    ├── schemas/
 │    └── main.py
 │
 ├── db/                 # Warstwa danych (baza, modele)
 │    ├── models/
 │    ├── migrations/
 │    └── database.py
 │
 ├── deploy/             # Warstwa środowiska i wdrożenia
 │    ├── docker-compose.yml
 │    ├── Dockerfile
 │    ├── .env
 │    └── config/
 │
 ├── tests/              # Testy jednostkowe i integracyjne
 │
 ├── README.md
 ├── LICENSE
 └── .gitignore



## Uruchomienie (Docker)
```bash
docker-compose up

