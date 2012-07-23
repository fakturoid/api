# Status kódy

Seznam status kódů a jejich použití v aplikaci.

## Základy a přihlášení

<table>
  <tr>
    <th>Případ</th>
    <th>Status Kód</th>
  </tr>
  <tr>
    <td>Chybějící hlavička 'User-Agent'</td>
    <td>400 Bad Request</td>
  </tr>
  <tr>
    <td>Zadání špatné subdomény nebo API_TOKEN</td>
    <td>401 Unauthorized</td>
  </tr>
  <tr>
    <td>Neexistující URL adresa</td>
    <td>404 Not Found</td>
  </tr>
  <tr>
    <td>Zadání špatného ID</td>
    <td>404 Not Found</td>
  </tr>
  <tr>
    <td>Použití jiného formátu než JSON</td>
    <td>415 Unsupported Media Type</td>
  </tr>
  <tr>
    <td>Zapnutý stav pouze pro čtení (POST, PUT a DELETE akce)</td>
    <td>503 Service Unavailable</td>
  </tr>
</table>

## Účet

<table>
  <tr>
    <th>HTTP</th>
    <th>Případ</th>
    <th>Status Kód</th>
  </tr>
  <tr>
    <td>GET&nbsp;/account.json</td>
    <td>Detail účtu</td>
    <td>200 OK</td>
  </tr>
</table>

## Kontakty

<table>
  <tr>
    <th>HTTP</th>
    <th>Případ</th>
    <th>Status Kód</th>
  </tr>
  <tr>
    <td>GET&nbsp;/subjects.json</td>
    <td>Seznam kontaktů</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>GET&nbsp;/subjects.json</td>
    <td>Seznam kontaktů se špatně zadaným parametrem 'since'</td>
    <td>400 Bad Request</td>
  </tr>
  <tr>
    <td>GET&nbsp;/subjects/ID.json</td>
    <td>Zobrazení kontaktu</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>POST&nbsp;/subjects.json</td>
    <td>Vytvoření kontaktu s validními daty</td>
    <td>201 Created</td>
  </tr>
  <tr>
    <td>POST&nbsp;/subjects.json</td>
    <td>Vytvoření kontaktu s nevalidními daty</td>
    <td>422 Unprocessable Entity</td>
  </tr>
  <tr>
    <td>POST&nbsp;/subjects.json</td>
    <td>Vytvoření kontaktu nad povolený limit tarifu</td>
    <td>403 Forbidden</td>
  </tr>
  <tr>
    <td>PUT&nbsp;/subjects/ID.json</td>
    <td>Úprava kontaktu s validními daty</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>PUT&nbsp;/subjects/ID.json</td>
    <td>Úprava kontaktu s nevalidními daty</td>
    <td>422 Unprocessable Entity</td>
  </tr>
  <tr>
    <td>DELETE&nbsp;/subjects/ID.json</td>
    <td>Smazání kontaktu</td>
    <td>204 No Content</td>
  </tr>
  <tr>
    <td>DELETE&nbsp;/subjects/ID.json</td>
    <td>Smazání kontaktu, ke kterému jsou vystaveny faktury</td>
    <td>403 Forbidden</td>
  </tr>
</table>

## Faktury

<table>
  <tr>
    <th>HTTP</th>
    <th>Případ</th>
    <th>Status Kód</th>
  </tr>
  <tr>
    <td>GET&nbsp;/invoices.json</td>
    <td>Seznam faktur</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>GET&nbsp;/invoices/regular.json</td>
    <td>Seznam faktur bez zálohových faktur</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>GET&nbsp;/invoices/proforma.json</td>
    <td>Seznam zálohových faktur</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>GET&nbsp;/invoices.json (/invoices/regular.json, /invoices/proforma.json) </td>
    <td>Seznam faktur se špatně zadaným parametrem 'since'</td>
    <td>400 Bad Request</td>
  </tr>
  <tr>
    <td>GET&nbsp;/invoices.json (/invoices/regular.json, /invoices/proforma.json) </td>
    <td>Seznam faktur se zadaným 'subject_id' s neexistujícím kontaktem</td>
    <td>404 Not Found</td>
  </tr>
  <tr>
    <td>GET&nbsp;/invoices/ID.json</td>
    <td>Zobrazení faktury</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>POST&nbsp;/invoices.json</td>
    <td>Vytvoření faktury s validními daty</td>
    <td>201 Created</td>
  </tr>
  <tr>
    <td>POST&nbsp;/invoices.json</td>
    <td>Vytvoření faktury s nevalidními daty</td>
    <td>422 Unprocessable Entity</td>
  </tr>
  <tr>
    <td>PUT&nbsp;/faktury/ID.json</td>
    <td>Úprava faktury s validními daty</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>PUT&nbsp;/invoices/ID.json</td>
    <td>Úprava faktury s nevalidními daty</td>
    <td>422 Unprocessable Entity</td>
  </tr>
  <tr>
    <td>POST&nbsp;/fire?event=event_name</td>
    <td>Správně zadaná událost</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>POST&nbsp;/fire?event=event_name</td>
    <td>Špatně zadané nebo neexistující event_name</td>
    <td>422 Unprocessable Entity</td>
  </tr>
  <tr>
    <td>DELETE&nbsp;/invoices/ID.json</td>
    <td>Smazání faktury</td>
    <td>204 No Content</td>
  </tr>
</table>


## Šablony

<table>
  <tr>
    <th>HTTP</th>
    <th>Případ</th>
    <th>Status Kód</th>
  </tr>
  <tr>
    <td>GET&nbsp;/generators.json</td>
    <td>Seznam šablon</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>GET&nbsp;/generators/template.json</td>
    <td>Seznam šablon bez opakování</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>GET&nbsp;/generators/reccuring.json</td>
    <td>Seznam pravidelných šablon</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>GET&nbsp;/generators.json (/generators/template.json, /generators/reccuring.json) </td>
    <td>Seznam šablon se špatně zadaným parametrem 'since'</td>
    <td>400 Bad Request</td>
  </tr>
  <tr>
    <td>GET&nbsp;/invoices.json (/invoices/template.json, /invoices/reccuring.json) </td>
    <td>Seznam šablon se zadaným 'subject_id' s neexistujícím kontaktem</td>
    <td>404 Not Found</td>
  </tr>
  <tr>
    <td>GET&nbsp;/generators/ID.json</td>
    <td>Zobrazení šablony</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>POST&nbsp;/generators.json</td>
    <td>Vytvoření šablony s validními daty</td>
    <td>201 Created</td>
  </tr>
  <tr>
    <td>POST&nbsp;/generators.json</td>
    <td>Vytvoření šablony s nevalidními daty</td>
    <td>422 Unprocessable Entity</td>
  </tr>
  <tr>
    <td>PUT&nbsp;/generators/ID.json</td>
    <td>Úprava šablony s validními daty</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>PUT&nbsp;/generators/ID.json</td>
    <td>Úprava šablony s nevalidními daty</td>
    <td>422 Unprocessable Entity</td>
  </tr>
  <tr>
    <td>DELETE&nbsp;/generators/ID.json</td>
    <td>Smazání šablony</td>
    <td>204 No Content</td>
  </tr>
</table>

## Události

<table>
  <tr>
    <th>HTTP</th>
    <th>Případ</th>
    <th>Status Kód</th>
  </tr>
  <tr>
    <td>GET&nbsp;/events.json (/events/paid.json)</td>
    <td>Správně zadaný požadavek</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>GET&nbsp;/events.json (/events/paid.json)</td>
    <td>Špatně zadaný parametr 'since'</td>
    <td>400 Bad Request</td>
  </tr>
  <tr>
    <td>GET&nbsp;/events.json (/events/paid.json)</td>
    <td>Parametr 'page' byl zadaný s neexistující stránkou</td>
    <td>400 Bad Request</td>
  </tr>
</table>

## Důležité události

<table>
  <tr>
    <th>HTTP</th>
    <th>Případ</th>
    <th>Status Kód</th>
  </tr>
  <tr>
    <td>GET&nbsp;/todos.json</td>
    <td>Správně zadaný požadavek</td>
    <td>200 OK</td>
  </tr>
  <tr>
    <td>GET&nbsp;/todos.json</td>
    <td>Špatně zadaný parametr 'since'</td>
    <td>400 Bad Request</td>
  </tr>
  <tr>
    <td>GET&nbsp;/todos.json</td>
    <td>Parametr 'page' byl zadaný s neexistující stránkou</td>
    <td>400 Bad Request</td>
  </tr>
</table>