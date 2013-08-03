# Invoice 

Faktura

<table>
<tr><th>Položka</th><th>Popis</th></tr>

<tr><td>id</td><td>identifikátor faktury</td></tr>

<tr><td>proforma</td><td>příznak proformy - true/false</td></tr>
<tr><td>partial_proforma</td><td>přiznak zda je proforma na plnou částku - true/false</td></tr>

<tr><td>number</td><td>číslo faktury (Př: 2011-0001, musí odpovídat formátu čísla v nastavení účtu)</td></tr>
<tr><td>variable_symbol</td><td>variabilní symbol (nepovinné - doplní se z čísla faktury)</td></tr>

<tr><td>your_name</td><td>název vaší firmy</td></tr>
<tr><td>your_street</td><td>vaše ulice</td></tr>
<tr><td>your_street2</td><td>vaše ulice 2</td></tr>
<tr><td>your_city</td><td>vaše město</td></tr>
<tr><td>your_zip</td><td>vaše poštovní směrovací číslo</td></tr>
<tr><td>your_country</td><td>vaše země (ISO kód)</td></tr>
<tr><td>your_registration_no</td><td>vaše IČ</td></tr>
<tr><td>your_vat_no</td><td>vaše DIČ</td></tr>

<tr><td>client_name</td><td>název firmy kontaktu</td></tr>
<tr><td>client_street</td><td>ulice kontatku</td></tr>
<tr><td>client_street2</td><td>ulice 2 kontaktu</td></tr>
<tr><td>client_city</td><td>město kontaktu</td></tr>
<tr><td>client_zip</td><td>poštovní směrovací číslo kontaktu</td></tr>
<tr><td>client_country</td><td>země kontaktu (ISO kód)</td></tr>
<tr><td>client_registration_no</td><td>IČ kontaktu</td></tr>
<tr><td>client_vat_no</td><td>DIČ kontaktu</td></tr>

<tr><td>subject_id</td><td>ID kontaktu (povinné)</td></tr>
<tr><td>generator_id</td><td>ID šablony ze které byla faktura vystavena (nepovinné)</td></tr>
<tr><td>related_id</td><td>ID proformy/faktury (nepovinné)</td></tr>

<tr><td>token</td><td>token pro public akci</td></tr>

<tr><td>status</td><td>stav faktury - open/sent/overdue/paid</td></tr>

<tr><td>order_number</td><td>číslo objednávky (nepovinné)</td></tr>

<tr><td>issued_on</td><td>datum vystavení (zobrazeno na faktuře)</td></tr>
<tr><td>taxable_fulfillment_due</td><td>datum zdanitelného plnění (nepovinné - doplní se dnes)</td></tr>
<tr><td>due</td><td>počet dní, než bude po splatnosti (nepovinné - doplní se z účtu)</td></tr>
<tr><td>due_on</td><td>datum splatnosti (doplní se podle due)</td></tr>
<tr><td>sent_at</td><td>datum a čas odeslání faktury</td></tr>
<tr><td>paid_at</td><td>datum a čas zaplacení faktury</td></tr>
<tr><td>reminder_sent_at</td><td>datum a čas odeslání upomínky</td></tr>
<tr><td>accepted_at</td><td>datum a čas odsouhlasení faktury klientem</td></tr>
<tr><td>canceled_at</td><td>datum stornování faktury (pouze pro neplátce DPH)</td></tr>

<tr><td>note</td><td>text před položkami faktury (nepovinné - doplní se z účtu)</td></tr>
<tr><td>footer_note</td><td>patička faktury (nepovinné - doplní se z účtu)</td></tr>

<tr><td>bank_account</td><td>číslo bankovního účtu (nepovinné - doplní se z účtu)</td></tr>
<tr><td>iban</td><td>IBAN (nepovinné - doplní se z účtu)</td></tr>
<tr><td>swift_bic</td><td>BIC (nepovinné - doplní se z účtu)</td></tr>

<tr><td>payment_method</td><td>bank (bankovní převod) / cash (hotově) / cod (dobírka)</td></tr>
<tr><td>currency</td><td>kód měny (nepovinné - doplní se z účtu, 3 znaky)</td></tr>
<tr><td>exchange_rate</td><td>kurz (nepovinné)</td></tr>
<tr><td>language</td><td>jazyk faktury</td></tr>
<tr><td>transferred_tax_liability</td><td>přenesená daňová povinnost true/false</td></tr>

<tr><td>subtotal</td><td>součet (bez DPH)</td></tr>
<tr><td>native_subtotal</td><td>součet v měně účtu</td></tr>
<tr><td>total</td><td>celkový součet (včetně DPH)</td></tr>
<tr><td>native_total</td><td>součet v měně účtu (včetně DPH)</td></tr>
<tr><td>remaining_amount</td><td>částka k zaplacení (včetně DPH)</td></tr>
<tr><td>remaining_native_amount</td><td>částka k zaplacení v měně účtu (včetně DPH)</td></tr>

<tr><td>html_url</td><td>HTML adresa faktury</td></tr>
<tr><td>public_html_url</td><td>veřejná HTML adresa faktury</td></tr>
<tr><td>url</td><td>API adresa faktury</td></tr>
<tr><td>subject_url</td><td>API adresa kontaktu</td></tr>
<tr><td>updated_at</td><td>datum poslední aktualizace faktury</td></tr>
</table>
  
_Poznámka:_ `your_*` a `client_*` položky se nastaví automaticky zkopírováním z nastavení účtu a z kontaktu odběratele při vytvoření faktury.

## Seznam faktur

- `GET /invoices.json` - seznam všech faktur
  
- `GET /invoices/proforma.json` - seznam zálohových faktur
  
- `GET /invoices/regular.json` - seznam faktur bez zálohových faktur

Faktury se stránkují po 10, pro další stránku faktur použijte `?page=2`. Faktury lze filtrovat podle parametrů `subject_id`, `since` a `status`. 

Při použití `?subject_id=4` budou vráceny faktury náležící danému kontaktu.

Při použití `?since=2012-05-20T15:00:00+01:00` budou vráceny faktury vytvořené po zadaném datu, při zadání nesprávného formátu data a času server vrátí odpověď `400 Bad Request`.

Při použití `?number=20120005` budou vráceny faktury s daným číslem.

Při použití `?status=paid` budou vráceny faktury s daným statusem. Při zadání neexistujícího statusu budou vráceny všechny faktury.

Filtry je možné libovolně kombinovat. Pokud budou podmínky takové, že žádný výsledek nebude vyhovovat, vrátí se prázdné pole.

<table>
  <tr><th>Status</th><th>Popis</th></tr>
  <tr><td>open</td><td>Faktura není zaplacena, odeslána ani po splatnosti.</td></tr>
  <tr><td>sent</td><td>Faktura byla odeslána a není po splatnosti.</td></tr>
  <tr><td>overdue</td><td>Faktura je po splatnosti.</td></tr>
  <tr><td>paid</td><td>Faktura je zaplacena.</td></tr>
  <tr><td>cancelled</td><td>Faktura je stornována. (pouze neplátci DPH)</td></tr>
</table>

```json
[
  {
    "id": 9,
    "proforma": false,
    "number": "2012-0004",
    // other invoice fields truncated ...
  },
  {
    "id": 10,
    "proforma": false,
    "number": "2012-0005",
    // other invoice fields truncated ...  
  }
]
```

## Zobrazení faktury

- `GET /invoices/#{id}.json`

```json
{
  "id": 9,
  "proforma": false,
  "number": "2012-0004",
  "variable_symbol": "20120004",
  "your_name": "Alexandr Hejsek",
  "your_street": "Hopsinkov\u00e1 14",
  "your_street2": null,
  "your_city": "Praha",
  "your_zip": "10000",
  "your_country": "CZ",
  "your_registration_no": "87654321",
  "your_vat_no": "CZ87654321",
  "client_name": "Microsoft a. s.",
  "client_street": "Trojanova 1216/46",
  "client_street2": null,
  "client_city": "Praha",
  "client_zip": "11000",
  "client_country": "CZ",
  "client_registration_no": "28444501",
  "client_vat_no": "CZ28444501",
  "subject_id": 4,
  "generator_id": 4,
  "related_id": null,
  "token": "udDTG8Q88M",
  "status": "paid",
  "order_number": null,
  "issued_on": "2011-10-13",
  "taxable_fulfillment_due": "2011-10-13",
  "due": 10,
  "due_on": "2011-10-23",
  "sent_at": null,
  "paid_at": "2011-10-20T12:11:37+02:00",
  "reminder_sent_at": null,
  "accepted_at": null,
  "cancelled_at": null,
  "note": null,
  "footer_note": null,
  "bank_account": "1234/1234",
  "iban": null,
  "swift_bic": null,
  "payment_method": "bank",
  "currency": "CZK",
  "exchange_rate": "1.0",
  "language": "cz",
  "transferred_tax_liability": false,
  "subtotal": "40000.0",
  "total": "48000.0",
  "native_subtotal": "40000.0",
  "native_total": "48000.0",
  "lines": [
    {
      "name": "PC",
      "quantity": "1.0",
      "unit_name": "",
      "unit_price": "20000.0",
      "vat_rate": 20,
      "with_vat": false
    },
    {
      "name": "Notebook",
      "quantity": "1.0",
      "unit_name": "",
      "unit_price": "20000.0",
      "vat_rate": 20,
      "with_vat": false
    }
  ],
  "html_url": "https://subdomena.fakturoid.cz/invoices/9",
  "public_html_url": "https://subdomena.fakturoid.cz/p/udDTG8Q88M/2012-0004",
  "url": "https://subdomena.fakturoid.cz/api/v1/invoices/9.json",
  "subject_url": "https://subdomena.fakturoid.cz/api/v1/subjects/4.json",
  "updated_at": "2012-05-13T12:11:37+02:00"
}
```

## Nová faktura

- `POST /invoices.json`

_Poznámka:_ Minimem pro vytvoření faktury je vyplnění atributu `subject_id`. 

```json
{
  "subject_id": "28",
  "number": "2012-0001",
  "currency": "CZK",
  "payment_method": "bank",
  "due": 10,
  "issued_on": "2012-03-30",
  "taxable_fulfillment_due": "2012-03-30",
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

Po úspěšném vytvoření faktury dostanete ze serveru odpověď ```201 Created```, hlavička ```location``` bude nastavena na adresu nově vytvořené faktury. Spolu s tím bude navrácena právě vytvořená faktura.

Pokud budou odeslána nevalidní data, dostanete ze serveru odpověď ```422 Unprocessable Entity``` a JSON se seznamem chyb v odeslaných datech.

Nevalidní data

```json
{ }
```

Odpověď bude:

```json
{
  "errors": {
    "client_name": [
      "je povinn\u00e1 polo\u017eka"
    ],
    "subject_id": [
      "je povinn\u00e1 polo\u017eka",
      "Tento kontakt nepat\u0159\u00ed va\u0161emu \u00fa\u010dtu"
    ]
  }
}
```

## Úprava faktury

- `PUT /invoices/#{id}.json`

```json
{
  "number": "2012-0022"
}
```

Odpověď serveru na tento příkaz je `200 OK` a JSON s upravenou fakturou. 

Při odeslání nevalidních dat dostanete ze serveru odpověď `422 Unprocessable Entity` a JSON se seznamem chyb v odeslaných datech.

## Událost na akce

- `POST /invoices/#{id}/fire.json?event=mark_as_sent`

<table>
<tr><th>event</th><th>popis</th></tr>
<tr><td>mark_as_sent</td><td>označit jako odeslanou</td></tr>
<tr><td>deliver</td><td>doručit emailem</td></tr>
<tr><td>pay</td><td>označit jako zaplacenou</td></tr>
<tr><td>pay_proforma</td><td>zaplatit proformu a vystavit daňový doklad</td></tr>
<tr><td>pay_partial_proforma</td><td>zaplatit částečnou proformu</td></tr>
<tr><td>remove_payment</td><td>odzaplatit</td></tr>
<tr><td>deliver_reminder</td><td>poslat upomínku</td></tr>
</table>

Po úspěšném vykonání události server vrátí odpověď `200 OK`. Pokud nebude možné událost vykonat, server vrátí odpověď `422 Unprocessable Entity`.

## Smazání faktury

- `DELETE /invoices/#{id}.json`

Po smazání faktury server vrátní odpověď `204 No Content`.
