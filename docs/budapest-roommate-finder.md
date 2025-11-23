# Budapest-albérlet- és szobatárs-kereső ötletterv

## Miért jó
- A Facebook-csoportokban szétszórtan jelennek meg az ajánlatok, nehezen kereshetők.
- Egy dedikált oldal jobb szűrőzést, értesítéseket és hitelesebb hirdetéseket tud adni.

## Célcsoportok és fő felhasználói utak
- **Lakót kereső bérlő**: saját szobájához vagy lakásához társat keres.
  - Hirdetés feladása → fotók és alapadatok megadása → publikálás → bejövő jelentkezők kezelése.
- **Szobát/Albérletet kereső**: találatokat böngész → szűr → elment → jelentkezik → üzen a hirdetőnek.

## Kulcsfunkciók
- **Keresés és szűrés**: kerületek, tömegközlekedési közelség (pl. metróvonalak), ár/hó, rezsi, beköltözési dátum, bútorozottság, dohányzás/állat, minimum bérleti idő.
- **Hirdetésfeladás**: fotók (több kép), alaprajz, szoba/lakás méret, közös költség, kaució, leírás, elérhetőség, preferált szobatárs jellemzők.
- **Értesítések**: mentett keresésekhez email/push értesítés új egyezésekre.
- **Üzenetküldés**: alap chat vagy email relay a privát adatok védelmére.
- **Hitelesítés / bizalom**: email- és telefonszám-verifikáció, opcióként személyi- vagy közműszámla-fotó hitelesítés.
- **Moderáció és fraud-védelem**: spam-szűrés, duplikált hirdetés felismerése, felhasználói jelentések kezelése.
- **Többnyelvűség**: HU/EN váltás, hogy expatok is tudják használni.

## Oldalstruktúra
- Nyitóoldal: kereső + kiemelt hirdetések.
- Találati lista: kártyák, térképes nézet (Budapest fókusz), szűrő panel.
- Hirdetés részlete: galéria, adatok, házirend, közlekedés, jelentkezés/üzenet gomb.
- Hirdetésfeladás wizard: több lépéses űrlap, valós idejű validáció.
- Profil: ellenőrzött jelvény, értékelések, aktív/archivált hirdetések.

## Adatmodell (vázlat)
- **User**: id, role (owner/seeker), name, contact, verification_status, languages, bio.
- **Listing**: id, user_id, title, description, district, address_hint, lat/lng, price_total, price_utilities, deposit, available_from, min_term_months, room_size, property_size, amenities, pets_allowed, smoking_allowed, photos.
- **SavedSearch**: user_id, filters (JSON), notification_channel.
- **Application/Message**: from_user, to_user, listing_id, status, thread.
- **Report**: reporter_id, listing_id, reason, status.

## Technológiai javaslat
- **Front-end**: Next.js + React, TypeScript, Tailwind/Chakra; mapshez Leaflet + OpenStreetMap.
- **Back-end**: Node.js (NestJS/Express) vagy Django FastAPI alternatívaként; GraphQL vagy REST.
- **Adatbázis**: PostgreSQL + PostGIS (keresés kerület/koordináta alapján), Redis a cache/queue-hoz.
- **Fájlkezelés**: S3-kompatibilis tárhely (pl. Wasabi), CDN képszolgálathoz.
- **Autentikáció**: email magic link + opcionális telefon OTP; JWT/Session.
- **Infra**: Docker-compose fejlesztéshez, CI-lint/test, staging környezet; Vercel/Render/Fly.io hosting.

## Roadmap (MVP → bővítés)
1. **MVP**: hirdetéslista + részletek, alap szűrők, hirdetésfeladás, email hitelesítés, egyszerű jelentkezés/üzenet továbbítás emailben.
2. **Keresési élmény**: térképes nézet, mentett keresések, értesítések.
3. **Bizalom**: verifikációs jelvények, moderációs eszközök, scam-szűrők.
4. **Growth**: fizetett kiemelések, megosztás, referral, analitika.

## Mérőszámok
- Idő az első releváns találatig, jelentkezésig, és az egyezésig.
- Moderációs jelzések aránya, válaszidők.
- Aktív hirdetések száma kerületenként, konverziós arány jelentkezésből chatbe.

## Következő lépések fejlesztéshez
- Hozz létre Next.js + NestJS alapú monorepót (turbo), CI-lint/test workflow-val.
- Definiáld a Listing/User API-sémát (OpenAPI/GraphQL) és írj contract testeket.
- Készíts drótvázakat (Figma) a keresőre, listára, wizardra és profilra.
- Indíts kis mennyiségű „seedelt” hirdetést moderálható admin felülettel.
