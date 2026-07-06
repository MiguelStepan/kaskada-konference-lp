# Kaskáda — Landing pages pro konference (B2B)

Mobile-first konverzní landing pages pro zachycení B2B poptávek na konference,
napojené jako prolink z Meta ads. Self-contained HTML soubory + sdílená složka s assety.

```
Kaskáda_LP/
├── index.html              ← hlavní LP (evergreen nabídka konferencí)
├── akce-rijen-2026.html    ← akční LP: sleva na pronájem podle počtu osob
└── assets/                 ← fotky a loga (sdílené)
```

Obě LP sdílí brand systém a assety; každou lze nasadit samostatně (jiná ad kampaň).

## 🎯 Akční LP (`akce-rijen-2026.html`)
Nabídka na **říjen 2026**: sleva na pronájem konferenčních prostor podle počtu osob
— **20+ → 20 %**, **40+ → 40 %**, **60+ → 60 %**. Formulář má **živý výpočet slevy**:
jakmile host zadá počet osob, rovnou vidí svou slevu a rozsvítí se odpovídající tier.
Odeslaná sleva jde i do e-mailu (skryté pole `sleva_pronajem`).

⚠️ **Deadline poptávky** je zatím `30. 9. 2026` (2× v souboru: hero + text). Potvrď / uprav
skutečné datum — hledej komentář `DEADLINE`.

---

> Obsah (kapacity, prostory, kontakty) vychází z prezentace
> **Hotel Brno Kaskáda – Prezentace.pdf** (Hotel Kaskáda Brno, TMR Hotels).

## ✅ Než pustíš ads — co doplnit

### 1) Formulář → odesílání na e-mail (Web3Forms) — ✅ HOTOVO
Access Key `50ed6c21-8cb6-4977-9472-484f88053f9d` je vložený ve všech 3 LP
(pole `access_key`). Poptávky chodí na e-mail zaregistrovaný ve Web3Forms.
Bez backendu, se spam ochranou (honeypot), zdarma 250 odeslání/měsíc.
- **Poslední test udělej z nasazené Netlify adresy** (ne z lokálního souboru).
- Autoresponder (auto-odpověď zákazníkovi) se dá zapnout ve Web3Forms dashboardu.

### 2) Kontakty — ✅ doplněné z prezentace
E-mail `jakub.julina@tmr.sk` a telefon `+420 604 290 817` jsou už v hlavičce,
patičce i sticky tlačítku. Zkontroluj, že jsou aktuální, a doplň ještě:
- odkaz na **zásady ochrany osobních údajů** u souhlasu ve formuláři (`href="#"`)
- přesnou **adresu** v patičce (teď „Jinačovice, 15 min od Brna“ + odkaz na mapu)

### 3) Měření konverzí — GA4 + Meta Pixel
V `<head>` jsou připravené **zakomentované** bloky. Až budeš mít účty:
- odkomentuj blok GA4 a vlož `G-XXXXXXXXXX` (Measurement ID),
- odkomentuj blok Meta Pixel a vlož `XXXXXXXXXXXXXXX` (Pixel ID).

Konverze z odeslaného formuláře se pak pošle **automaticky**:
- GA4 event `generate_lead`
- Meta Pixel event `Lead`

(Logika je už ve skriptu dole, není třeba nic dopisovat.)

---

## 📐 Struktura (lean, optimalizováno na konverzi)
Stránka je záměrně krátká, jeden jasný message a **formulář je hned v heru** (nad ohybem):
1. **Hero** — value prop + čísla + **kompaktní formulář** (na desktopu vpravo, na mobilu pod textem)
2. **Value** — 3 body (vše pod střechou / 15 min od Brna / golf) + fotka
3. **Prostory** — sály + SVG diagramy uspořádání (divadlo / škola / U-tvar)
4. **Closing CTA** + footer

Sticky CTA (mobil) i tlačítka v sekcích míří kotvou zpět na formulář v heru (`#poptavka`).

## 🖼️ Fotky konferenčních sálů (až je budeš mít)
V sekci **Prostory** jsou teď SVG **diagramy uspořádání** s kapacitami — fungují i bez fotek.
Až budeš mít fotky sálů, vlož je do `assets/` a přidej `<img>` nad blok `.layouts`
(postup je v komentáři u sekce). Loga klientů / referenci lze doplnit později.

---

## 🚀 Nasazení
Stránka je statická → nahraješ celou složku kamkoliv:
- **Netlify / Vercel** — přetáhni složku do dashboardu (drag & drop), dostaneš URL.
- **FTP / vlastní hosting** — nahraj `index.html` + `assets/` do webového rootu.

Do Meta ads pak dáš výslednou URL jako cílový odkaz.

> Tip: URL, na kterou míří ads, si ulož s UTM parametry
> (`?utm_source=meta&utm_campaign=konference`) pro čistší data v GA4.
