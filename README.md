# DIAMIR – KI-Schätzung

KI-gestütztes Aufwandsschätzungs-Tool für das DIAMIR Produktkonzeptionsteam.

## Deployment auf Vercel

### 1. Repo mit Vercel verbinden

1. Geh auf [vercel.com](https://vercel.com) und melde dich an (GitHub-Login empfohlen)
2. Klick **"Add New Project"**
3. Wähle dieses Repository (`PK_Schaetzung`) aus
4. Framework Preset: **"Other"** (kein Framework nötig)
5. Klick **"Deploy"** – Vercel erkennt die Struktur automatisch

### 2. Anthropic API-Key hinterlegen

Nach dem ersten Deploy (oder davor unter "Environment Variables"):

1. Im Vercel-Projekt → **Settings → Environment Variables**
2. Neue Variable anlegen:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** deinen API-Key von [console.anthropic.com](https://console.anthropic.com)
   - **Environment:** Production (+ Preview + Development wenn gewünscht)
3. **Redeploy** auslösen (Deployments → drei Punkte → Redeploy)

### 3. Fertig 🎉

Das Tool ist jetzt unter eurer Vercel-URL erreichbar (z. B. `pk-schaetzung.vercel.app`).  
Optional: Unter **Settings → Domains** eine eigene Domain vergeben.

---

## Projektstruktur

```
├── index.html      ← Das Tool (Frontend)
├── api/
│   └── claude.js   ← Serverless Proxy (hält den API-Key serverseitig)
└── vercel.json     ← Routing-Konfiguration
```

## Lokale Entwicklung

```bash
npm i -g vercel
vercel dev
```

Dann `ANTHROPIC_API_KEY` in einer `.env.local` Datei hinterlegen:
```
ANTHROPIC_API_KEY=sk-ant-...
```
