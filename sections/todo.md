# Todo

Důležitá událost

<table>
<tr><th>Položka</th><th>Popis</th></tr>
<tr><td>name</td><td>typ události - initial_todo, initial_fb, already_paid, unpaired_payment, email_bounced</td></tr>
<tr><td>created_at</td><td>datum a čas vytvoření události</td></tr>
<tr><td>completed_at</td><td>datum a čas odškrtnutí události</td></tr>
<tr><td>invoice_id</td><td>ID faktury</td></tr>
<tr><td>subject_id</td><td>ID kontaktu</td></tr>
<tr><td>text</td><td>text události</td></tr>

<tr><td>invoice_url</td><td>API adresa faktury</td></tr>
<tr><td>subject_url</td><td>API adresa kontaktu</td></tr>
</table>

## Seznam důležitých událostí

- `GET /todos.json` (volitelně `?page=2` pro druhou stránku, `?since=2012-05-20T15:00:00+01:00`).

Při použítí `since` budou vráceny důležité události vytvořené po zadaném datu. Důležité události jsou stránkovány po 15, pro další stránku použijte `?page=2` (v případě použití parametru since `&page=2`)

```json
[
  {
    "name": "initial_fb",
    "created_at": "2012-05-13T12:11:36+02:00",
    "completed_at": null,
    "invoice_id": null,
    "subject_id": null,
    "text": "P\u0159idejte si m\u011b do <a href='https://www.facebook.com/fakturoid'>Facebooku</a> a budete v\u017edy v\u011bd\u011bt, co jsem se nau\u010dil nov\u00e9ho.",
    "invoice_url": null,
    "subject_url": null
  },
  {
    "name": "initial",
    "created_at": "2012-05-13T12:11:36+02:00",
    "completed_at": "2012-06-02T09:29:15+02:00",
    "invoice_id": null,
    "subject_id": null,
    "text": "P\u0159\u00edklad d\u016fle\u017eit\u00e9 ud\u00e1losti, kter\u00e1 vy\u017eaduje va\u0161i pozornost. Od\u0161krtn\u011bte ji t\u00edmto tla\u010d\u00edtkem \u2192",
    "invoice_url": null,
    "subject_url": null
  }
]
```

Při použití parametru since se špatnou hodnotou dostanete odpověď serveru `400 Bad Request`.