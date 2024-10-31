# Vefforritun 1, 2024: Verkefni 9, JS #3

- [Fyrirlestur 10.3: Inngangur að verkefni 9 (43:39)](https://youtu.be/TjY6TTenRq8)
- [Fyrirlestur 11.2: Verkefni 9, async útfærslur (46:54)](https://www.youtube.com/watch?v=9_N6wTkdkvs)
- [Fyrirlestur 11.4: Verkefni 9, útfærslur á stöðum (37:34)](https://www.youtube.com/watch?v=ufqLNV2zJgQ)

## Markmið

- Forrita á móti DOM, _Document Object Model_.
- Forrita á móti API með `fetch`.
- Lesa gögn úr JSON.

## Grunnur

Gefin er grunnur að verkefni:

- `package.json` með uppsetningu á `browser-sync`, `lint` og `prettier` scriptum.
- `.vscode` stillingar til að nota `eslint` og `prettier` þegar skjöl eru vistuð.
- `index.html` með leiðbeiningum og tengingu við `main.js` sem einingu (_module_).
- Grunnútlit í `styles.css`.
- Grunnur að forriti í `./src` með athugasemdir og tillögur að útfærslum eru í skjölunum.

Skjölun notar [`jsdoc`](https://jsdoc.app/).

### NPM

Til að nota þennan grunn sem gefinn er hér þarf að sækja það frá GitHub og keyra NPM:

```bash
# Inni í möppu sem á að geyma verkefnið
git clone https://github.com/vefforritun/vef1-2024-v9.git
# eða
git clone git@github.com:vefforritun/vef1-2024-v9.git

# Förum inn í möppu
cd vef1-2024-v9

# Sækjum öll dependency með NPM
npm install

# Keyrum NPM script fyrir development
npm run dev
```

Áður en skilað er þarf að breyta remote í þitt eigið repo:

```bash
git remote remove origin
git remote add origin <slóð á þitt GitHub repo>
```

## Virkni

### Grunnviðmót

Smíða skal allt viðmót í JavaScript—ekkert skal vera innan `<body>` í `index.html`.

Í grunnviðmóti skal vera:

- Fyrirsögn.
- Inngangstexti, t.d. `Veldu stað til að sjá hita- og úrkomuspá.`.
- Takkar fyrir allar gefnar leitir.
- Virkni sem leitar fyrir hvern og einn takka.
- Element sem birtir leitarniðurstöður með titli, falið í byrjun.

### Leit út frá staðsetningu notanda

Fyrsti takki sem birtur er skal vera takki sem bíður notanda að leita að veðurspá út frá sinni staðsetningu. Nota skal til þess [`navigator.geolocation`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/geolocation).

Athugið að gera þarf ráð fyrir að notandi gefi ekki leyfi til að sækja staðsetningu og þarf þá að birta villuskilaboð.

### API tenging

Nota skal [API frá Open-Meteo](https://open-meteo.com/) til að sækja veðurspár. Sækja skal a.m.k. hitastig og úrkomu.

Sækja skal gögn fyrir daginn í dag.

[Dæmi um kall í vefþjónustu](https://api.open-meteo.com/v1/forecast?latitude=65.6835&longitude=-18.0878&hourly=temperature_2m,apparent_temperature,precipitation&timezone=GMT&forecast_days=1) þar sem:

- `latitude` og `longitude` eru staðsetning notanda, þetta þarf að senda út frá því sem notandi velur.
- `hourly` eru gögn sem sótt eru: `temperature_2m`, og `precipitation`.
- `timezone` er `GMT`.
- `forecast_days` er `1`, eingöngu dagurinn í dag.

### Leitarniðurstöður

Þegar gögn koma til baka frá vefþjónustu skal birta þau í töflu. Gögnin eru á JSON formi og þarf að vinna úr þeim.

Fyrir ofan töflu skal birta heiti á staðsetningu, t.d. `Reykjavík` og latitude og longitude.

Birta skal töflu með eftirfarandi dálkum:

- Klukkustund, ekki skal birta alla dagsetningu, t.d. skal birta `12:00` en ekki `2024-10-21T12:00:00`.
- Hitastig án einingar, eining skal tiltekin í fyrstu röð.
- Úrkomu án einingar, eining skal tiltekin í fyrstu röð.

### Mismunandi stöður

Í forritinu skal gera ráð fyrir mismunandi stöðum sem geta komið upp:

- Notandi gefur ekki leyfi til að sækja staðsetningu.
- Bið eftir svari frá vefþjónustu, nota skal `sleep` fall sem gefið er til að bíða.
- Villa við að sækja gögn frá vefþjónustu.
- Gögn koma til baka frá vefþjónustu.

## eslint

Uppsett er `eslint`, þegar það er keyrt með `npm run lint` á ekki að skila neinum villum.

## Netlify

Skila skal verkefninu keyrandi á Netlify (eða sambærilegri hýsingu). Gefin er sama `build` script í `package.json` en uppfæra þarf hana m.v. það sem er í `lib/` möppu og CSS skrá.

## Mat

- 20% Grunnviðmót útfært.
- 10% Leit út frá staðsetningu notanda útfærð.
- 20% Tenging við API útfærð.
- 20% Leitarniðurstöður birtar.
- 10% Tekið tillit til mismunandi staða í svari.
- 10% Verkefni sett upp á GitHub og tengt Netlify.
- 10% Engar `eslint` villur þegar `npm run lint` er keyrt.

## Sett fyrir

Verkefni sett fyrir mánudaginn 21. október 2024.

## Skil

Skila skal í Canvas, seinasta lagi fyrir lok dags fimmtudaginn 31. október 2024.

Skilaboð skulu innihalda:

- Slóð á verkefnið keyrandi í hýsingu
- Slóð á GitHub repo fyrir verkefni. Dæmatímakennurum skal hafa verið boðið í repo. Notendanöfn þeirra eru:
  - `digitalsigga`
  - `ofurtumi`
  - `osk`
  - `polarparsnip`
  - `reynirjr`

Skila má eins oft og þið viljið þar til skilafrestur rennur út.

## Einkunn

Leyfilegt er að ræða, og vinna saman að verkefni en **skrifið ykkar eigin lausn**. Ef tvær eða fleiri lausnir eru mjög líkar þarf að færa rök fyrir því, annars munu allir hlutaðeigandi hugsanlega fá 0 fyrir verkefnið.

Ef stórt mállíkan (LLM, „gervigreind“, t.d. ChatGTP) er notað til að skrifa part af lausn skal taka það fram. [Sjá nánar á upplýsingasíða um gervigreind hjá HÍ](https://gervigreind.hi.is/).

Sett verða fyrir tíu minni verkefni þar sem átta bestu gilda 5% hvert, samtals 40% af lokaeinkunn.

Sett verða fyrir tvö hópverkefni þar sem hvort um sig gildir 10%, samtals 20% af lokaeinkunn.

> Útgáfa 0.1
