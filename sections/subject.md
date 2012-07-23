# Subject

Kontakt

<table>
<tr><th>Položka</th><th>Pouze pro čtení</th><th>Popis</th></tr>

<tr><td>id</td><td>Ano</td><td>identifikátor kontaktu</td></tr>
<tr><td>custom_id</td><td>Ne</td><td>identifikátor kontaktu ve vaší aplikaci</td></tr>

<tr><td>name</td><td>Ne</td><td>jméno firmy kontaktu (jediná povinná položka)</td></tr>
<tr><td>street</td><td>Ne</td><td>ulice</td></tr>
<tr><td>street2</td><td>Ne</td><td>ulice 2</td></tr>
<tr><td>city</td><td>Ne</td><td>město</td></tr>
<tr><td>zip</td><td>Ne</td><td>poštovní směrovací číslo</td></tr>
<tr><td>country</td><td>Ne</td><td>země</td></tr>

<tr><td>registration_no</td><td>Ne</td><td>IČ podnikatele</td></tr>
<tr><td>vat_no</td><td>Ne</td><td>DIČ (plátci DPH)</td></tr>

<tr><td>bank_account</td><td>Ne</td><td>číslo bankovního účtu</td></tr>
<tr><td>iban</td><td>Ne</td><td>IBAN</td></tr>

<tr><td>full_name</td><td>Ne</td><td>jméno kontaktní osoby</td></tr>
<tr><td>email</td><td>Ne</td><td>email pro posílání faktur kontaktu</td></tr>
<tr><td>email_copy</td><td>Ne</td><td>email pro posílání copie faktur kontaktu</td></tr>
<tr><td>phone</td><td>Ne</td><td>telefon</td></tr>
<tr><td>web</td><td>Ne</td><td>web</td></tr>

<tr><td>html_url</td><td>Ano</td><td>HTML adresa kontaktu</td></tr>
<tr><td>url</td><td>Ano</td><td>API adresa kontaktu</td></tr>
<tr><td>updated_at</td><td>Ano</td><td>datum poslední aktualizace kontaktu</td></tr>
</table>

## Seznam kontaktů

- `GET /subjects.json`

Volitelně lze použít parametr `since`.

Při použití `?since=2012-05-20T15:00:00+01:00` budou vráceny faktury vytvořené po zadaném datu, při zadání nesprávného formátu data a času server vrátí odpověď `400 Bad Request`.

```json
[
  {
    "id": 6,
    "custom_id": null,
    "name": "Apple Czech s.r.o.",
    "street": "Klimentsk\u00e1 1216/46",
    "street2": null,
    "city": "Praha",
    "zip": "11000",
    "country": "\u010cesk\u00e1 republika",
    "registration_no": "28897501",
    "vat_no": "CZ28897501",
    "bank_account": null,
    "iban": null,
    "full_name": null,
    "email": "",
    "email_copy": null,
    "phone": null,
    "web": "https://www.apple.cz",
    "html_url": "https://subdomena.fakturoid.cz/subjects/6",
    "url": "https://subdomena.fakturoid.cz/api/v1/subjects/6.json",
    "updated_at": "2012-05-13T12:11:38+02:00"
  },
  {
    "id": 28,
    "custom_id": null,
    "name": "MICROSOFT s.r.o.",
    "street": "Vysko\u010dilova 1461/2a",
    "street2": null,
    "city": "Praha",
    "zip": "14000",
    "country": "\u010cesk\u00e1 republika",
    "registration_no": "47123737",
    "vat_no": "CZ47123737",
    "bank_account": "",
    "iban": "",
    "full_name": "",
    "email": "",
    "email_copy": "",
    "phone": "",
    "web": "",
    "html_url": "https://subdomena.fakturoid.cz/subjects/28",
    "url": "https://subdomena.fakturoid.cz/api/v1/subjects/28.json",
    "updated_at": "2012-06-02T09:34:47+02:00"
  }
]
```

## Zobrazení kontaktu

- `GET /subjects/#{id}.json`

```json
{
  "id": 28,
  "custom_id": null,
  "name": "MICROSOFT s.r.o.",
  "street": "Vysko\u010dilova 1461/2a",
  "street2": null,
  "city": "Praha",
  "zip": "14000",
  "country": "\u010cesk\u00e1 republika",
  "registration_no": "47123737",
  "vat_no": "CZ47123737",
  "bank_account": "",
  "iban": "",
  "full_name": "",
  "email": "",
  "email_copy": "",
  "phone": "",
  "web": "",
  "html_url": "https://subdomena.fakturoid.cz/subjects/28",
  "url": "https://subdomena.fakturoid.cz/api/v1/subjects/28.json",
  "updated_at":"2012-06-02T09:34:47+02:00"
}
```

## Nový kontakt

- `POST /subjects.json`

```json
{
  "name" : "Apple cz s.r.o."
}
```

Po úspěšném vytvoření kontaktu dostanete ze serveru odpověď `201 Created`, hlavička `location` bude nastavena na adresu nově vytvořeného kontaktu. Spolu s tím bude navrácen právě vytvořený kontakt.

Při dosažení maximálního počtu kontaktů pro váš tarif dostanete při pokusu o vytvoření dalšího odpověď ze serveru `403 Forbiden`.

Pokud budou odeslána nevalidní data, dostanete ze serveru odpověď `422 Unprocessable Entity` a JSON se seznamem chyb v odeslaných datech.

Odeslaná data:

```json
  { }
```

Odpověď:

```json
{
  "errors": {
    "name": [
      "je povinn\u00e1 polo\u017eka",
      "je p\u0159\u00edli\u0161 kr\u00e1tk\u00fd/\u00e1 (min. 2 znak\u016f)"
    ]
  }
}
```

## Úprava kontaktu

- `PUT /subjects/#{id}.json`

```shell
{ 
  "name" : "Apple cz s.r.o."
}
```

Odpověď serveru na tento příkaz je `200 OK` a JSON s upraveným kontaktem. 

Při odeslání nevalidních dat dostanete ze serveru odpověď `422 Unprocessable Entity` a JSON se seznamem chyb v odeslaných datech.

## Smazání kontaktu

- `DELETE /subjects/#{id}.json`

Po úspěšném smazání kontaktu server vrátní odpověď `204 No Content`. Pokud jsou ke kontaktu přiřazeny faktury, nemůže být smazán a odpověď serveru bude `403 Forbidden`.
