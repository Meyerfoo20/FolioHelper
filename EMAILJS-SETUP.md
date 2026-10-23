# EmailJS-inställning för FormFolio

Service `service_9zpq6nl`, två mallar (allt EmailJS-relaterat är redan ifyllt i `index.html`):
- `template_w8cothh` → orderbekräftelse till kunden
- `template_umux0d9` → order, kunduppgifter och HTML-kod till carlssonneo20@gmail.com

Auto-Reply ska vara **avstängt** på båda mallarna (annars skickas dubbla mejl).

## template_w8cothh – till kunden
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

## template_umux0d9 – till dig
- **To Email:** `carlssonneo20@gmail.com`
- **Reply To:** `{{reply_to}}`
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

  <h3 style="border-bottom:2px solid #e5e7eb; padding-bottom:6px;">4. Profilbild</h3>
  <p style="margin:8px 0;"><img src="{{avatar_url}}" alt="Profilbild" width="200" style="border-radius:8px; max-width:200px;"></p>
  <p style="margin:8px 0 24px 0; line-height:1.7;">
    <a href="{{avatar_url}}" style="font-weight:bold;">Ladda ned bilden</a> &middot; <a href="{{avatar_viewer}}">Öppna på ImgBB</a><br>
    <span style="color:#6b7280;">{{avatar_note}}</span>
  </p>

  <h3 style="border-bottom:2px solid #e5e7eb; padding-bottom:6px;">5. HTML-kod ({{portfolio_size}})</h3>
  <p style="margin:8px 0; color:#6b7280;">Markera allt i rutan, kopiera och spara som <b>index.html</b>.</p>
  <pre style="background:#f3f4f6; border:1px solid #e5e7eb; border-radius:6px; padding:12px; font-size:11px; white-space:pre-wrap; word-break:break-all;">{{portfolio_code}}</pre>

</div>
```

Obs: `{{portfolio_code}}` med **två** klammerparenteser – då visas koden som text.

## ImgBB – profilbilden
1. Skapa ett gratis konto på https://imgbb.com
2. Gå till https://api.imgbb.com → **Get API key** och kopiera nyckeln.
3. Nyckeln är redan inlagd i `index.html` (`IMGBB_API_KEY`).

När kunden laddat upp en egen bild laddas den upp till ImgBB (max 1200 px, JPG) när ordern skickas.
I mejlet får du en förhandsbild och en nedladdningslänk. HTML-koden pekar på `profilbild.jpg` –
spara bilden med det namnet i samma mapp som `index.html` när du publicerar sidan.
Misslyckas uppladdningen skickas ordern ändå, och bilden finns då inbäddad direkt i koden.

## Bra att veta
- Gratisplanen: max 50 kB per utskick. Sidan krymper koden (och vid behov bilden) automatiskt så att den ryms. Varje order räknas som 2 mejl av dina 200/månad.
- Account → Security: lägg till din domän i "Allowed origins".
