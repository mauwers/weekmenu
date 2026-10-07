# Eigen kopie van de Weekmenu-app maken

Met deze stappen krijg je een eigen Weekmenu-app met een eigen database.
Jouw gerechten en weekmenu's zijn volledig gescheiden van die van andere gezinnen.
Je hebt nodig: een GitHub-account en een Google-account. Reken op ongeveer 20 minuten.

## 1. Kopieer de app (GitHub)
1. Ga naar https://github.com/mauwers/weekmenu en log in.
2. Klik rechtsboven op **Fork** en daarna op **Create fork**.
   Je hebt nu een eigen kopie, bijvoorbeeld `jouwnaam/weekmenu`.

## 2. Maak een eigen database (Firebase)
1. Ga naar https://console.firebase.google.com en log in met je Google-account.
2. Klik op **Project maken**. Kies een naam, bijvoorbeeld `weekmenu-familie-jansen`. Google Analytics mag uit.
3. Kies in het menu links **Build → Firestore Database** en klik op **Database maken**.
   - Kies een locatie in Europa, bijvoorbeeld `eur3`.
   - Kies **Starten in productiemodus**.
4. Open het tabblad **Regels**, vervang de tekst door het volgende en klik op **Publiceren**:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /weekmenu/{doc} {
         allow read, write: if true;
       }
     }
   }
   ```
   Let op: iedereen die de link naar jouw app heeft, kan het menu zien en aanpassen.
   Deel de link dus alleen met je eigen gezin.
5. Klik linksboven op het tandwiel en kies **Projectinstellingen**.
   Klik onderaan bij "Je apps" op het **</>**-icoon (Web). Geef de app een naam en klik op **App registreren**.
   Je krijgt nu een blok `const firebaseConfig = { ... }` te zien. Laat dit scherm openstaan.

## 3. Pas `config.js` aan
1. Open in jouw GitHub-kopie het bestand `config.js` en klik op het potloodje om het te bewerken.
2. Vervang alles tussen `firebaseConfig = {` en `};` door de gegevens uit stap 2.5.
3. Zet bij `PERSONEN` de namen van jouw gezin, bijvoorbeeld:
   `["Sanne","Tom","Lotte","Allemaal"]`
4. Klik op **Commit changes**.

## 4. Zet de app online (GitHub Pages)
1. Ga in jouw kopie naar **Settings → Pages**.
2. Kies bij "Branch" **main** en **/ (root)**, en klik op **Save**.
3. Na 1 à 2 minuten staat je app op `https://jouwnaam.github.io/weekmenu/`.

## 5. Zet de app op je telefoon
- **iPhone (Safari):** open de link, tik op Deel (□↑) en kies **Zet op beginscherm**.
- **Android (Chrome):** open de link, tik op ⋮ en kies **App installeren** of **Toevoegen aan startscherm**.

Stuur dezelfde link naar je gezinsleden. Dan zien jullie allemaal hetzelfde menu en dezelfde boodschappenlijst.
De eerste keer staan er een paar voorbeeldgerechten in. Die kun je zelf aanpassen of verwijderen.
