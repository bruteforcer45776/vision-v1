# Vision V1 — Analisi Presenza Online
**vision-v1.it** · Powered by Bixont Marketing Agency

---

## 🚀 Deploy su Netlify + vision-v1.it

### Struttura progetto
```
vision-v1/
├── index.html                    ← App frontend completa
├── netlify.toml                  ← Config Netlify
├── netlify/
│   └── functions/
│       └── analyze.js            ← Serverless function (Google APIs)
└── README.md
```

---

## Step 1 — GitHub

1. Vai su **github.com** → New repository → Nome: `vision-v1` → Public
2. Carica tutti i file (trascina o usa GitHub Desktop)
3. Commit: "Initial Vision V1 deploy"

---

## Step 2 — Netlify

1. Vai su **netlify.com** → Add new site → Import from Git
2. Seleziona il repo `vision-v1`
3. Build settings: lascia tutto vuoto (HTML puro)
4. Clicca **Deploy site**
5. Il sito va live su `random-name.netlify.app`

---

## Step 3 — Variabili d'ambiente (API Key)

In Netlify Dashboard → **Site settings → Environment variables**:

| Variabile | Dove ottenerla | Costo |
|-----------|---------------|-------|
| `GOOGLE_API_KEY` | [Google Cloud Console](https://console.cloud.google.com) → Abilita "Places API" | ~$0.017/richiesta |
| `PSI_API_KEY` | Stesso progetto Google → "PageSpeed Insights API" | Gratis |
| `LEAD_WEBHOOK` | [Make.com](https://make.com) o Zapier → Webhook URL | Gratis piano base |

### Come ottenere GOOGLE_API_KEY:
1. Vai su [console.cloud.google.com](https://console.cloud.google.com)
2. Crea nuovo progetto → "Vision V1"
3. API & Services → Enable APIs → cerca e abilita:
   - **Places API**
   - **PageSpeed Insights API**
4. Credentials → Create credentials → API Key
5. Copia la key e incollala in Netlify

---

## Step 4 — Dominio vision-v1.it

In Netlify → **Site settings → Domain management → Add custom domain**:
- Inserisci `vision-v1.it` → Confirm

Netlify ti fornisce:
```
Type A      → 75.2.60.5
Type CNAME  → [tuo-sito].netlify.app
```

Nel pannello DNS del tuo registrar (Aruba/Register.it/Namecheap):
1. Elimina eventuali record A esistenti
2. Aggiungi record `A @ → 75.2.60.5`
3. Aggiungi record `CNAME www → [tuo-sito].netlify.app`
4. Attendi 15-60 minuti

Netlify attiva **HTTPS gratis** automaticamente via Let's Encrypt.

---

## Step 5 — Lead Capture con Make.com (gratis)

1. Vai su [make.com](https://make.com) → Create scenario
2. Primo modulo: **Webhooks → Custom webhook** → copia URL
3. Incolla URL in Netlify come variabile `LEAD_WEBHOOK`
4. Secondo modulo: **Email (Gmail/Brevo)** → invia report PDF
5. Opzionale: aggiungi **Google Sheets** per salvare i lead

---

## 🔧 Aggiornamenti futuri

Per aggiornare il sito basta:
1. Modifica i file in locale
2. Carica su GitHub (o usa git push)
3. Netlify rideploya automaticamente in ~30 secondi

---

## 📊 Stack tecnico

| Layer | Tecnologia | Costo |
|-------|-----------|-------|
| Frontend | HTML/CSS/JS puro | Gratis |
| Hosting | Netlify | Gratis (fino a 100GB bandwidth) |
| Serverless | Netlify Functions | Gratis (125K chiamate/mese) |
| GMB Data | Google Places API | Pay per use (~€0.015/call) |
| Speed Data | PageSpeed Insights | Gratis |
| Lead capture | Make.com webhook | Gratis (1000 op/mese) |
| Dominio | vision-v1.it | ~€10/anno |
| SSL | Let's Encrypt via Netlify | Gratis |

**Costo mensile stimato con 500 analisi/mese: ~€8-15**

---

## 🔮 Roadmap

- [ ] Integrazione Supabase per storico analisi
- [ ] Dashboard admin per vedere tutti i lead
- [ ] Report PDF automatico via email (Brevo)
- [ ] Analisi social reale (Instagram Graph API)
- [ ] Abbonamento mensile (Stripe)
- [ ] White label per agenzie

---

*Vision V1 · Bixont Marketing Agency · vision-v1.it*
