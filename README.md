# pa7r1ck.io / DonMarco

Grundgerüst für Patricks persönliche Webseite mit **Next.js (App Router), React und TypeScript**. Die Startseite zeigt „pa7r1ck.io“ und „all you need“. Das Styling verwendet normales CSS.

## Lokal entwickeln

Benötigt Node.js 24 und npm. Mit installiertem nvm: `nvm install && nvm use`.

Im Repository-Verzeichnis:

```sh
npm ci
npm run dev
```

Die lokale Entwicklung läuft unter `http://localhost:3000`. Änderungen an den Komponenten werden automatisch übernommen.

## Projektstruktur

- `src/app/page.tsx`: Startseite; weitere Seiten erhalten eigene Ordner mit einer `page.tsx`.
- `src/app/layout.tsx`: gemeinsames Layout, Sprache und Metadaten.
- `src/app/globals.css`: grundlegendes Styling.
- `src/app/icon.svg`: Website-Icon.
- `next.config.ts`: Next.js-Konfiguration.

Komponenten sind standardmäßig Server Components. Für interaktive Komponenten mit State oder Browser-APIs wird gezielt `"use client"` verwendet. Imports über `@/` verweisen auf `src/`.

## Prüfen und Produktionsbetrieb

```sh
npm run lint
npm run typecheck
npm run build
npm start
```

`npm start` benötigt einen erfolgreichen Build und startet die Anwendung auf Port 3000. Die GitHub-Actions-Konfiguration führt Installation, Lint, Typprüfung und Build bei Pushes auf `main` sowie Pull Requests aus. Es gibt noch keine automatisierte Anwendungstestsuite.

## Hosting

Für diese Next.js-Anwendung bietet sich Vercel an: Repository importieren, Framework **Next.js**, Projektverzeichnis Repository-Wurzel, Build `npm run build`, Node.js 24.x. Vercel stellt eine eigene URL bereit; eine persönliche Domain kann später verbunden werden. Ein Deployment wurde durch dieses Setup noch nicht eingerichtet.

Die bisherige `index.html` und `.nojekyll` bleiben für die bestehende statische GitHub-Pages-Seite erhalten. GitHub Pages führt die Next.js-Anwendung nicht aus. Änderungen an `src/app/` werden dort daher nicht automatisch sichtbar. Nach dem Wechsel auf Vercel kann die alte HTML-Version entfernt und GitHub Pages deaktiviert werden.

## Später: privater Bereich

Anmeldung, Ausgabentracker und Supabase sind noch nicht implementiert. Das Grundgerüst benötigt keine Zugangsdaten. Der nächste Schritt ist ein Supabase-Projekt mit Auth und PostgreSQL sowie Zugriffsregeln für eure beiden Benutzerkonten. Datenzugriffe müssen durch serverseitige Authentifizierung und Datenbankregeln geschützt werden.

Lokale Zugangsdaten gehören in `.env.local` (von Git ignoriert), beim Hosting in dessen Umgebungsvariablen. Eine Supabase-Service-Role darf niemals im Browser oder in `NEXT_PUBLIC_*`-Variablen landen.
