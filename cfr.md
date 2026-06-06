# Konsolideeritud mittefunktsionaalsed nõuded (kandidaat)

See dokument ühendab nõuded järgmistest allikatest:

- cfr.md – hetkel kehtivad ristfunktsionaalsed nõuded (vt. <https://koodivaramu.eesti.ee/e-gov/cfr> )
- Ühised nõuded mis esinevad vähemalt kahes erinevas MFN/RFN dokumendis.

Nõudetaseme nimetused:

- **required** – kohustuslik
- **expected** – oodatav
- **recommended** – soovituslik
- **draft** – mustand
- **deprecated** – eemaldamisele

---

## 1. Kodeering ja vorming

### 1.1 UTF-8 kodeering

**Nõue:** Andmebaasid, rakendused, SQL skriptid ja lähtekood peavad kasutama UTF-8 kodeeringut. UTF-16 või UTF-32 on soovitatavad, eriti kui on vajadus talletada emotikone.

**Nõudetase:** required

**Põhjendus:** [Unicode](https://en.wikipedia.org/wiki/Unicode) UTF-8 on riigi infosüsteemide üldine kodeeringustandard; tagab eesti keele, erimärkide ja emoji ühilduvuse andmebaaside, API-de ja lähtekoodi vahel.

---

### 1.2 Ajavorming

**Nõue:** Kuupäeva ja aja esitamisel kasutada ISO 8601 või RFC 3339 vorminguid. Ajatemplid tuleb esitada UTC-s.

**Nõudetase:** required

**Põhjendus:** [ISO 8601](https://www.w3.org/TR/NOTE-datetime) / [RFC 3339](https://tools.ietf.org/html/rfc3339) tagab kuupäeva-aja ühtse esituse andmevahetuses, logides ja API-des; UTC ajavöönd välistab suve-/talveaja segaduse hajussüsteemides.

---

## 2. Kasutajakogemus ja juurdepääsetavus

### 2.1 Juurdepääsetavus

**Nõue:** Avalikud kasutajaliidesed peab vastama WCAG 2.2 tasemele AA (juurdepääsetavus).
Karbitoodetel eelistada lahendusi, kus nõuetele vastavus on kasvõi minimaalses mahus tagatud.

**Nõudetase:** required

**Põhjendus:** [Web Content Accessibility Guidelines](https://www.w3.org/TR/WCAG22/) 2.2 taseme AA; [EN 301 549](https://www.etsi.org/deliver/etsi_en/301500_301599/301549/03.02.01_60/en_301549v030201p.pdf); riigi avalike teenuste ligipääsetavuse kohustus ([RT](https://www.riigiteataja.ee/akt/105032019027?leiaKehtiv)).

---

### 2.2 HTML5 ja CSS3 standardid

**Nõue:** Veebipõhine kasutajaliides peab ühilduma standarditega HTML 5 ja CSS 3.

**Nõudetase:** required

**Põhjendus:** [HTML5](https://html.spec.whatwg.org/) ja [CSS3](https://www.w3.org/Style/CSS/) tagavad brauseriteülene ühilduvuse, pikaajalise toetuse ja valideeritavuse (W3C validator).

---

### 2.3 Brauserite tugi

**Nõue:** Kasutajaliides peab töötama veebibrauserites, mis toetavad eID baastarkvara kaht viimast versiooni.

**Nõudetase:** required

**Põhjendus:** Kehtiv eID baastarkvara toepoliitika: minimaalselt Edge, Chrome, Firefox, Safari viimased versioonid.

---

### 2.4 Veateadete kuvamine

**Nõue:** Rakendus asendab vaikimisi veateate lehekülje kuid säilitab algse HTTP vastuskoodi. Veateated peavad olema arusaadavad ja kasutajasõbralikud, ilma liigse tehnilise infota.

**Nõudetase:** required

**Põhjendus:** Kasutajakogemus ja infoturve — arusaadavad veateated ilma süsteemiinfota; HTTP vastuskoodi säilitamine toetab monitooringut ja API kliente.

---

### 2.5 E-riigi disainisüsteem

**Nõue:** Kasutajaliides kasutab e-riigi disainisüsteemi ja valmiskomponente raamistikku TEDI (<https://www.tedi.ee/>).
Uute raamistike ja komponentide loomisel on tagasipanustamine oodatud.
Masingenerereeritud arendusmudeli puhul lähtuda TEDI stiiliraamatust.
Nõue kehtib lõpptarbijatele suunatud avalikele teenustele.
Karbitoodete erisused on lubatud.

**Nõudetase:** expected

**Põhjendus:** [TEDI](https://www.tedi.ee/) / [TEDI Design System](https://github.com/TEDI-Design-System) tagab riigi avalike teenuste visuaalse ja interaktsioonilise ühtluse; vähendab arenduskulu ja kasutajakogemuse killustatust.

---

### 2.6 Kasutajaliidese masinasõbralikkus

**Nõue:** Avalike teenuste puhul tagada nende kättesaadavus ka masinasõbralikus formaadis (näiteks MD) ja/või MCP protokolli kasutades.

**Nõudetase:** expected

**Põhjendus:** Masinloetav sisujuht (nt Markdown) ja [Model Context Protocol](https://modelcontextprotocol.io/) toetavad automatiseeritud teenuste tarbimist, tehisaru agendi integratsiooni ja avalike andmete taaskasutust.

---

### 2.7 Nutiseadmetega arvestamine

**Nõue:** Veebirakenduse kasutajaliides on kasutatav nutiseadmetel (responsive design). Kriitilised funktsioonid on kasutatavad väikese ekraaniga seadmetel.

**Nõudetase:** expected

**Põhjendus:** Mobile-first; [Web Content Accessibility Guidelines](https://en.wikipedia.org/wiki/Web_Content_Accessibility_Guidelines); User experience.

---

### 2.8 Klaviatuuri navigatsioon

**Nõue:** Kogu kasutajaliides on täielikult kasutatav klaviatuuri abil ilma hiireta. Fookuse järjekord on loogiline ja nähtav (WCAG AA osa).

**Nõudetase:** required

**Põhjendus:** [Web Content Accessibility Guidelines](https://en.wikipedia.org/wiki/Web_Content_Accessibility_Guidelines) 2.2; Keyboard accessibility; Screen reader support.

---

### 2.9 Vähendatud liikumine (reduced motion)

**Nõue:** Rakendus võtab arvesse kasutaja eelistust vähendatud animatsioonide suhtes (prefers-reduced-motion). Animatsioonidega sisu võib alternatiivina olla staatiline.

**Nõudetase:** recommended

**Põhjendus:** [Web Content Accessibility Guidelines](https://en.wikipedia.org/wiki/Web_Content_Accessibility_Guidelines) 2.2; Accessibility; Vestibular disorders.

---

### 2.10 Tumereziimi tugi (dark mode)

**Nõue:** Rakendus toetab tumereziimi.

**Nõudetase:** recommended

**Põhjendus:** [Web Content Accessibility Guidelines](https://www.w3.org/TR/WCAG22/) kasutajaeelistused (`prefers-color-scheme`); kasutajakogemus öises kasutuses ja väsimuse vähendamine.

---

## 3. Turvalisus

### 3.1 Turvalised HTTP-päised

**Nõue:** Rakendus kasutab turvalisi HTTP-päiseid, näiteks Content-Security-Policy (CSP), X-Content-Type-Options, X-Frame-Options, Strict-Transport-Security (HSTS), Referrer-Policy.

**Nõudetase:** required

**Põhjendus:** [OWASP](https://en.wikipedia.org/wiki/OWASP) Secure Headers; [Content Security Policy](https://en.wikipedia.org/wiki/Content_Security_Policy); veebirakenduste turvalisus.

---

### 3.2 CSRF kaitse

**Nõue:** State-changing päringud on kaitstud CSRF (Cross-Site Request Forgery) vastu. Kasutatakse CSRF tokeneid või SameSite küpsiseid.

**Nõudetase:** required

**Põhjendus:** [OWASP](https://en.wikipedia.org/wiki/OWASP) Top 10; [Cross-site request forgery](https://en.wikipedia.org/wiki/Cross-site_request_forgery).

---

### 3.3 Sõltuvuste haavatavuste skaneerimine

**Nõue:** Rakenduse sõltuvused (teegid, konteinerid) skaneeritakse regulaarselt haavatavuste osas (nt Dependabot, Snyk, Trivy). Kõrge ja keskmise tasemega haavatavused lahendatakse enne toodangusse minekut.

**Nõudetase:** required

**Põhjendus:** [OWASP](https://en.wikipedia.org/wiki/OWASP); Software Supply Chain Security; NIST SSDF.

---

### 3.4 SBOM (Software Bill of Materials)

**Nõue:** Rakenduse kohta on koostatav masinloetav komponentide loend (SBOM), nt SPDX või CycloneDX formaadis. SBOM on saadaval iga väljastatud rakenduse versiooni kohta.

**Nõudetase:** required

**Põhjendus:** [Software bill of materials](https://en.wikipedia.org/wiki/Software_bill_of_materials); NTIA; CISA; Software Supply Chain Security.

---

### 3.5 TLS/HTTPS krüpteerimine

**Nõue:** Kliendi ja serveri vaheline suhtlus peab olema krüpteeritud (TLS 1.3 või uuem). Nõue kehtib ka sisevõrkude rakenduste ja tehniliste komponentide omavahelise suhtluse kohta.

**Nõudetase:** required

**Põhjendus:** [Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security) 1.3; konfidentsiaalsus ja terviklus kliendi-serveri ja komponentidevahelises suhtluses; [E-ITS](https://eits.ria.ee/) krüpteerimismeetmed.

---

### 3.6 Turvatestimine

**Nõue:** Rakendus peab läbinud enne toodangusse minemist turvatestimise.
Veebirakendused arendada ja testida vastavalt OWASP ASVS tase 2 soovitustele lähtudes viimasest stabiilsest versioonist.
Võimalusel integreerida tehisaru põhised turvatestimise vahendid oma tavapäraste töövoogude osaks.

**Nõudetase:** required

**Põhjendus:** [OWASP Application Security Verification Standard](https://owasp.org/www-project-application-security-verification-standard/) tase 2; ennetab tuntud haavatavusi enne toodangut; SAST/DAST ja penetratsioonitestid.

---

### 3.7 Paroolide ja saladuste turvaline salvestamine

**Nõue:** Paroolid ja saladused peavad olema räsitud, soolatud. Ei tohi kasutada hardcoded ega cleartext paroole. Kasutada keskset saladuste hoidlat (nt. Vault). Privaatvõtmeid, salasõnu ja muud sensitiivset infot ei talletata koodihoidlas ega veebidokumentides.

**Nõudetase:** required

**Põhjendus:** [OWASP Password Storage Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html); keskne saladuste hoidla (Vault); ei tohi olla cleartext ega hardcoded — supply chain ja lähtekoodi lekke risk.

---

### 3.8 Sessiooni aegumine

**Nõue:** Rakendusel peab olema konfigureeritav kasutajasessiooni aegumise aeg. Sessioon peab serveri poolel lõppema. Seansi identifikaator peab olema piisava pikkusega, juhuslik ja unikaalne kogu aktiivse seansi jooksul.

**Nõudetase:** required

**Põhjendus:** Volitamata juurdepääsu vähendamine; serveripoolne sessiooni lõpetamine; konfigureeritav aegumine vastavalt andmete tundlikkusele.

---

### 3.9 Krüptograafia

**Nõue:** Krüptoalgoritmite ja räsifunktsioonide kasutamisel tuleb järgida RIA krüptograafiliste algoritmide elutsükli uuringu soovitusi (<https://www.id.ee/artikkel/kruptograafiliste-algoritmide-elutsukli-uuringud-2/>). Valitud krüptoalgoritmide oodatav eluiga peab olema pikem kui rakenduse planeeritud eluiga.

**Nõudetase:** required

**Põhjendus:** RIA krüptograafiliste algoritmide elutsükli uuring tagab ajakohased ja riigi poolt heakskiidetud algoritmid.

---

### 3.10 Sisendi ja väljundi valideerimine

**Nõue:** Kasutaja ja rakenduste sisendit kontrollitakse ja puhastatakse vastu rakenduse ootusi. Väljundit tuleb alati puhastada ja filtreerida enne kasutamist (sh kasutajaliideses).

**Nõudetase:** required

**Põhjendus:** [OWASP Input Validation](https://owasp.org/www-project-proactive-controls/); kaitse [SQL injection](https://en.wikipedia.org/wiki/SQL_injection), [XSS](https://en.wikipedia.org/wiki/Cross-site_scripting) ja [CSRF](https://en.wikipedia.org/wiki/Cross-site_request_forgery) vastu; valideerimine serveri poolel.

---

### 3.11 URL ja sessioon

**Nõue:** URL ei tohi sisaldada isikuandmeid või sessioonivõtit.

**Nõudetase:** required

**Põhjendus:** Privaatsus (isikuandmed URL-is) ja sessiooni kaaperdamise risk; [OWASP Session Management](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html).

---

### 3.12 X-tee ja andmebaasid

**Nõue:** Esitluskiht on andmekihist täielikult isoleeritud. Esitluskihist ei tohi teha otsepäringuid x-tee teenuste ja andmebaasi poole.

**Nõudetase:** required

**Põhjendus:** Kolmekihiline arhitektuur; turvalisus (X-tee päringud on serveri poolel mitte brauserist) ja äriloogika kapseldatus; klient ei tohi pöörduda otse andmebaasi poole.

---

### 3.13 E-ITS

**Nõue:** Infosüsteem peab olema arendatud mimimaalselt kooskõlas E-ITS suure kaitsetarbe nõuetele kui ei ole määratud teisiti.

**Nõudetase:** required

**Põhjendus:** [Eesti infoturbestandard (E-ITS)](https://eits.ria.ee/); riigi infosüsteemide minimaalne infoturbe tase.

---

### 3.14 WAF reeglid

**Nõue:** Arenduse käigus luua WAF reeglid (vt. <https://owasp.org/www-community/Web_Application_Firewall>) kui WAF on kasutusel.

**Nõudetase:** recommended

**Põhjendus:** [OWASP Web Application Firewall](https://owasp.org/www-community/Web_Application_Firewall); täiendav kaitsekiht avalike veebirakenduste ees.

---

### 3.15 Mitmikautentimine

**Nõue:** Kohtades, kus rakendatakse mitmikautentimist laieneb sama kohustus ka administratiivsetele funktsioonidele.

**Nõudetase:** required

**Põhjendus:** Administratiivsete funktsioonide kõrgem turvatase; [NIST SP 800-63B](https://pages.nist.gov/800-63-3/sp800-63b.html) MFA soovitused privileegitud kontodele.

## 4. Andmebaas

### 4.1 Primaarvõti (surrogaatvõti)

**Nõue:** Igas andmebaasi tabelis peab olema tehniline primaarvõti (surrogaatvõti). Ärivõtmeid ei tohi kasutada primaarvõtmena.

**Nõudetase:** required

**Põhjendus:** Andmemudeli stabiilsus ja migreeritavus; ärivõtme muutused ei mõjuta viiteid; jõudlus ja ORM ühilduvus.

---

### 4.2 Välisvõtmed indekseeritud

**Nõue:** Kõik välisvõtmed (foreign keys) peavad olema indekseeritud.

**Nõudetase:** required

**Põhjendus:** Päringute jõudlus JOIN ja FK kontrollide korral; andmete terviklus; vältida täistabeli skannimist suurtes tabelites.

---

### 4.3 Päringumuutujad

**Nõue:** SQL päringute puhul tuleb kasutada päringumuutujaid (Parameter Binding), mitte konstantidena sisse kirjutatud väärtusi.

**Nõudetase:** required

**Põhjendus:** [SQL injection](https://en.wikipedia.org/wiki/SQL_injection) ennetamine; parameter binding on OWASP ja E-ITS nõue.

---

### 4.4 Andmebaasi migratsioonid

**Nõue:** Andmebaasi skeemi muudatused tuleb versioneerida ja automatiseerida migratsioonivahenditega.

**Nõudetase:** required

**Põhjendus:** Näiteks [Liquibase](https://www.liquibase.org/) / [Flyway](https://flywaydb.org/) tagavad korduvad, versioneeritud skeemimuudatused CI/CD-s; väldib käsitsi muduatusi toodangus.

---

### 4.5 Kahekohaline andmebaasikasutaja

**Nõue:** Andmebaasidel peab olem olema rakendatud vähemalt kaks erineva õigustetaset (baasi, skeemi haldamise õigused vs. rakenduse toimetamise õigused). Rakenduste andmebaasikontod peavad omama minimaalseid õiguseid.

**Nõudetase:** expected

**Põhjendus:** [Principle of least privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege); eraldi DDL ja DML õigused; vähendab rünnakupinda ja eksliku skeemimuudatuse riski.

---

### 4.6 Äriloogika andmebaasis

**Nõue:** Andmebaas ei tohi sisaldada äriloogikat (triggerid, protseduurid jms).

**Nõudetase:** expected

**Põhjendus:** [Domain-driven design](https://en.wikipedia.org/wiki/Domain-driven_design) — äriloogika rakenduskihis; andmebaas hoiab andmeid, mitte ärireegleid; lihtsustab testimist ja migreerimist.

---

### 4.7 Loogiline kustutamine ja versioneerimine

**Nõue:** Andmete kustutamine peaks olema loogiline (kustutamise lipuga) või obfuskeerimine. Unikaalseid ID väärtuseid ei taaskasutata. E-ITS kõrgema kaitsetarbega infosüsteemide puhul tuleb kirjed versioneerida.

**Nõudetase:** expected

**Põhjendus:** Auditijälg ja taastamine; [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) andmete elutsükkel; E-ITS tervikluse klass ≥2 nõuab kirjete versioneerimist.

---

## 5. Logimine

### 5.1 Audit-logi nõuded

**Nõue:** Rakenduse tarkvara tööd logitakse ning audit-logi talletatakse rakendusest ja selle andmebaasist eraldi.

Logima peab õnnestunud ja ebaõnnestunud sisselogimiskatsed, ligipääsu logiandmetele, rakenduse töö katkemise, rakenduse administreerimistegevused, süsteemsed muudatused konfiguratsioonis, andmetöötlusega seotud muutused. Logitakse aeg, kontekst (kes, kus, mida, mis tulemusega) ja kategooria (DEBUG, INFO, WARNING, ERROR, FATAL).
DEBUG kategooria talletamine toodangu keskkonnas pole kohustuslik.
Auditilogi kaitstakse muutmise eest ja säilitatakse määratud perioodi.

**Nõudetase:** required

**Põhjendus:** [System and Organization Controls](https://en.wikipedia.org/wiki/System_and_Organization_Controls) (SOC 2); [ISO/IEC 27001](https://en.wikipedia.org/wiki/ISO/IEC_27001); Compliance; Forensics.

---

### 5.2 Logides ei tohi olla tundlikke andmeid

**Nõue:** Logidesse ei tohi salvestada paroole, sessioonivõtmeid (va trace id), isikuandmeid ega muid tundlikke andmeid.

**Nõudetase:** required

**Põhjendus:** [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation); logide leke on sage andmelekke vektor; [ISO/IEC 27001](https://en.wikipedia.org/wiki/ISO/IEC_27001) logimise nõuded.

---

### 5.3 Struktureeritud logimine

**Nõue:** Logimine peab olema struktureeritud (JSON formaat). Logikirjete sisu vastab standardile (OpenTelemetry, ECS).

**Nõudetase:** required

**Põhjendus:** [OpenTelemetry](https://opentelemetry.io/) / [Elastic Common Schema](https://www.elastic.co/docs/reference/ecs); masinloetav logimine toetab SIEM-i, jaotatud jälgimist ja automatiseeritud analüüsi.

### 5.4 Logide säilitamine

**Nõue:** Logisi säilitada minimaalselt 1 aasta, soovitatavalt 3 aastat.

**Nõudetase:** expected

**Põhjendus:** [System and Organization Controls](https://en.wikipedia.org/wiki/System_and_Organization_Controls) (SOC 2); forensics ja compliance; minimaalselt 1 aasta, soovitatavalt 3 aastat vastavalt andmekogu nõuetele.

---

## 6. Monitooring ja health check

### 6.1 Masinloetavad elusoleku ja valmisoleku kontrollid

**Nõue:** Rakendusel peavad olema realiseeritud elusoleku ja valmisoleku kontrollid, eelistatult JSON formaadis. Toodangu keskkondades on rakendused automaatselt monitooritud.

**Nõudetase:** required

**Põhjendus:** [Kubernetes liveness/readiness probes](https://kubernetes.io/docs/concepts/configuration/liveness-readiness-startup-probes/); [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering); automaatne monitooring ja koormusjaotus.

---

## 7. Konfiguratsioon

### 7.1 Rakenduseväline konfiguratsioon

**Nõue:** Konfiguratsioon (sh paroolid) ei ole osa tarkvara koodist vaid paigaldatakse keskkonnamuutujate kaudu.

**Nõudetase:** required

**Põhjendus:** [Twelve-Factor App](https://12factor.net/config) — konfiguratsioon keskkonnamuutujates; ei tohi olla osa lähtekoodist; toetab keskkondade lahusust.

---

### 7.2 Dubleerivate parameetrite vältimine

**Nõue:** Konfiguratsioonis ei tohi olla sisult dubleerivaid parameetreid. Sama parameeter ainult ühes kohas.

**Nõudetase:** required

**Põhjendus:** Konfiguratsiooni haldamise lihtsus; vältib vastuolusid ja vigu, kui sama parameeter on mitmes kohas erineva väärtusega.

---

## 8. Koodi kvaliteet ja testimine

### 8.1 Staatiline koodianalüüs

**Nõue:** Kood peab läbima staatilise koodianalüüsi (nt. SonarQube). Ei tohi esineda kriitilisi ja kõrgemaid probleeme. Rakendus ei lähe toodangusse, kui selles on avastatud turvalisuse nõrkusi või haavatavusi.

**Nõudetase:** required

**Põhjendus:** Näiteks [SonarQube](https://www.sonarsource.com/products/sonarqube/); varajane vigade avastamine; turvanõrkuste tuvastamine enne toodangut; koodikvaliteedi mõõdetavus.

---

### 8.2 Automaattestid ja code review

**Nõue:** Kasutajafunktsionaalsus peab olema kaetud automaattestidega. Sisemised funktsioonid peavad olema kaetud 80% ulatuses testidega. Toodangusse ei lähe kood, mille testid ebaõnnestuvad. Kood peab olema läbinud koodi ülevaatuse (code review) minimaalselt paarisprogrammeerimise printsiibil. Sama saab realiseerida agentses arenduspraktikas erinevate agentidega.

**Nõudetase:** required

**Põhjendus:** [Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration); nelja-silma printsiip (code review) vähendab vigade ja turvariskide sattumist toodangusse; minimaalselt 80% testikattuvus.

---

### 8.3 Koormustestid

**Nõue:** Rakendused on läbinud koormustestid vähemalt kahekordse eeldatava kasutajate mahuga enne toodangusse minekut. Piiratud sisekasutusega rakenduse puhul ei ole nõue kohustuslik.

**Nõudetase:** required

**Põhjendus:** [Load testing](https://en.wikipedia.org/wiki/Software_load_testing); tagab teenuse stabiilsuse eeldatava koormuse korral; avastab kitsaskohad enne toodangut.

---

### 8.4 Lähtekood inglise keeles

**Nõue:** Lähtekood, kommentaarid ja logiteated peavad olema inglise keeles (v.a. kasutajale näidatud teated, mida tuleb realiseerida tõlkefailidega).

**Nõudetase:** required

**Põhjendus:** Rahvusvahelise arendusmeeskonna tugi; koodihoidla loetavus; logide ja monitooringu ühtlus; kasutajale suunatud tekstid tõlkefailides.

---

## 9. API diain ja dokumentatsioon

### 9.1 OpenAPI / Swagger spetsifikatsioon

**Nõue:** REST API-d peavad olema dokumenteeritud OpenAPI (Swagger) spetsifikatsioonis. Tehniliste komponentide API-del eksisteerib automaatselt genereeritud dokumentatsioon.

**Nõudetase:** required

**Põhjendus:** [OpenAPI Specification](https://spec.openapis.org/oas/latest.html); masinloetav API dokumentatsioon; automaatne genereerimine ja integratsioonide tugi.

---

### 9.2 API versioneerimine

**Nõue:** API-d peavad toetama versioneerimist (URL-is v1, v2 vms). Vanade versioonide tugi minimaalselt 6–12 kuud. REST API URL kujul /api/[versioon]/[ressurss]/[id]. Idempotentsus, Cache-Control tugi.

**Nõudetase:** required

**Põhjendus:** Tagasiühilduvus ja kontrollitud toe lõppemine; URL-põhine versioneerimine (/api/v1/); vanade versioonide deprecation 6–12 kuud.

---

### 9.3 MCP protokolli tugi

**Nõue:** Tehisaru sõbralikud liidesed peava järgima  MCP protokolli spetsifikatsiooni (vt. <https://github.com/modelcontextprotocol>).

**Nõudetase:** required

**Põhjendus:** [Model Context Protocol](https://modelcontextprotocol.io/) — standardiseeritud masinliides tehisaru agentidele.

---

### 9.4 Suurte andmekogumite toetus

**Nõue:** Suuri andmekogumeid tagastavatel API-del peab olema lehekülgedeks jagamise tugi (pagination) või järjehoidja põhisele läbimisele.
Vastused ei ületa mõistlikku suurust (näiteks 1000 kirjet korraga).

**Nõudetase:** required

**Põhjendus:** REST best practices; API design; [Representational state transfer](https://en.wikipedia.org/wiki/Representational_state_transfer).

---

### 9.5 Standardiseeritud veavastused

**Nõue:** API veavastused järgivad ühtset struktuuri (nt RFC 7807 Problem Details for HTTP APIs). Veakoodid on dokumenteeritud ja kategoriseeritud.

**Nõudetase:** required

**Põhjendus:** [RFC 7807](https://www.rfc-editor.org/rfc/rfc7807) Problem Details for HTTP APIs (obsoleeritud RFC 9457 poolt); API consistency; Developer experience.

---

### 9.6 API elukaare reeglid

**Nõue:** API versioonide kasutuselt võtmise (deprecation) reeglid on dokumenteeritud. Vanemate versioonide tugi lõpetatakse vähemalt 6–12 kuud ette teada antud hoiatusega.

**Nõudetase:** expected

**Põhjendus:** API versioning best practices; Breaking change management.

---

## 10. Arhitektuur

### 10.1 Autentimine ja identiteet

**Nõue:** Avalike teenuse puhul peab lasutajate autentimine käima läbi TARA teenuse. Rakendus ei tohi luua uut identiteedisüsteemi. Tuleb tugineda olemasolevatele riiklikele või asutuse põhisüsteemidele (ldap/kerberos).

**Nõudetase:** required

**Põhjendus:** [RIA TARA](https://www.ria.ee/et/riigi-infosusteem/eid/partnerile.html) — riigi ühtne autentimisteenus; ei tohi luua paralleelset identiteedisüsteemi; EntraID/LDAP/Kerberos vms. sisekasutajatele.

### 10.1.1 Ristkasutatavad teenused

**Nõue:** Ristkasutatavatel avalikel teenus rakendada riiklik SSO (GOVSSO), kaaluda sisemiselt rakendada JWT, OAuth rakendamist teenuste/teenuskomponentide vahel.

**Nõudetase:** expected

**Põhjendus:** [GOVSSO](https://www.ria.ee/et/riigi-infosusteem/eid/govsso.html) riiklik SSO; [OAuth 2.0](https://oauth.net/2/) / [JWT](https://datatracker.ietf.org/doc/html/rfc7519) teenuste vaheliseks autentimiseks.

---

### 10.2 Autoriseerimine

**Nõue:** Rakenduse tehnilised komponendid kaitsevad iseennast ja valideerivad kasutaja või tehnilise teenuse õigusi. Autoriseerimine on rakenduste enda tagada.

**Nõudetase:** expected

**Põhjendus:** [Role-based access control](https://en.wikipedia.org/wiki/Role-based_access_control); zero trust — iga komponent valideerib õigused ise; ei toetuda ainult võrguperimeetrile.

---

### 10.3 X-tee ja andmevahetus

**Nõue:** Asutuste vaheline infosüsteemide vaheline andmevahetus toimub üle X-tee. X-tee päringud realiseeritakse serveri poolel, mitte kasutajaarvutist.

**Nõudetase:** required

**Põhjendus:** [X-tee](https://www.ria.ee/et/riigi-infosusteem/andmevahetuskiht-x-tee.html) — riigi infosüsteemide vaheline andmevahetuskiht.

---

### 10.4 Eessüsteem ja tagasüsteem eraldatud

**Nõue:** Eessüsteemid ja tagasüsteemid peavad olema arhitektuuriliselt selgelt lahutatud. Kasutajaliides ja teenuse funktsionaalsus on loogiliselt eristatud kihid ja suhtlevad üle API.

**Nõudetase:** required

**Põhjendus:** [Separation of concerns](https://en.wikipedia.org/wiki/Separation_of_concerns); sõltumatud arendus-, paigaldus- ja skaleerimistsüklid; API-põhine suhtlus.

---

### 10.5 Domeenipõhine disain

**Nõue:** Rakendused on disainitud domeenist juhinduva disaini (<https://en.wikipedia.org/wiki/Domain-driven_design>) ja 12F arhitektuuri põhimõtteid jälgides (vt. <https://12factor.net/>).

**Nõudetase:** expected

**Põhjendus:** [Domain-driven design](https://en.wikipedia.org/wiki/Domain-driven_design); [Twelve-Factor App](https://12factor.net/); loogiline tükeldamine ja hooldatavus.

---

### 10.6 Komponeeritav esitluskiht

**Nõue:** Kasutajaliides ja teenuse funktsionaalsus peavad olema loogiliselt eristatud. Avalike teenuste puhul peab esitluskiht olema disainitud viisil, et kasutajaliidese funktsionaalsust oleks võimalik taaskasutada ja integreerida erinevates portaalides ning kanalites ilma äriloogika dubleerimiseta. Kasutajaliidese komponendid peavad olema võimalusel iseseisvalt juurutatavad ja taaskasutatavad. Avalikes teenustes tuleb arvestada kesksete portaalide (nt eesti.ee) nõuetega.

**Nõudetase:** expected

**Põhjendus:** Komponeeritav esitluskiht võimaldab sama teenuse kasutajaliidese funktsionaalsuste taaskasutamist erinevates portaalides ja kanalites, vähendab dubleerivat arendust ning toetab sõltumatut arendust ja juurutamist. Nõude realiseerimiseks võib kasutada mikrofrontendide (Micro Frontends), veebikomponentide (Web Components) või muid samaväärseid lähenemisi.
Viited:

- <https://martinfowler.com/articles/micro-frontends.html>
- <https://developer.mozilla.org/en-US/docs/Web/API/Web_components>
- <https://www.tedi.ee/>

### 10.7 REST API ja olekuta teenused

**Nõue:** Tehnilised komponendid avaldavad REST API. Kasutajaliidese olekut hoitakse kliendi poolel; teenused on olekuta (stateless).

**Nõudetase:** expected

**Põhjendus:** [Representational state transfer](https://en.wikipedia.org/wiki/Representational_state_transfer); [stateless](https://en.wikipedia.org/wiki/Statelessness) teenused skaleeruvad horisontaalselt; olek kliendi poolel.

---

### 10.8 Pilvekõlbulikkus ja hajuskomponendid

**Nõue:** Rakendus on pilvekõlbulik: skriptiga paigaldatav, koosneb mitmest sõltumatust instantsist, on automaatselt skaleeritav, andmed varundatud. Hajuskomponendid ei jaga sama andmebaasi, mälu ega failisüsteemi. Kõik andmed mida on vaja talletada pikemalt, peavad olema talletatud teenuse instantsidest väljaspool.

**Nõudetase:** expected

**Põhjendus:** [Cloud native](https://en.wikipedia.org/wiki/Cloud-native_computing); [Twelve-Factor App](https://12factor.net/); horisontaalne skaleerimine; andmed instantsidest väljaspool (S3, eraldi DB).

---

### 10.9 Korrelatsiooni ID

**Nõue:** Tehnilised komponendid logivad või genereerivad korrelatsiooni ID. Korrelatsiooni ID saadetakse iga edasise päringuga kaasa (nt X-Correlation-ID).

**Nõudetase:** draft

**Põhjendus:** [Distributed tracing](https://en.wikipedia.org/wiki/Distributed_tracing); [OpenTelemetry](https://opentelemetry.io/) trace context; logikirjete sidumine üle komponentide (X-Correlation-ID / trace-id).

---

### 10.10 Rakendusserver eraldi andmebaasiserverist

**Nõue:** Rakendusserver peab võimaldama töötamist andmebaasiserverist eraldi serveril/konteineris.

**Nõudetase:** required

**Põhjendus:** Skaleeruvus; komponentide sõltumatud elutsüklid; konteineripõhine paigaldus; andmebaasi ja rakenduse eraldi haldus.

---

### 10.11 Konfiguratsioonifailid on kaitstud

**Nõue:** Konfiguratsioonifailid peavad olema kaitstud. Muutmine on lubatud ainult administraatoritel.

**Nõudetase:** required

**Põhjendus:** Konfiguratsiooni muutmine ainult administraatoritel; vaikimisi kaitstud failid (nt. IIS *.config, Apache*.conf); väldib volitamata muudatusi.

---

## 11. Arendus ja juurutus

### 11.1 Versioneerimine

**Nõue:** Rakenduse kood on versioneeritud kasutades Git'i. Kogu lähtekood tuleb tarnida hajusversioonihalduse süsteemi (Git) kaudu.

**Nõudetase:** required

**Põhjendus:** [Git](https://git-scm.com/) — muudatuste jälgimine, koostöö, auditeeritavus

---

### 11.1.1 Kohapealne puhver

**Nõue:** Rakenduse ehitamiseks vajalikud välised sõltuvused peavad olema peegeldatud kohalikesse repositooriumitesse.

**Nõudetase:** expected

**Põhjendus:** Tarneahela turvalisus; korduvad ehitused ilma välisvõrguta; sõltuvuste kontroll ja skaneerimine (nt. Artifactory, Nexus jms.).

---

### 11.2 Koodi selgus

**Nõue:** Lähtekood on kirjutatud selgusega, mis võimaldab uuel arendajal süsteemi edasi arendada. Lähtuda Clean Code printsiibist.

**Nõudetase:** required

**Põhjendus:** [Clean Code](https://en.wikipedia.org/wiki/Robert_C._Martin); teadmusülekanne uutele arendajatele; vähendab tehnilist võlga ja hoolduskulusid.

---

### 11.3 Taaskasutus

**Nõue:** Taaskasutatavalt disainitud kood on e-riigi koodivaramus (<https://koodivaramu.eesti.ee>), funktsioonid on e-riigi funktsioonivaramus (<https://funktsioonivaramu.eesti.ee/>)

**Nõudetase:** recommended

**Põhjendus:** Võimaldab vältida dubleerivaid arendusi; võimaldab ühiskomponentide aiemat kasutamist.

---

### 11.4 Programmeerimiskeeled ja komponentide EOL

**Nõue:** Arenduses ei kasutata programmeerimiskeeli väljaspool Top 25 TIOBE index'it (<https://www.tiobe.com/tiobe-index/>). Kõikide komponentide eluea lõpp (EOL) ei tohi olla lähemal kui 5 aastat.

**Nõudetase:** expected

**Põhjendus:** [TIOBE Index](https://www.tiobe.com/tiobe-index/) — tööjõu kättesaadavus ja kogukonna tugi; EOL >5 aasta pärast tagab turvapaigad ja toetuse.

---

### 11.5 Litsents

**Nõue:** Tarkvara tuleb markeerida litsentsiga (LICENCE-fail või faili päis). Riik eelistav vaba litsentsi kasutamist (soovitus: MIT, alternatiiv EUPL).

**Nõudetase:** required

**Põhjendus:** [MIT License](https://en.wikipedia.org/wiki/MIT_License) / [EUPL](https://en.wikipedia.org/wiki/European_Union_Public_Licence); avatud lähtekood riigi tarkvaras; õiguslik selgus taaskasutamisel.

---

### 11.6 Taasteplaanid

**Nõue:** Teenuse rakendustele eksisteerivad ajakohased taasteplaanid, eelistatult automatiseeritult toimivad.

**Nõudetase:** required

**Põhjendus:** [ISO 22301](https://en.wikipedia.org/wiki/ISO_22301) — business continuity; [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering) disaster recovery; RTO/RPO täitmine.

---

### 11.7 CI/CD ja automatiseerimine

**Nõue:** Keskkondadesse tarkvara paigaldamine on automatiseeritud (Gitlab CI, Jenkins jms). Soovitatav on kasutada blue-green juurutusmustrit.

**Nõudetase:** required

**Põhjendus:** [Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery); korduvad, auditeeritavad juurutused; [Blue-green deployment](https://en.wikipedia.org/wiki/Blue-green_deployment) katkestuste vältimiseks.

---

### 11.8 Semantiline versioneerimine

**Nõue:** Rakendus on versioneeritud semantilise versioneerimise põhimõtte järgi (A.B.C). Lisainfo: <https://semver.org/>

**Nõudetase:** expected

**Põhjendus:** [Semantic Versioning](https://semver.org/); selge versioonide tähendus (MAJOR.MINOR.PATCH); API ja pakettide ühilduvus.

---

### 11.9 Vastupanuvõime

**Nõue:** Rakendus peab olema väliste süsteemide tõrgete suhtes vastupanuvõimeline (resilient). Välise süsteemi tõrge tohib mõjutada ainult otseselt sõltuvaid kasutuslugusid.

**Nõudetase:** required

**Põhjendus:** [Circuit breaker design pattern](https://en.wikipedia.org/wiki/Circuit_breaker_design_pattern); [Graceful degradation](https://en.wikipedia.org/wiki/Graceful_degradation); väliste süsteemide tõrge piirdub sõltuvate kasutuslugudega.

---

### 11.10 Kasutuslood

**Nõue:** Süsteemi funktsionaalne skoop on defineeritud ja dokumenteeritud selgesõnaliste kasutuslugudega.

**Nõudetase:** required

**Põhjendus:** See on testide ja vastuvõtu alus; sidusrühmadel on ühtne arusaam nõuetest.

---

## 12. Andmekvaliteet ja standardid

### 12.1 Aadressiandmete süsteem

**Nõue:** Aadressiandmete käitlemisel lähtuda määrusest "Aadressiandmete süsteem" (<https://www.riigiteataja.ee/akt/118062021032?leiaKehtiv>)

**Nõudetase:** required

**Põhjendus:** Aadressiandmete süsteem tagab ühtsed aadressid riigi registris ja ADS integratsiooni.

---

### 12.2 Klassifikaatorid ja EMTAK

**Nõue:** Tegevusalade andmete puhul kasutada EMTAK klassifikaatorit (<https://www.rik.ee/et/e-ariregister/emtak-tegevusalad>)  või määruse "Klassifikaatorite süsteem" (vt. <https://www.riigiteataja.ee/akt/12910889>) nõudeid.

**Nõudetase:** required

**Põhjendus:** [EMTAK](https://www.rik.ee/et/e-ariregister/emtak-tegevusalad); [Klassifikaatorite süsteem](https://www.riigiteataja.ee/akt/12910889) (VV määrus nr 11); andmete võrdlevus ja statistika.

---

### 12.3 Objektide identifitseerimine

**Nõue:** Objektid identifitseeritakse registrikoodide abil (<https://www.riigiteataja.ee/akt/123122022024?leiaKehtiv>). Isikud isikukoodiga rahvastikuregistrist (<https://www.riigiteataja.ee/akt/128062019037?leiaKehtiv>).

**Nõudetase:** required

**Põhjendus:** [Registrikoodide süsteem](https://www.riigiteataja.ee/akt/123122022024?leiaKehtiv); [Rahvastikuregister](https://www.riigiteataja.ee/akt/128062019037?leiaKehtiv) isikukood; riiklikult ühtsed identifikaatorid.

---

### 12.4 Andmejälgija

**Nõue:** Infosüsteemide ja andmekogude juures kasutatakse RIA andmejälgijat kooskõlas kehtivate nõuetega, vt. <https://github.com/e-gov/AJ>

**Nõudetase:** required  

**Põhjendus:** [RIA Andmejälgija (AJ)](https://github.com/e-gov/AJ); isikuandmete töötlemise läbipaistvus ([TKTA §13 lg 10](https://www.riigiteataja.ee/et/akt/119052022008?leiaKehtiv)); auditeeritavus ja usaldus.

---

### 12.5 Andmekvaliteedi mudel

**Nõue:** Infosüsteemile peab rakendama andmekvaliteedi mudelit (täielikkus, ajakohasus, õigsus, reeglipärasus, ühekordsus). Kvaliteedi mõõtmise tulemused on väljavõetavad.

**Nõudetase:** expected

**Põhjendus:** [ISO 8000](https://www.iso.org/standard/50798.html) andmekvaliteedi dimensioonid; täielikkus, ajakohasus, õigsus, reeglipärasus, ühekordsus; taaskasutatavate andmete usaldus.

---

### 12.6 Andmete eksport

**Nõue:** Andmeid saab eksportida masin- ja inimloetavas vormingus (nt. JSON, CSV). Masintöödeldavad andmed on struktureeritud. Soovitav on luua eksportdivõimekus läbi API.

**Nõudetase:** required

**Põhjendus:** [Avaliku teabe seadus](https://www.riigiteataja.ee/akt/114032011019?leiaKehtiv); masin- ja inimloetavad vormingud (JSON, CSV); avaandmete taaskasutamine.

---

### 12.7 Avaandmete teabevärav

**Nõue:** Infosüsteemile on koostatud andmekirjeldused, mis on avalikustatud Avaandmete teabeväravas.
Andmekirjelduste loomisel ja nende teabeväravasse edastamiseks saab kasutada RIHAKE'se rakendust või suhelda otse API liidesega.

**Nõudetase:** required  

**Põhjendus:** [Eesti teabevärav](https://andmed.eesti.ee/); [AvTS §29 lg 6](https://www.riigiteataja.ee/et/akt/122032011010?leiaKehtiv); andmekirjeldused RIHAKE'se (<https://abi.ria.ee/rihake>) kaudu; andmete leitavus ja taaskasutamine.

---

## 13. Versioneerimine ja tarne

### 13.1 Muudatuste kirjeldus (Changelog)

**Nõue:** Iga uue versiooniga peab kaasas olema muudatuste kirjeldus (Changelog või release notes).

**Nõudetase:** required

**Põhjendus:** [Keep a Changelog](https://keepachangelog.com/); muudatuste jälgimine kasutajatele ja operaatoritele

---

## 14. Dokumentatsioon ja otsustamine

### 14.1 Dokumentatsioon eesti keeles

**Nõue:** Lõppkasutajatele ja avalikkusele suunatud dokumentatsioon peab olema kirjutatud eesti keeles.

**Nõudetase:** required

**Põhjendus:** Eesti keel on riigikeel (<https://www.riigiteataja.ee/et/akt/28746?leiaKehtiv>)

---

### 14.2 Kasutusjuhend inimesele

**Nõue:** Tarkvara komponentide puhul on olemas kasutusjuhendid (Readme.MD)): käivitamine, peatamine, tervisekontroll, tüüpilised probleemid ja lahendused.

**Nõudetase:** required

**Põhjendus:** [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering); Operations; Incident response.

---

### 14.3 Kasutusjuhend masinale

**Nõue:** Tarkvara komponentide puhul on olemas masinale arusaadavad kasutusjuhendid (Agent.MD)): käivitamine, peatamine, tervisekontroll, tüüpilised probleemid ja lahendused.

**Nõudetase:** expected

**Põhjendus:** Masinloetav operatsioonijuhend (Agent.MD / README) toetab automatiseeritud juurutust, CI/CD agente ja tehisaru abistatud hooldust; OpenAPI ja health check viited.

---

### 14.4 Arhitektuuriotsuste dokumenteerimine (ADR)

**Nõue:** Olulised arhitektuurilised, tehnilised ja integratsioonialased otsused tuleb dokumenteerida Architecture Decision Record (ADR) vormis. ADR-id peavad olema hallatud Git-põhises versioonihalduses koos lähtekoodiga. ADR peab minimaalselt kirjeldama:

- otsuse konteksti;
- kaalutud alternatiive;
- tehtud otsust;
- otsuse põhjendust;
- mõju süsteemile.

**Nõudetase:** expected

**Põhjendus:**  ADR-id säilitavad teadmise, miks konkreetne tehniline või arhitektuuriline lahendus valiti. See vähendab teadmuse kadumist, toetab süsteemi edasiarendamist ning võimaldab arhitektuuriliste otsuste jälgitavust kogu süsteemi elutsükli jooksul.
Viited:

- Michael Nygard, Documenting Architecture Decisions (<https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions>)
- ADR GitHub organisatsioon (<https://adr.github.io/>)

---

### 14.5 Dokumentatsioon kui lähtekood

**Nõue:** Süsteemi nõuded, kasutuslood, arhitektuurikirjeldused, arhitektuuriotsused (ADR), liidestuste kirjeldused ja muu tehniline dokumentatsioon peavad olema hallatud Git-põhises versioonihalduses koos lähtekoodiga. Dokumentatsiooni autoriteetne allikas peab olema avatud, tekstipõhine, versioonihallatav ja masintöödeldav.
Vormingute näited:

- dokumentatsioon, nõuded ja kasutuslood: Markdown (MD);
- arhitektuuri-, protsessi-, integratsiooni- ja süsteemiskeemid: tekstipõhised skeemikirjeldusformaadid (näiteks Mermaid, PlantUML, Structurizr DSL või muu samaväärne formaat);
- API kirjeldused: OpenAPI;
- struktureeritud konfiguratsiooni- ja andmekirjeldused: JSON või YAML.

Diagrammide autoriteetseks lähtevorminguks loetakse tekstipõhine skeemikirjeldus. Diagrammide säilitamine üksnes pildi- või binaarvormingus ei ole lubatud.

**Nõudetase:** expected

**Põhjendus:**  Documentation as Code käsitleb dokumentatsiooni samadel põhimõtetel nagu lähtekoodi: versioonihaldus, muudatuste ülevaatus, automatiseeritud valideerimine ja koostöö. See parandab dokumentatsiooni ajakohasust, jälgitavust ja taaskasutatavust.

Viited:

- <https://www.writethedocs.org/guide/docs-as-code/>

---

## 15. Jõudlus ja skaleeritavus

### 15.1 Vastuseaja SLA

**Nõue:** Rakenduse kriitiliste operatsioonide vastuseaeg peab olema määratletud ja mõõdetav. Soovitus: p95 latentsus < 2 sekundit tavalistele kasutajategevustele; API päringutele < 500 ms tüüpilistele operatsioonidele.

**Nõudetase:** expected

**Põhjendus:** [ISO/IEC 25010](https://en.wikipedia.org/wiki/ISO/IEC_9126) – Performance efficiency; kasutajakogemuse kvaliteet; [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering) praktikad.

---

### 15.2 Koormuse all aeglane degradatsioon

**Nõue:** Kõrge koormuse korral rakendus ei krahhi, vaid aeglustab vastuseid või rakendab piirangute süsteemi (rate limiting, queue). Kriitilised funktsioonid jäävad kättesaadavaks.

**Nõudetase:** required

**Põhjendus:** [Circuit breaker design pattern](https://en.wikipedia.org/wiki/Circuit_breaker_design_pattern); Graceful degradation.

---

### 15.3 API rate limiting

**Nõue:** Avalikud ja autenditud API-d peavad toetama rate limiting’ut, et vältida ärakasutamist ja tagada teenuse stabiilsus. Rate limiting on dokumenteeritud ja konfigureeritav.

**Nõudetase:** required

**Põhjendus:** [OWASP](https://en.wikipedia.org/wiki/OWASP) API Security; DDoS kaitse; teenuse stabiilsus.

---

## 16. Kättesaadavus ja taastumine

### 16.1 Kättesaadavuse SLA

**Nõue:** Teenuse kättesaadavus on määratletud (nt 99,5% või 99,9% aastas) ja monitooritav. Planeeritud hooldusaknad on dokumenteeritud ja teavitamine on korraldatud.

**Nõudetase:** required

**Põhjendus:** [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering); [ITIL](https://en.wikipedia.org/wiki/ITIL); teenuse taseme lepingud.

---

### 16.2 RTO ja RPO

**Nõue:** Taastumise aeg (RTO) ja andmete kaotuspunkt (RPO) on määratletud vastavalt ärivajadustele. Varukoopiad ja taastamisprotsessid on testitud regulaarselt.

**Nõudetase:** required

**Põhjendus:** [ISO 22301](https://en.wikipedia.org/wiki/ISO_22301) – Business continuity management; BCP; Disaster Recovery.

---

## 17. Privaatsus ja andmekaitse (GDPR)

### 17.1 Andmete minimeerimine

**Nõue:** Kogutakse ja töödeldakse ainult vajalikke isikuandmeid. Andmete kogumine on põhjendatud ja dokumenteeritud.

**Nõudetase:** required

**Põhjendus:** [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) art 5; Privacy by Design.

---

### 17.2 Kustutamisõigus ja andmete säilitamine

**Nõue:** Rakendus toetab isikuandmete kustutamist, obfuskeerimist või anonümiseerimist vastavalt õigusaktidele. Säilitustähtajad on määratletud ja nende tegevuste automatiseerimine on võimalik.

**Nõudetase:** required

**Põhjendus:** [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) art 17; Right to erasure; Andmete elutsükkel.

---

### 17.3 Privaatsus disainis

**Nõue:** Isikuandmete kaitse on arvestatud juba süsteemi kavandamise faasis (Privacy by Design). Tundlikud andmed on identifitseeritud ja kaitstud.

**Nõudetase:** required

**Põhjendus:** [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) art 25; [ISO/IEC 27701](https://en.wikipedia.org/wiki/ISO/IEC_27701) – Privacy information management.

---

## 18. Observability ja SRE

### 18.1 Jaotatud jälgimine (distributed tracing)

**Nõue:** Hajusrakenduste puhul toetab süsteem jaotatud jälgimist (nt OpenTelemetry, Jaeger). Päringud on jälgitavad üle komponentide.

**Nõudetase:** required

**Põhjendus:** [OpenTelemetry](https://opentelemetry.io/) (CNCF; vt ka [Distributed tracing](https://en.wikipedia.org/wiki/Distributed_tracing)); [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering).

---

### 18.2 SLO/SLI määratlus

**Nõue:** Teenuse kriitiliste operatsioonide puhul on määratletud teenuse taseme indikaatorid (SLI) ja eesmärgid (SLO). SLO-d on dokumenteeritud ja monitooritavad.

**Nõudetase:** required

**Põhjendus:** [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering); Google SRE handbook.

---

## 19. Muudatuste juhtimine

### 19.1 Funktsioonilipud (feature flags)

**Nõue:** Uued funktsioonid saab juurutada funktsioonilipude (feature flags) kaudu, võimaldades järk-järgulist roll-out'i ja kiiret tagasivõtmist ilma uue versiooni väljastamiseta.

**Nõudetase:** recommended

**Põhjendus:** [Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery); Risk mitigation; A/B testing.

---

### 19.2 Tagasivõtmise võimalus (rollback)

**Nõue:** Juurutusprotsess võimaldab kiirelt naasta eelmise töötava versiooni juurde (rollback) ilma andmekaotusteta. Rollback on testitud ja dokumenteeritud.

**Nõudetase:** expected

**Põhjendus:** [Blue-green deployment](https://en.wikipedia.org/wiki/Blue-green_deployment); Canary; Deployment safety.

---

## 20. Andmete haldus

### 20.1 Andmete säilituspoliitika

**Nõue:** Andmete säilitustähtajad on määratletud vastavalt õigusaktidele ja ärivajadustele. Säilitusaja ületanud andmed kustutatakse või anonüümiseeritakse automatiseeritult.

**Nõudetase:** required

**Põhjendus:** [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation); Data lifecycle; Retention policies.

---
