# Budapest albérlet- és szobatárs-kereső ötletterv

Ez a repó egy Budapest-központú szobatárs/albérlet kereső weboldal koncepcióját gyűjti össze. Részletesebb funkció- és technológiai ötletek a [`docs/budapest-roommate-finder.md`](docs/budapest-roommate-finder.md) fájlban olvashatók.

## Gyors indítás (alap statikus oldal)

Az egyszerűen kipróbálható kezdőoldal a `docs` mappában található. Bármely modern böngészővel megnyitható, vagy egy minimális webszerverrel futtatható.

1. **Repo klónozása**
   ```bash
   git clone https://github.com/<felhasznalo>/codex.git
   cd codex/docs
   ```
2. **Oldal megnyitása**
   - Közvetlenül: duplakatt a `index.html` fájlra, majd nyisd meg böngészőben.
   - Vagy indíts mini szervert (például Python 3-mal):
     ```bash
     python -m http.server 8000
     ```
     Ezután látogasd meg: [http://localhost:8000](http://localhost:8000)

## GitHub Pages használat

1. Pushold a repót a saját GitHub-fiókodba.
2. A repo **Settings → Pages** menüjében forrásnak állítsd be a `main` branchet és a `/docs` mappát (ezt a GitHub Pages alapértelmezésben kínálja fel).
3. Ha inkább a gyökérmappát használnád forrásnak, hagyd a fájlokat a repo gyökerében, vagy másold át oda a `docs` tartalmát (és válaszd a `/(root)` opciót).
4. Mentés után pár perc múlva elérhető lesz az oldal a GitHub által generált URL-en.
