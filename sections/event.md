# Event

Událost

<table>
<tr><th>Položka</th><th>Popis</th></tr>
<tr><td>name</td><td>typ události - generated, sent, accepted, sent_reminder, overdue, paid, paid_bank, payment_removed, unpaired_payment</td></tr>
<tr><td>created_at</td><td>datum a čas vytvoření události</td></tr>
<tr><td>invoice_id</td><td>ID faktury (nepovinné)</td></tr>
<tr><td>subject_id</td><td>ID kontaktu (nepovinné)</td></tr>
<tr><td>text</td><td>text události</td></tr>

<tr><td>invoice_url</td><td>API adresa faktury (nepovinné)</td></tr>
<tr><td>subject_url</td><td>API adresa kontaktu (nepovinné)</td></tr>
</table>

## Seznam událostí

- `GET /events.json` - všechny události (volitelně `?page=2` pro druhou stránku, `?since=2012-05-20T15:00:00+01:00`).

- `GET /events/paid.json` - událostí o zaplacení (volitelně `?page=2`, `?since=2012-05-20T15:00:00+01:00`).

Při použítí `since` budou vráceny události vytvořené po zadaném datu. Události jsou stránkovány po 15, pro další stránku použijte `?page=2` (v případě použití parametru since `&page=2`)

```json
[
  {
    "name": "paid",
    "created_at": "2012-05-29T16:28:53+02:00",
    "invoice_id": 11,
    "subject_id": 4,
    "text": "Zaplacena ",
    "invoice_url": "https://subdomena.fakturoid.cz/api/v1/invoices/11.json",
    "subject_url": "https://subdomena.fakturoid.cz/api/v1/subjects/4.json"
  },
  {
    "name": "payment_removed",
    "created_at": "2012-05-29T16:28:44+02:00",
    "invoice_id": 11,
    "subject_id": 4,
    "text": "Zaplacen\u00ed zru\u0161eno",
    "invoice_url": "https://subdomena.fakturoid.cz/api/v1/invoices/11.json",
    "subject_url": "https://subdomena.fakturoid.cz/api/v1/subjects/4.json"
  },
  {
    "name": "paid",
    "created_at": "2012-05-29T15:21:00+02:00",
    "invoice_id": 11,
    "subject_id": 4,
    "text": "Zaplacena ",
    "invoice_url": "https://subdomena.fakturoid.cz/api/v1/invoices/11.json",
    "subject_url": "https://subdomena.fakturoid.cz/api/v1/subjects/4.json"
  }
]
```

Při použití parametru since se špatnou hodnotou dostanete odpověď serveru `400 Bad Request`.