# Fejlesztési roadmap – Budapest szobatárs és albérlet összekötő

Az oldal két fő felhasználói útvonalra épül: aki már rendelkezik lakással és társat keres, illetve aki szobát/albérletet keres, ahová beköltözhet. A roadmap az MVP-től a bővített verziókig vezet, kiemelve a lépéseket, amik a két szereplőt gyorsan összehozzák.

## 1. Információs alap (statikus landing)
- Két szerep ("van lakás" / "szobát keres") egyértelmű bemutatása, külön CTA-kkal.
- Mintalisták a kínált szobákra és a szobát kereső profilokra.
- Alap stílus és reszponzív grid, hogy GitHub Pages-en is jól jelenjen meg.

## 2. Keresés és szűrés MVP
- Frontend: Next.js (App Router) + TypeScript, Tailwind; statikus adatokkal induló listaoldal és részletnézet.
- Szűrők: kerület, max ár, beköltözési dátum, dohányzás/állat opciók; client-side szűrés az első körben.
- Form state és validáció: React Hook Form vagy tanús TypeScript típusok.

## 3. Alapszintű backend és hitelesítés
- API: REST vagy GraphQL v1 `Listing` és `Profile` végpontokkal (NestJS vagy FastAPI ajánlott).
- Auth: e-mail alapú magic link / OTP, JWT-s session-kezelés.
- Perzisztencia: PostgreSQL séma alap (User, Listing, Application/Message), seed adatok fejlesztéshez.

## 4. Közvetlen kapcsolatfelvétel és értesítések
- Üzenetküldés: kezdetben e-mail relay vagy webhook → inbox, később real-time chat (WebSocket/Ably/Pusher).
- Mentett keresések és e-mail/push értesítések új egyezéseknél.
- Moderáció: bejelentés, spam-szűrés (pl. egyszerű rate-limit, kulcsszófilter), verifikációs jelvények.

## 5. Térképes élmény és bizalomépítés
- Térképes keresés (Leaflet + OpenStreetMap, PostGIS a backend oldalon), heatmap a kerületi eloszlásra.
- Fotóvalidáció és közműszámla/személyi feltöltés opció a hirdetőknek.
- Ajánlott szobatárs profil (kereslet-kínálati matching alap preferenciák szerint).

## 6. Bevételek és üzemeltetés
- Kiemelések és promó spotok (pl. top of list / kiemelt kártyák), kuponok induláshoz.
- CI/CD: lint + test pipeline, staging deploy (Render/Fly/Vercel), alap megfigyelés (uptime, error monitoring).
- Analitika: alap event tracking (keresés, mentés, jelentkezés), funnel riportok.

## 7. Ütemezés javaslat (hetek)
- **Hét 1–2**: statikus landing + mintalisták, Next.js skeleton, design tokenek.
- **Hét 3–4**: kereső és részletoldal statikus adatokkal, alap szűrők és validáció.
- **Hét 5–6**: backend alap, auth, listázás + részlet API, seed adatok, e-mail relay.
- **Hét 7–8**: értesítések, moderáció, térképes nézet alfa, verifikációs badge-ek.
- **Hét 9+**: fizetett kiemelések, analitika, scaling és finomhangolás.
