# Základní popis

## Požadavek

Požadavky je nutné posílat pomocí HTTPS. Všechny URL adresy začínají ```https://subdomena.fakturoid.cz/api/v1/```

Například pro vytvoření požadavku na seznam vašich faktur přidáte adresu ```invoices.json``` k základu adresy. Požadavek povede tedy na adresu ```https://subdomena.fakturoid.cz/api/v1/invoices.json```.

Příklad

```shell
curl -u X:API_TOKEN -H 'User-Agent: YourApp (yourname@example.com)' \
  https://subdomena.fakturoid.cz/api/v1/invoices.json
```

Pro vytvoření nebo úpravu záznamu musíte přidat hlavičku ```Content-Type``` a data ve formátu JSON.

Příklad

```shell
curl -u X:653638dc733afce75130303fe6e6010f63768af0 -H 'User-Agent: YourApp (yourname@example.com)' \
  -H 'Content-Type: application/json' \
  -X POST -d '{ "subject_id": "28" }' \
  https://subdomena.fakturoid.cz/api/v1/invoices.json
```


## Identifikace vaší aplikace

Všechny požadavky musí obsahovat hlavičku ```User-Agent``` se jménem vaší aplikace a odkazem na ni nebo e-mailovou adresou.

```
User-Agent: YourApp (yourname@example.com) 
```

Pokud požadavek nebude obsahovat tuto hlavičku, dostanete jako odpověď server ```400 Bad Request```

## Pouze JSON

API podporuje pouze formát JSON. Při použití jiného formátu dostanete ze serveru odpověď ```415 Unsupported Media Type```.

## Ověření

Ověření se provádí pomocí HTTP BASIC AUTH, kde jako heslo uvedete api_token (zjistíte v Nastavení vašeho účtu). Username není vyžadován (můžete poslat prázdý řetězec nebo například 'x').

Příklad

```shell
curl -u X:653638dc733afce75130303fe6e6010f63768af0 \
  -H 'User-Agent: YourApp (yourname@example.com)' \
  https://subdomena.fakturoid.cz/api/v1/account.json
```

Při zadání špatných přihlašovacích údajů dostanete ze serveru odpověď ```401 Unauthorized```


## Stav pouze pro čtení

V případě údržby, kdy je robot ve stavu pouze pro čtení dostanete u HTTP POST, PUT a DELETE akcí odpověď ze serveru ```503 Service Unavailable```

## Zabokovaný účet

Máte-li zabokovaný účet, dostanete odpověď serveru `402 Payment Required` a seznam odkazů na nezaplacené faktury po splatnosti.
