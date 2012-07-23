# Generator

Šablona (jednoduché i pravidelné) faktury

<table>
<tr><th>Položka</th><th>Popis</th></tr>

<tr><td>id</td><td>identifikátor šablony</td></tr>

<tr><td>name</td><td>pojmenování šablony</td></tr>
<tr><td>recurring</td><td>true/false jedná se o pravidelnou nebo normální šablonu</td></tr>
<tr><td>proforma</td><td>příznak proformy - true/false</td></tr>

<tr><td>start_date</td><td>počáteční datum pro pravidelnou šablonu</td></tr>
<tr><td>end_date</td><td>koncové datum pro pravidelnou šablonu</td></tr>
<tr><td>months_period</td><td>počet měsíců do dalšího vystavení faktury ze šablony (pravidelná šablona)</td></tr>
<tr><td>next_occurrence_on</td><td>datum dalšího vystavení faktury z pravidelné šablony</td></tr>
<tr><td>due</td><td>počet dní, než bude po splatnosti (nepovinné - doplní se z účtu)</td></tr>

<tr><td>send_email</td><td>true/false posílat pravidelnou šablonu emailem</td></tr>
<tr><td>subject_id</td><td>ID kontaktu (povinné)</td></tr>

<tr><td>bank_account</td><td>číslo bankovního účtu (nepovinné - doplní se z účtu)</td></tr>
<tr><td>iban</td><td>IBAN</td></tr>
<tr><td>swift_bic</td><td>BIC (pro SWIFT platby)</td></tr>

<tr><td>payment_method</td><td>bank (bankovní převod) / cash (hotově) / cod (dobírka)</td></tr>
<tr><td>currency</td><td>kód měny (nepovinné - doplní se z účtu, 3 znaky)</td></tr>
<tr><td>exchange_rate</td><td>kurz (nepovinné)</td></tr>
<tr><td>language</td><td>jazyk vystavené faktury</td></tr>
<tr><td>transferred_tax_liability</td><td>přenesená daňová povinnost true/false</td></tr>

<tr><td>subtotal</td><td>součet (bez DPH)</td></tr>
<tr><td>native_subtotal</td><td>součet v měně účtu</td></tr>
<tr><td>total</td><td>celkový součet (včetně DPH)</td></tr>
<tr><td>native_total</td><td>celkový součet v měně účtu</td></tr>

<tr><td>html_url</td><td>HTML adresa šablony</td></tr>
<tr><td>url</td><td>API adresa šablony</td></tr>
<tr><td>subject_url</td><td>API adresa kontaktu</td></tr>
<tr><td>udated_at</td><td>datum poslední aktualizace šablony</td></tr>
</table>

## Seznam šablon

- `GET /generators.json` - seznam všech šablon

- `GET /generators/recurring.json` - seznam pravidelných šablon

- `GET /generators/template.json` - seznam jednoduchých šablon

Faktury lze filtrovat podle parametrů `subject_id` a `since`. 

Při použití `?subject_id=4` budou vráceny šablnoy náležící danému kontaktu, při jeho neexistenci dostanete odpověď ze serveru `404 Not Found`.

Při použití `?since=2012-05-20T15:00:00+01:00` budou vráceny šablony vytvořené po zadaném datu, při zadání nesprávného formátu data a času server vrátí odpověď `400 Bad Request`.

Filtry je možné libovolně kombinovat.

```json
[
  {
    "id": 5,
    "name": "\u0160kolen\u00ed",
    "recurring": false,
    "proforma": false,
    "start_date": null,
    "end_date": null,
    "months_period": null,
    "next_occurrence_on": null,
    "due": 10,
    "send_email": false,
    "subject_id": null,
    "bank_account": null,
    "iban": null,
    "swift_bic": null,
    "currency": "CZK",
    "payment_method": "bank",
    "exchange_rate": "1.0",
    "language": null,
    "subtotal": "28000.0",
    "total": "33600.0",
    "native_subtotal": "28000.0",
    "native_total": "33600.0",
    "lines": [
      {
        "name": "\u0160kolen\u00ed person\u00e1lu",
        "quantity": "4.0",
        "unit_name": "lidi",
        "unit_price": "7000.0",
        "vat_rate": 20,"with_vat":false
      }
    ],
    "html_url": "https://subdomena.fakturoid.cz/generators/5",
    "url": "https://subdomena.fakturoid.cz/api/v1/generators/5.json",
    "subject_url": null,
    "updated_at": "2012-05-13T12:11:38+02:00"
  },
  {
    "id": 4,
    "name": "\u0160kolen\u00ed",
    "recurring": true,
    "proforma": false,
    "start_date": "2011-07-13",
    "end_date": null,
    "months_period": 1,
    "next_occurrence_on": "2012-06-13",
    "due": 10,
    "send_email": false,
    "subject_id": 4,
    "bank_account": null,
    "iban": null,
    "swift_bic": null,
    "currency": "CZK",
    "payment_method": "bank",
    "exchange_rate": "1.0",
    "language": null,
    "subtotal": "20000.0",
    "total": "24000.0",
    "native_subtotal": "20000.0",
    "native_total": "24000.0",
    "lines": [
      {
        "name": "\u0160kolen\u00ed",
        "quantity": "1.0",
        "unit_name": "",
        "unit_price": "20000.0",
        "vat_rate": 20,
        "with_vat": false
      }
    ],
    "html_url": "https://subdomena.fakturoid.cz/generators/4",
    "url": "https://subdomena.fakturoid.cz/api/v1/generators/4.json",
    "subject_url": "https://subdomena.fakturoid.cz/api/v1/subjects/4.json",
    "updated_at": "2012-05-13T12:11:37+02:00"
  }
]
```

## Detail šablony

- `GET /generators/#{id}.json`

```json
{
  "id": 4,
  "name": "\u0160kolen\u00ed",
  "recurring": true,
  "proforma": false,
  "start_date": "2011-07-13",
  "end_date": null,
  "months_period": 1,
  "next_occurrence_on": "2012-06-13",
  "due": 10,
  "send_email": false,
  "subject_id": 4,
  "bank_account": null,
  "iban": null,
  "swift_bic": null,
  "currency": "CZK",
  "payment_method": "bank",
  "exchange_rate": "1.0",
  "language": null,
  "subtotal": "20000.0",
  "total": "24000.0",
  "native_subtotal": "20000.0",
  "native_total": "24000.0",
  "lines": [
    {
      "name": "\u0160kolen\u00ed",
      "quantity": "1.0",
      "unit_name": "",
      "unit_price": "20000.0",
      "vat_rate": 20,
      "with_vat": false
    }
  ],
  "html_url": "https://subdomena.fakturoid.cz/generators/4",
  "url": "https://subdomena.fakturoid.cz/api/v1/generators/4.json",
  "subject_url": "https://subdomena.fakturoid.cz/api/v1/subjects/4.json",
  "updated_at": "2012-05-13T12:11:37+02:00"
}
```

## Nová šablona

- `POST /generators.json`

```json
{
  "name": "Podpora",
  "recurring": false,
  "currency": "CZK",
  "payment_method": "bank",
  "due": 10,
  "lines": [
    {
      "name": "Hard work",
      "quantity": "1.0",
      "unit_name": "h",
      "unit_price": "40000",
      "vat_rate": "20"
    }
  ]
}
```

Po úspěšném vytvoření šablony dostanete ze serveru odpověď `201 Created`, hlavička `location` bude nastavena na adresu nově vytvořené šablony. Spolu s tím bude navrácena právě vytvořená šablona.

Pokud budou odeslána nevalidní data, dostanete ze serveru odpověď `422 Unprocessable Entity` a JSON se seznamem chyb v odeslaných datech.

## Úprava šablony

- `PUT /generators/#{id}.json`

```json
{
  "name": "Hosting"
}
```

Odpověď serveru na tento příkaz je `200 OK` a JSON s upravenou fakturou. 

Při odeslání nevalidních dat dostanete ze serveru odpověď `422 Unprocessable Entity` a JSON se seznamem chyb v odeslaných datech.

## Smazání šablony

- `DELETE /generators/#{id}.json`

Po smazání šablony server vrátní odpověď `204 No Content`.
