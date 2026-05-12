# Konsolideeritud mittefunktsionaalsed nõuded (kandidaat)

See dokument ühendab nõuded järgmistest allikatest:
- **cfr.md** – hetkel kehtivad ristfunktsionaalsed nõuded (vt. https://koodivaramu.eesti.ee/e-gov/cfr )
- Ühised nõuded mis esinevad vähemalt kahes erinevas MFN/RFN dokumendis.

**Nõudetaseme nimetused:**
- **required** – kohustuslik
- **expected** – oodatav
- **recommended** – soovituslik
- **draft** – mustand

---

## 1. Kodeering ja vorming

### 1.1 UTF-8 kodeering

**Nõue:** Andmebaasid, rakendused, SQL skriptid ja lähtekood peavad kasutama UTF-8 kodeeringut. UTF-16 või UTF-32 on soovitatavad, eriti kui on vajadus talletada emotikone.
**Nõudetase:** required

---

### 1.2 Ajavorming

**Nõue:** Kuupäeva ja aja esitamisel kasutada ISO 8601 või RFC 3339 vorminguid. Ajatemplid tuleb esitada UTC-s.
**Nõudetase:** required

---

## 2. Kasutajaliides ja ligipääsetavus

### 2.1 Juurdepääsetavus

**Nõue:** Avalikud kasutajaliidesed peab vastama WCAG 2.2 tasemele AA (juurdepääsetavus). 
**Nõudetase:** required
>> karbitoodetele kehtestada erand + EN standard ?
---

### 2.2 HTML5 ja CSS3 standardid

**Nõue:** Veebipõhine kasutajaliides peab ühilduma standarditega HTML 5 ja CSS 3.
**Nõudetase:** required

---

### 2.3 Brauserite tugi

**Nõue:** Kasutajaliides peab töötama veebibrauserites, mis toetavad eID baastarkvara kaht viimast versiooni.
**Nõudetase:** required

---

### 2.4 Veateadete kuvamine

**Nõue:** Rakendus asendab vaikimisi veateate lehekülje kuid säilitab algse HTTP vastuskoodi. Veateated peavad olema arusaadavad ja kasutajasõbralikud, ilma liigse tehnilise infota.
**Nõudetase:** required

---

### 2.5 E-riigi disainisüsteem

**Nõue:** Kasutajaliides kasutab e-riigi disainisüsteemi ja valmiskomponente raamistikku TEDI (https://www.tedi.ee/). Uute raamistike ja komponentide loomisel on tagasipanustamine oodatud. Masingenerereeritud arendusmudeli puhul lähtuda TEDI stiiliraamatust.Nõue kehtib lõpptarbijatele suunatud avalikele teenustele. Karbitoodete erisus on lubatud.
**Nõudetase:** expected

---

### 2.6 Kasutajaliidese masinasõbralikkus

**Nõue:** Avalike teenuste puhul tagada nende kättesaadavus ka masinasõbralikus formaadis (näiteks MD) ja/või MCP protokolli kasutades. 
**Nõudetase:** expected

---

## 3. Turvalisus

### 3.1 TLS/HTTPS krüpteerimine

**Nõue:** Kliendi ja serveri vaheline suhtlus peab olema krüpteeritud (TLS 1.3 või uuem). Nõue kehtib ka sisevõrkude rakenduste ja tehniliste komponentide vahelise suhtluse kohta.
**Nõudetase:** required

---

### 3.2 OWASP soovituste järgimine

**Nõue:** Rakendus peab läbinud enne toodangusse minemist turvatestimise. Veebirakendused arendada ja testida vastavalt OWASP ASVS tase 2 soovitustele.
Lähtuda viimasest stabiilsest versiooni. 
**Nõudetase:** required

---

### 3.3 Paroolide ja saladuste turvaline salvestamine

**Nõue:** Paroolid ja saladused peavad olema räsitud, soolatud; ei tohi olla cleartext ega hardcoded. Kasutada keskset saladuste hoidlat (nt. Vault). Privaatvõtmeid, salasõnu ja muud sensitiivset ei talletata koodihoidlas ega veebidokumentides.

**Nõudetase:** required

---

### 3.4 Sessiooni aegumine

**Nõue:** Rakendusel peab olema konfigureeritav kasutajasessiooni aegumise aeg. Sessioon peab serveri poolel lõppema. Seansi identifikaator peab olema piisava pikkusega, juhuslik ja unikaalne kogu aktiivse seansi jooksul.
**Nõudetase:** required

---

### 3.5 Krüptograafia

**Nõue:** Krüptoalgoritmite ja räsifunktsioonide kasutamisel tuleb järgida RIA krüptograafiliste algoritmide elutsükli uuringut. Krüptoalgoritmi oodatav eluiga peab olema pikem kui rakenduse planeeritud eluiga. TODO: masinloetavasse liidesesse tuua loend turvalistest algoritmidest.
**Nõudetase:** required

---

### 3.6 Sisendi ja väljundi valideerimine

**Nõue:** Kasutaja ja rakenduste sisendit kontrollitakse ja puhastatakse vastu rakenduse ootusi. Väljundit tuleb alati puhastada ja filtreerida enne kasutamist (sh kasutajaliideses).
**Nõudetase:** required

---

### 3.7 URL ja sessioon

**Nõue:** URL ei tohi sisaldada isikuandmeid või sessioonivõtit.
**Nõudetase:** required

---

### 3.8 X-tee ja andmebaas – arhitektuur

**Nõue:** Esitluskiht on andmekihist täielikult isoleeritud. Esitluskihist ei tohi teha otsepäringuid x-tee teenuste ja andmebaasi poole.
**Nõudetase:** required

---

### 3.9 E-ITS

**Nõue:** Infosüsteem peab olema arendatud mimimaalselt kooskõlas E-ITS suure kaitsetarbe nõuetele kui ei ole määratud teisiti.
**Nõudetase:** required

---

## 4. Andmebaas

### 4.1 Primaarvõti (surrogaatvõti)

**Nõue:** Igas andmebaasi tabelis peab olema tehniline primaarvõti (surrogaatvõti). Ärivõtmeid ei tohi kasutada primaarvõtmena.
**Nõudetase:** required

---

### 4.2 Välisvõtmed indekseeritud

**Nõue:** Kõik välisvõtmed (foreign keys) peavad olema indekseeritud.
**Nõudetase:** required

---

### 4.3 Päringumuutujad

**Nõue:** SQL päringute puhul tuleb kasutada päringumuutujaid (Parameter Binding), mitte konstantidena sisse kirjutatud väärtusi.
**Nõudetase:** required

---

### 4.4 Andmebaasi migratsioonid

**Nõue:** Andmebaasi skeemi muudatused tuleb versioneerida ja automatiseerida migratsioonivahenditega.
**Nõudetase:** required

---

### 4.5 Kahekohaline andmebaasikasutaja

**Nõue:** Andmebaasidel peab olem olema rakendatud vähemalt kaks erineva õigustetaset (baasi, skeemi haldamise õigused vs. rakenduse toimetamise õigused). Rakenduste andmebaasikontod peavad omama minimaalseid õiguseid.
**Nõudetase:** expected

---

### 4.6 Äriloogika andmebaasis

**Nõue:** Andmebaas ei tohi sisaldada äriloogikat (triggerid, protseduurid jms).
**Nõudetase:** expected

---

### 4.7 Loogiline kustutamine ja versioneerimine

**Nõue:** Andmete kustutamine peaks olema loogiline (kustutamise lipuga) või obfuskeerimine. Unikaalseid ID väärtuseid ei taaskasutata. E-ITS kõrgema kaitsetarbega infosüsteemide puhul tuleb kirjed versioneerida.
**Nõudetase:** expected

---

## 5. Logimine

### 5.1 Audit-logi nõuded

**Nõue:** Rakenduse tarkvara tööd logitakse ning audit-logi talletatakse rakendusest ja selle baasist eraldi. Logima peab õnnestunud ja ebaõnnestunud sisselogimiskatsed, ligipääs logiandmetele, rakenduse töö katkemine, rakenduse administreerimistegevused, süsteemsed muudatused konfiguratsioonis, andmetöötlus ja seotud manipulatsioonid. Logitakse aeg, kontekst (kes, kus, mida, mis tulemusega) ja kategooria (DEBUG, INFO, WARNING, ERROR, FATAL). DEBUG kategooria talletamine toodangu keskkonnas pole kohustuslik.
**Nõudetase:** required

---

### 5.2 Logides ei tohi olla tundlikke andmeid

**Nõue:** Logidesse ei tohi salvestada paroole, sessioonivõtmeid (va trace id), isikuandmeid ega muid tundlikke andmeid.
**Nõudetase:** required

---

### 5.3 Struktureeritud logimine

**Nõue:** Logimine peab olema struktureeritud (JSON formaat). Logikirjete sisu vastab standardile (OpenTelemetry, ECS).
**Nõudetase:** required

### 5.4 Logide säilitamine
**Nõue:** Logisi säilitada minimaalselt 1 aasta, soovitatavalt 3 aastat.
**Nõudetase:** expected

---

## 6. Monitooring ja health check

### 6.1 Masinloetavad elusoleku ja valmisoleku kontrollid

**Nõue:** Rakendusel peavad olema realiseeritud elusoleku ja valmisoleku kontrollid, eelistatult JSON formaadis. Toodangu keskkondades on rakendused automaatselt monitooritud.
**Nõudetase:** required

---

## 7. Konfiguratsioon

### 7.1 Rakenduseväline konfiguratsioon

**Nõue:** Konfiguratsioon (sh paroolid) ei ole osa tarkvara koodist vaid paigaldatakse keskkonnamuutujate kaudu.
**Nõudetase:** required

---

### 7.2 Dubleerivate parameetrite vältimine

**Nõue:** Konfiguratsioonis ei tohi olla sisult dubleerivaid parameetreid. Sama parameeter ainult ühes kohas.
**Nõudetase:** required

---

## 8. Koodi kvaliteet ja testimine

### 8.1 Staatiline koodianalüüs

**Nõue:** Kood peab läbima staatilise koodianalüüsi (nt. SonarQube). Ei tohi esineda kriitilisi ja kõrgemaid probleeme. Rakendus ei lähe toodangusse, kui selles on avastatud turvalisuse nõrkusi või haavatavusi.
**Nõudetase:** required

---

### 8.2 Automaattestid ja code review

**Nõue:** Kasutajafunktsionaalsus peab olema kaetud automaattestidega. Sisemised funktsioonid peavad olema kaetud 80% ulatuses testidega. Toodangusse ei lähe kood, mille testid ebaõnnestuvad. Kood peab olema läbinud koodi ülevaatuse (code review) minimaalselt paarisprogrammeerimise printsiibil.
**Nõudetase:** required

---

### 8.3 Koormustestid

**Nõue:** Rakendused on läbinud koormustestid vähemalt kahekordse eeldatava kasutajate mahuga enne toodangusse minekut. Piiratud sisekasutusega rakenduse puhul ei ole nõue kohustuslik.
**Nõudetase:** required

---

### 8.4 Lähtekood inglise keeles

**Nõue:** Lähtekood, kommentaarid ja logiteated peavad olema inglise keeles (v.a. kasutajale näidatud teated, mida tuleb realiseerida tõlkefailidega).
**Nõudetase:** required

---

## 9. API ja dokumentatsioon

### 9.1 OpenAPI / Swagger spetsifikatsioon

**Nõue:** REST API-d peavad olema dokumenteeritud OpenAPI (Swagger) spetsifikatsioonis. Tehniliste komponentide API-del eksisteerib automaatselt genereeritud dokumentatsioon.
**Nõudetase:** required

---

### 9.2 API versioneerimine

**Nõue:** API-d peavad toetama versioneerimist (URL-is v1, v2 vms). Vanade versioonide tugi minimaalselt 6–12 kuud. REST API URL kujul /api/[versioon]/[ressurss]/[id]. Idempotentsus, Cache-Control tugi.
**Nõudetase:** required

---

### 9.3 MCP protokolli tugi

**Nõue:** Masinasõbralikud liidesed peava järgima  MCP protokolli spetsifikatsiooni (vt. https://github.com/modelcontextprotocol)).
**Nõudetase:** required

---

## 10. Arhitektuur

### 10.1 Autentimine ja identiteet

**Nõue:** Avalike teenuse puhul peab lasutajate autentimine käima läbi TARA teenuse. Rakendus ei tohi luua uut identiteedisüsteemi. Tuleb tugineda olemasolevatele riiklikele või asutuse põhisüsteemidele (ldap/kerberos). 
**Nõudetase:** required

### 10.1.1 Ristkasutatavad teenused

**Nõue:** Ristkasutatavatel avalikel teenus rakendada riiklik SSO (GOVSSO), kaaluda. isemiselt rakendada JWT, OAuth rakendamist teenuste/teenuskomponentide vahel.
**Nõudetase:** expected
---

### 10.2 Autoriseerimine

**Nõue:** Rakenduse tehnilised komponendid kaitsevad iseennast ja valideerivad kasutaja või tehnilise teenuse õigusi. Autoriseerimine on rakenduste enda tagada.
**Nõudetase:** expected

---

### 10.3 X-tee ja andmevahetus

**Nõue:** Asutuste vaheline infosüsteemide vaheline andmevahetus toimub üle X-tee. X-tee päringud realiseeritakse serveri poolel, mitte kasutajaarvutist.
**Nõudetase:** required

---

### 10.4 Eessüsteem ja tagasüsteem eraldatud

**Nõue:** Eessüsteemid ja tagasüsteemid peavad olema arhitektuuriliselt selgelt lahutatud. Kasutajaliides ja teenuse funktsionaalsus on loogiliselt eristatud kihid ja suhtlevad üle API.
**Nõudetase:** required

---

### 10.5 Domeenipõhine disain

**Nõue:** Rakendused on disainitud domeenist juhinduva disaini (https://en.wikipedia.org/wiki/Domain-driven_design) ja 12F arhitektuuri põhimõtteid jälgides (vt. https://12factor.net/).
**Nõudetase:** expected

---

### 10.6 REST API ja olekuta teenused

**Nõue:** Tehnilised komponendid avaldavad REST API. Kasutajaliidese olekut hoitakse kliendi poolel; teenused on olekuta (stateless).
**Nõudetase:** expected

---

### 10.7 Pilvekõlbulikkus ja hajuskomponendid

**Nõue:** Rakendus on pilvekõlbulik: skriptiga paigaldatav, koosneb mitmest sõltumatust instantsist, on automaatselt skaleeritav, andmed varundatud. Hajuskomponendid ei jaga sama andmebaasi, mälu ega failisüsteemi. Kõik andmed mida on vaja talletada pikemalt, peavad olema talletatud teenuse instantsidest väljaspool.
**Nõudetase:** expected

---

### 10.8 Korrelatsiooni ID

**Nõue:** Tehnilised komponendid logivad või genereerivad korrelatsiooni ID. Korrelatsiooni ID saadetakse iga edasise päringuga kaasa (nt X-Correlation-ID).
**Nõudetase:** draft
>> Visata välja.
---

### 10.9 Rakendusserver eraldi andmebaasiserverist

**Nõue:** Rakendusserver peab võimaldama töötamist andmebaasiserverist eraldi serveril/konteineris.
**Nõudetase:** required

---

### 10.10 Konfiguratsioonifailid on kaitstud

**Nõue:** Konfiguratsioonifailid peavad olema kaitstud. Muutmine on lubatud ainult administraatoritel.
**Nõudetase:** required

---

## 11. Arendus ja juurutus

### 11.1 Versioneerimine

**Nõue:** Rakenduse kood on versioneeritud kasutades Git'i. Kogu lähtekood tuleb tarnida hajusversioonihalduse süsteemi (Git) kaudu.
**Nõudetase:** required

---

### 11.1.1 Kohapealne puhver

**Nõue:** Rakenduse ehitamiseks vajalikud välised sõltuvused peavad olema peegeldatud kohalikesse repositooriumitesse.
**Nõudetase:** expected

---


### 11.2 Koodi selgus

**Nõue:** Lähtekood on kirjutatud selgusega, mis võimaldab uuel arendajal süsteemi edasi arendada. Lähtuda Clean Code printsiibist.
**Nõudetase:** required

---

### 11.3 Taaskasutus

**Nõue:** Taaskasutatavalt disainitud kood on e-riigi koodivaramus (koodivaramu.eesti.ee)
**Nõudetase:** recommended

---

### 11.4 Programmeerimiskeeled ja komponentide EOL

**Nõue:** Arenduses ei kasutata programmeerimiskeeli väljaspool Top 25 TIOBE index'it (https://www.tiobe.com/tiobe-index/). Kõikide komponentide eluea lõpp (EOL) ei tohi olla lähemal kui 5 aastat.
**Nõudetase:** expected

---

### 11.5 Litsents

**Nõue:** Tarkvara tuleb markeerida litsentsiga (LICENCE-fail või faili päis). Riik eelistav vaba litsentsi kasutamist (soovitus: MIT, alternatiiv EUPL).
**Nõudetase:** required

---

### 11.6 Taasteplaanid

**Nõue:** Teenuse rakendustele eksisteerivad ajakohased taasteplaanid, eelistatult automatiseeritult toimivad.
**Nõudetase:** required

---

### 11.7 CI/CD ja automatiseerimine

**Nõue:** Keskkondadesse tarkvara paigaldamine on automatiseeritud (Gitlab CI, Jenkins jms). Soovitatav on kasutada blue-green juurutusmustrit.
**Nõudetase:** required

---

### 11.8 Semantiline versioneerimine

**Nõue:** Rakendus on versioneeritud semantilise versioneerimise põhimõtte järgi (A.B.C). Lisainfo: https://semver.org/
**Nõudetase:** expected

---

### 11.9 Vastupanuvõime

**Nõue:** Rakendus peab olema väliste süsteemide tõrgete suhtes vastupanuvõimeline (resilient). Välise süsteemi tõrge tohib mõjutada ainult otseselt sõltuvaid kasutuslugusid.
**Nõudetase:** required
>> TODO: lisame juurde näited, viited.

---

### 11.10 Kasutuslood

**Nõue:** Süsteemi funktsionaalne skoop on defineeritud ja dokumenteeritud selgesõnaliste kasutuslugudega.
**Nõudetase:** required

---

## 12. Andmekvaliteet ja standardid

### 12.1 Aadressiandmete süsteem

**Nõue:** Aadressiandmete käitlemisel lähtuda määrusest "Aadressiandmete süsteem" (https://www.riigiteataja.ee/akt/118062021032?leiaKehtiv)
**Nõudetase:** required

---

### 12.2 Klassifikaatorid ja EMTAK

**Nõue:** Tegevusalade andmete puhul kasutada EMTAK klassifikaatorit (https://www.rik.ee/et/e-ariregister/emtak-tegevusalad)  või määruse "Klassifikaatorite süsteem" (vt. https://www.riigiteataja.ee/akt/12910889) nõudeid. 
>> Levitustes kasutatakse riigis kokku lepitud klassifikaatoreid (kas on vajalik?)
**Nõudetase:** required

---

### 12.3 Objektide identifitseerimine

**Nõue:** Objektid identifitseeritakse registrikoodide abil (https://www.riigiteataja.ee/akt/123122022024?leiaKehtiv). Isikud isikukoodiga rahvastikuregistrist (https://www.riigiteataja.ee/akt/128062019037?leiaKehtiv).
**Nõudetase:** required

---

### 12.4 Andmejälgija

**Nõue:** Infosüsteemide ja andmekogude juures kasutatakse RIA andmejälgijat kooskõlas kehtivate nõuetega, vt. https://github.com/e-gov/AJ
**Nõudetase:** required  

---

### 12.5 Andmekvaliteedi mudel

**Nõue:** Infosüsteemile peab rakendama andmekvaliteedi mudelit (täielikkus, ajakohasus, õigsus, reeglipärasus, ühekordsus). Kvaliteedi mõõtmise tulemused on väljavõetavad.
**Nõudetase:** expected

---

### 12.6 Andmete eksport

**Nõue:** Andmeid saab eksportida masin- ja inimloetavas vormingus (nt. JSON, CSV). Masintöödeldavad andmed on struktureeritud. Soovitav on luua eksportdivõimekus läbi API.
**Nõudetase:** required

---

 ### 12.7  Avaandmete teabevärav

**Nõue:** Infosüsteemile on koostatud andmekirjeldused, mis on avalikustatud Avaandmete teabeväravas.
Andmekirjelduste loomisel ja nende teabeväravasse edastamiseks saab kasutada RIHAKE'se rakendust või suhelda otse API liidesega.

**Nõudetase:** required  


## 13. Versioneerimine ja tarne

### 13.1 Muudatuste kirjeldus (Changelog)

**Nõue:** Iga uue versiooniga peab kaasas olema muudatuste kirjeldus (Changelog või release notes).
**Nõudetase:** required

---

## 14. Dokumentatsioon

### 14.1 Dokumentatsioon eesti keeles

**Nõue:** Lõppkasutajatele ja avalikkusele suunatud dokumentatsioon peab olema kirjutatud eesti keeles.
**Nõudetase:** required

---

## 15. Turvalisus – täiendavad nõuded

### 15.1 WAF reeglid

**Nõue:** Arenduse käigus luua WAF reeglid, vt. https://owasp.org/www-community/Web_Application_Firewall,kui WAF on kasutusel, tuleks alati ikka pruukida.

**Nõudetase:** recommended

---

### 15.2 Mitmikautentimine
**Nõue:** Kohtades, kus rakendatakse mitmikautentimist,laieneb sama kohustus ka administratiivsetele funktsioonidele.
**Nõudetase:** required

---

## Kokkuvõte
Nõuded pärinevad järgmistest allikatest:
**Allikad:**
- `cfr.md` – Kehtiva ristfunktsionaalsed nõuded (vt. https://koodivaramu.eesti.ee/e-gov/cfr)
- asutuste mittefunktsionaalsed nõuded
