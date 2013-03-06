# Message

Posílání emailů k fakturám

__Poznámka:__ Je přístupné pouze pro placené účty.

<table>
  <tr><th>Položka</th><th>Popis</th></tr>
  <tr><td>email</td><td>E-mail příjemce</td></tr>
  <tr><td>email_copy</td><td>Kopie na e-mail</td></tr>
  <tr><td>subject</td><td>Předmět emailu</td></tr>
  <tr><td>message</td><td>Text e-mailu</td></tr>
</table>

## Odeslání e-mailu

- `POST /invoices/#{invoice_id}/message`

Minimem pro odeslání e-mailu je vyplnění atributu `email`, všechna ostatní pole se doplní z výchozích nastavení.

Použité výchozí hodnoty:
<table>
  <tr><th>Stav faktury</th><th>Popis</th></tr>
  <tr><td>Po splatnost</td><td>Použijí se výchozí hodnoty pro upomínku.</td</tr>
  <tr><td>Ostatní</td><td>Použijí se výchozí hodnoty pro odeslání faktury.</td></tr>
</table> 

```json
{
  "email": "test@test.cz",
  "email_copy":"",
  "subject": "E-mail subject",
  "message": "Hello,\n\nI have invoice for you.\n#link#\n\n   John Doe"
}
```

Po úspěšném vytvoření e-mailu server vrací odpověď `201 Created`.

Pokud budou odeslána nevalidní data, server odpoví `422 Unprocessable Entity` se seznamem chyb.

Při odeslání požadavku neplaceným účtem bude odpověď serveru `403 Forbidden`.

Proměnné, které je možné v textu e-mailu použít:
<table>
  <tr><th>Proměnná</th><th>Popis</th></tr>
  <tr><td>#link#</td><td>odkaz na stránku s náhled a tiskem faktury</td</tr>
  <tr><td>#no#</td><td>číslo faktury</td</tr>
  <tr><td>#vs#</td><td>variabilní symbol</td</tr>
  <tr><td>#price#</td><td>koncová cena</td></tr>
</table>
