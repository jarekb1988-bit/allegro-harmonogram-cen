# Podmiana_cen_dni_tygodnia

## Cel i funkcje

Prywatna aplikacja sprzedawcy do planowania cen „Kup teraz” w PLN na własnym koncie Allegro.pl. Właściciel wpisuje numer oferty, wybiera dni tygodnia, godzinę według czasu polskiego i cenę docelową. Panel pokazuje podsumowanie przed zapisaniem reguły. O wyznaczonej porze aplikacja sprawdza aktualną cenę. Jeśli wymaga zmiany, wysyła polecenie dla wskazanej oferty. Historia zawiera numer oferty, termin, cenę przed zmianą, cenę docelową oraz wynik.

## Połączenie z Allegro

Właściciel rozpoczyna OAuth Device Flow w prywatnym panelu. Otwiera stronę Allegro i zatwierdza dostęp dla swojego konta. Serwer odbiera tokeny, a następnie odnawia je przy użyciu refresh tokena.

## Dane i uprawnienia

| Uprawnienie | Funkcja | Operacja |
|---|---|---|
| `allegro:api:sale:offers:read` | Sprawdzenie formatu oferty, waluty i bieżącej ceny | Odczyt pojedynczej własnej oferty przez `GET /sale/product-offers/{offerId}` przed zaplanowaną zmianą oraz w razie potrzeby sprawdzenie wyniku. |
| `allegro:api:sale:offers:write` | Ustawienie ceny wskazanej przez sprzedawcę | Wysłanie kwoty w PLN dla jednej oferty przez `PUT /offers/{offerId}/change-price-commands/{commandId}`. |

## Dostęp i bezpieczeństwo

Panel wymaga hasła i nasłuchuje na interfejsie lokalnym. Przy instalacji na Ubuntu właściciel korzysta z tunelu SSH. Harmonogram i historia są przechowywane w lokalnej bazie SQLite. Sekret aplikacji, tokeny OAuth i skrót hasła panelu są przechowywane w osobnych plikach z ograniczonym dostępem. Właściciel potwierdza dostęp na stronie Allegro.

## Kontakt w sprawach weryfikacji i działania aplikacji

E-mail opiekuna aplikacji: **sales@vagtech24.pl**
