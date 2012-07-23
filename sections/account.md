# Account

Účet

<table>
<tr><th>Položka</th><th>Popis</th></tr>
<tr><td>subdomain</td><td>subdoména</td></tr>
<tr><td>plan</td><td>jméno tarifu</td></tr>
<tr><td>plan_price</td><td>cena tarifu</td></tr>

<tr><td>email</td><td>email vlastníka účtu</td></tr>
<tr><td>invoice_email</td><td>email, ze kterého jsou odesílány faktury</td></tr>
<tr><td>phone</td><td>telefon vlastníka účtu</td></tr>
<tr><td>web</td><td>web vlastníka účtu</td></tr>

<tr><td>name</td><td>jméno firmy</td></tr>
<tr><td>full_name</td><td>jméno majitele účtu</td></tr>
<tr><td>registration_no</td><td>IČ</td></tr>
<tr><td>vat_no</td><td>DIČ</td></tr>

<tr><td>street</td><td>ulice</td></tr>
<tr><td>street2</td><td>ulice 2</td></tr>
<tr><td>city</td><td>město</td></tr>
<tr><td>zip</td><td>PSČ</td></tr>
<tr><td>country</td><td>země</td></tr>

<tr><td>bank_account</td><td>bankovní účet</td></tr>
<tr><td>iban</td><td>IBAN</td></tr>
<tr><td>swift_bic</td><td>BIC (pro SWIFT platby)</td></tr>

<tr><td>currency</td><td>měna</td></tr>
<tr><td>unit_name</td><td>výchozí jednotka</td></tr>
<tr><td>vat_rate</td><td>výchozí daňová sazba</td></tr>
<tr><td>displayed_note</td><td>text patičky</td></tr>
<tr><td>invoice_note</td><td>text před položkami faktury</td></tr>
<tr><td>due</td><td>počet dní před splatností</td></tr>

<tr><td>html_url</td><td>HTML adresa účtu</td></tr>
<tr><td>url</td><td>API adresa účtu</td></tr>
<tr><td>updated_at</td><td>datum poslední úpravy účtu</td></tr>
<tr><td>created_at</td><td>datum vytvoření účtu</td></tr>
</table>

_Poznámka:_ Účet je read only, pro změny použijte prosím webové rozhraní.

## Detail účtu

- `GET /account.json`

```json
{
  "subdomain": "testdph",
  "plan": "2",
  "plan_price": 300,
  "email": "testdph@test.cz",
  "invoice_email": "testdph@test.cz",
  "phone": null,
  "web": null,
  "name": "Alexandr Hejsek",
  "full_name": null,
  "registration_no": "87654321",
  "vat_no": "CZ87654321",
  "street": "Hopsinkov\u00e1 14",
  "street2": null,
  "city": "Praha",
  "zip": "10000",
  "country": "\u010cesk\u00e1 republika",
  "bank_account": "1234/1234",
  "iban": null,
  "swift_bic": null,
  "currency": "CZK",
  "unit_name": "",
  "vat_rate": 20,
  "displayed_note": null,
  "invoice_note": null,
  "due": 14,
  "html_url": "https://subdomena.fakturoid.cz/account",
  "url": "https://subdomena.fakturoid.cz/api/v1/account.json",
  "updated_at": "2012-06-01T23:12:44+02:00",
  "created_at":"2012-05-13T12:11:36+02:00"
}
```
