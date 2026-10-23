# EmailJS-inställning för FormFolio

Allt skickas med **en** mall (`template_w8cothh`) via service `service_9zpq6nl`:
- **Huvudmallen (Content)** → orderbekräftelse till kunden
- **Auto-Reply** → order, kunduppgifter och HTML-kod till carlssonneo20@gmail.com

Kvar att fylla i `index.html`: `publicKey` (Account → General → Public Key).

## Huvudmallen – till kunden
- **To Email:** `{{to_email}}`
- **From Name:** FormFolio
- **Reply To:** `{{reply_to}}`
- **Subject:** `Orderbekräftelse {{order_id}} – FormFolio`
- **Content:**
```
Hej {{to_name}}!

Tack för din beställning. Din order {{order_id}} är genomförd.

Domän: {{domain}}
Design: {{template_name}} ({{theme_name}})
Pris: {{price}}

Vi sätter nu upp din hemsida. När den är online skickar vi fakturan till dig
(30 dagars betaltid).

Vänliga hälsningar
FormFolio
```

## Auto-Reply – till dig
Fliken **Auto-Reply** i samma mall → slå på den.
- **To Email:** `{{admin_email}}` (eller skriv carlssonneo20@gmail.com direkt)
- **Reply To:** `{{customer_email}}`
- **Subject:** `Ny order {{order_id}} – {{domain}}`
- **Content:** Edit Content → **Code Editor**, klistra in:

```html
<div style="font-family:Arial,sans-serif; font-size:14px; color:#1f2937; max-width:720px;">

  <h2 style="margin:0 0 4px 0;">Ny beställning – {{order_id}}</h2>
  <p style="margin:0 0 24px 0; color:#6b7280;">Mottagen {{order_date}}</p>

  <h3 style="border-bottom:2px solid #e5e7eb; padding-bottom:6px;">1. Domän</h3>
  <p style="font-size:18px; font-weight:bold; margin:8px 0 24px 0;">{{domain}}</p>

  <h3 style="border-bottom:2px solid #e5e7eb; padding-bottom:6px;">2. Beställning</h3>
  <p style="margin:8px 0 24px 0; line-height:1.7;">
    Mall: {{template_name}}<br>
    Färgtema: {{theme_name}}<br>
    Pris: {{price}}
  </p>

  <h3 style="border-bottom:2px solid #e5e7eb; padding-bottom:6px;">3. Kund &amp; fakturauppgifter</h3>
  <p style="margin:8px 0 24px 0; line-height:1.7;">
    Namn/Företag: {{customer_name}}<br>
    Pers/Org.nr: {{customer_id}}<br>
    E-post: {{customer_email}}<br>
    Adress: {{customer_street}}<br>
    {{customer_zip}} {{customer_city}}
  </p>

  <h3 style="border-bottom:2px solid #e5e7eb; padding-bottom:6px;">4. HTML-kod ({{portfolio_size}})</h3>
  <p style="margin:8px 0; color:#6b7280;">Markera allt i rutan, kopiera och spara som <b>index.html</b>.</p>
  <pre style="background:#f3f4f6; border:1px solid #e5e7eb; border-radius:6px; padding:12px; font-size:11px; white-space:pre-wrap; word-break:break-all;">{{portfolio_code}}</pre>

</div>
```

Obs: `{{portfolio_code}}` med **två** klammerparenteser – då visas koden som text.

## Bra att veta
- Gratisplanen: max 50 kB per utskick. Sidan stoppar beställningen med ett meddelande om koden blir över 45 kB. Varje order räknas som 2 mejl (bekräftelse + auto-reply) av dina 200/månad.
- Account → Security: lägg till din domän i "Allowed origins".
