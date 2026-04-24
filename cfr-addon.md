# Ettepanekud täiendavate mittefunktsionaalsete nõuete kandidaatide kohta

**Analüüs:** Kõik mittefunktsionaalsed nõuded erinevate asutuste MFN-dokumentides ja uuendatud cfr.md dokumendis.

**Põhimõte:** Täiendused põhinevad tarkvaraarenduse ja juhtimise parimate praktikate võrdlusel praeguse nõuete kogumiga.

**Viidatud standardid ja praktikad (Wikipedia):**
- [ISO/IEC 25010](https://en.wikipedia.org/wiki/ISO/IEC_9126) – tarkvara kvaliteedimudel (25010 asendab 9126)
- [ITIL](https://en.wikipedia.org/wiki/ITIL) – IT teenuste halduse raamistik
- [DevOps](https://en.wikipedia.org/wiki/DevOps) – arenduse ja operatsioonide integratsioon
- [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering) – SRE
- [OWASP](https://en.wikipedia.org/wiki/OWASP) – veebirakenduste turvalisus

---

## 1. Jõudlus ja skaleeritavus

### 1.1 Vastuseaja SLA

**Nõue:** Rakenduse kriitiliste operatsioonide vastuseaeg peab olema määratletud ja mõõdetav. Soovitus: p95 latentsus < 2 sekundit tavalistele kasutajategevustele; API päringutele < 500 ms tüüpilistele operatsioonidele.
**Nõudetase:** expected

**Põhjendus:** [ISO/IEC 25010](https://en.wikipedia.org/wiki/ISO/IEC_9126) – Performance efficiency; kasutajakogemuse kvaliteet; [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering) praktikad.

---

### 1.2 Koormuse all aeglane degradatsioon

**Nõue:** Kõrge koormuse korral rakendus ei krahhi, vaid aeglustab vastuseid või rakendab piirangute süsteemi (rate limiting, queue). Kriitilised funktsioonid jäävad kättesaadavaks.
**Nõudetase:** expected

**Põhjendus:** [Circuit breaker design pattern](https://en.wikipedia.org/wiki/Circuit_breaker_design_pattern); Graceful degradation.

---

### 1.3 API rate limiting

**Nõue:** Avalikud ja autenditud API-d peavad toetama rate limiting’ut, et vältida ärakasutamist ja tagada teenuse stabiilsus. Rate limiting on dokumenteeritud ja konfigureeritav.
**Nõudetase:** expected

**Põhjendus:** [OWASP](https://en.wikipedia.org/wiki/OWASP) API Security; DDoS kaitse; teenuse stabiilsus.

---

## 2. Kättesaadavus ja taastumine

### 2.1 Kättesaadavuse SLA

**Nõue:** Teenuse kättesaadavus on määratletud (nt 99,5% või 99,9% aastas) ja monitooritav. Planeeritud hooldusaknad on dokumenteeritud ja teavitamine on korraldatud.
**Nõudetase:** expected

**Põhjendus:** [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering); [ITIL](https://en.wikipedia.org/wiki/ITIL); teenuse taseme lepingud.

---

### 2.2 RTO ja RPO

**Nõue:** Taastumise aeg (RTO) ja andmete kaotuspunkt (RPO) on määratletud vastavalt ärivajadustele. Varukoopiad ja taastamisprotsessid on testitud regulaarselt.
**Nõudetase:** expected

**Põhjendus:** [ISO 22301](https://en.wikipedia.org/wiki/ISO_22301) – Business continuity management; BCP; Disaster Recovery.

---

## 3. Privaatsus ja andmekaitse (GDPR)

### 3.1 Andmete minimeerimine

**Nõue:** Kogutakse ja töödeldakse ainult vajalikke isikuandmeid. Andmete kogumine on põhjendatud ja dokumenteeritud.
**Nõudetase:** required

**Põhjendus:** [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) art 5; Privacy by Design.

---

### 3.2 Kustutamisõigus ja andmete säilitamine

**Nõue:** Rakendus toetab isikuandmete kustutamist vastavalt õigusaktidele. Säilitustähtajad on määratletud ja automatiseeritud kustutamine on võimalik.
**Nõudetase:** required

**Põhjendus:** [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) art 17; Right to erasure; Andmete elutsükkel.

---

### 3.3 Privaatsus disainis

**Nõue:** Isikuandmete kaitse on arvestatud juba süsteemi kavandamise faasis (Privacy by Design). Tundlikud andmed on identifitseeritud ja kaitstud.
**Nõudetase:** expected

**Põhjendus:** [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation) art 25; [ISO/IEC 27701](https://en.wikipedia.org/wiki/ISO/IEC_27701) – Privacy information management.

---

## 4. Turvalisus – täiendavad nõuded

### 4.1 Turvalised HTTP-päised

**Nõue:** Rakendus kasutab turvalisi HTTP-päiseid: Content-Security-Policy (CSP), X-Content-Type-Options, X-Frame-Options, Strict-Transport-Security (HSTS), Referrer-Policy.
**Nõudetase:** expected

**Põhjendus:** [OWASP](https://en.wikipedia.org/wiki/OWASP) Secure Headers; [Content Security Policy](https://en.wikipedia.org/wiki/Content_Security_Policy); veebirakenduste turvalisus.

---

### 4.2 CSRF kaitse

**Nõue:** State-changing päringud on kaitstud CSRF (Cross-Site Request Forgery) vastu. Kasutatakse CSRF tokeneid või SameSite küpsiseid.
**Nõudetase:** required

**Põhjendus:** [OWASP](https://en.wikipedia.org/wiki/OWASP) Top 10; [Cross-site request forgery](https://en.wikipedia.org/wiki/Cross-site_request_forgery).

---

### 4.3 Sõltuvuste haavatavuste skaneerimine

**Nõue:** Rakenduse sõltuvused (teegid, konteinerid) skaneeritakse regulaarselt haavatavuste osas (nt Dependabot, Snyk, Trivy). Kriitilised haavatavused lahendatakse enne toodangusse minekut.
**Nõudetase:** required

**Põhjendus:** [OWASP](https://en.wikipedia.org/wiki/OWASP); Software Supply Chain Security; NIST SSDF.

---

### 4.4 SBOM (Software Bill of Materials)

**Nõue:** Rakenduse kohta on koostatav masinloetav komponentide loend (SBOM), nt SPDX või CycloneDX formaadis. SBOM on saadaval iga väljastatud versiooni kohta.
**Nõudetase:** recommended

**Põhjendus:** [Software bill of materials](https://en.wikipedia.org/wiki/Software_bill_of_materials); NTIA; CISA; Software Supply Chain Security.

---

## 5. Observability ja SRE

### 5.1 Jaotatud jälgimine (distributed tracing)

**Nõue:** Hajusrakenduste puhul toetab süsteem jaotatud jälgimist (nt OpenTelemetry, Jaeger). Päringud on jälgitavad üle komponentide.
**Nõudetase:** expected

**Põhjendus:** [OpenTelemetry](https://opentelemetry.io/) (CNCF; vt ka [Distributed tracing](https://en.wikipedia.org/wiki/Distributed_tracing)); [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering).

---

### 5.2 SLO/SLI määratlus

**Nõue:** Teenuse kriitiliste operatsioonide puhul on määratletud teenuse taseme indikaatorid (SLI) ja eesmärgid (SLO). SLO-d on dokumenteeritud ja monitooritavad.
**Nõudetase:** recommended

**Põhjendus:** [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering); Google SRE handbook.

---

### 5.3 Intsidendi vastus ja post-mortem

**Nõue:** Intsidendite korral on olemas protsess reageerimiseks ja dokumenteerimiseks. Oluliste intsidendite puhul koostatakse post-mortem analüüs (blameless) ja parandusmeetmed.
**Nõudetase:** expected

**Põhjendus:** [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering); [ITIL](https://en.wikipedia.org/wiki/ITIL) Incident Management; Continuous improvement.

---

## 6. API disain

### 6.1 Leheküljendus ja suurte andmekogumite toetus

**Nõue:** Suurte andmekogumite tagastavatel API-del on toetus leheküljendusele (pagination) või kursori-põhisele läbimisele. Vastused ei ületa mõistlikku suurust (nt max 1000 kirjet).
**Nõudetase:** expected

**Põhjendus:** REST best practices; API design; [Representational state transfer](https://en.wikipedia.org/wiki/Representational_state_transfer).

---

### 6.2 Standardiseeritud veavastused

**Nõue:** API veavastused järgivad ühtset struktuuri (nt RFC 7807 Problem Details for HTTP APIs). Veakoodid on dokumenteeritud ja kategoriseeritud.
**Nõudetase:** recommended

**Põhjendus:** [RFC 7807](https://www.rfc-editor.org/rfc/rfc7807) Problem Details for HTTP APIs (obsoleeritud RFC 9457 poolt); API consistency; Developer experience.

---

### 6.3 API deprecation poliitika

**Nõue:** API versioonide kasutuselt võtmise (deprecation) poliitika on dokumenteeritud. Vanemate versioonide tugi lõpetatakse vähemalt 6–12 kuud ette teada antud hoiatusega.
**Nõudetase:** expected

**Põhjendus:** API versioning best practices; Breaking change management.

---

## 7. Dokumentatsioon ja otsustamine

### 7.1 Arhitektuuri otsuste dokumenteerimine (ADR)

**Nõue:** Olulised arhitektuuri- ja disainiotused on dokumenteeritud (Architecture Decision Records). Iga ADR sisaldab konteksti, otsust ja tagajärgi.
**Nõudetase:** recommended

**Põhjendus:** [Architectural decision](https://en.wikipedia.org/wiki/Architectural_decision); Michael Nygard ADR pattern; Knowledge retention; Onboarding.

---

### 7.2 Käivitusjuhend (runbook)

**Nõue:** Toodangu keskkonna komponentide puhul on olemas käivitusjuhendid (runbook): käivitamine, peatamine, tervisekontroll, tüüpilised probleemid ja lahendused.
**Nõudetase:** expected

**Põhjendus:** [Site Reliability Engineering](https://en.wikipedia.org/wiki/Site_reliability_engineering); Operations; Incident response.

---

## 8. Kasutajakogemus ja juurdepääsetavus

### 8.1 Mobiilseadmetega arvestamine

**Nõue:** Veebirakenduse kasutajaliides on kasutatav mobiilseadmetel (responsive design). Kriitilised funktsioonid on kasutatavad väikese ekraaniga seadmetel.
**Nõudetase:** expected

**Põhjendus:** Mobile-first; [Web Content Accessibility Guidelines](https://en.wikipedia.org/wiki/Web_Content_Accessibility_Guidelines); User experience.

---

### 8.2 Klaviatuuri navigatsioon

**Nõue:** Kogu kasutajaliides on täielikult kasutatav klaviatuuri abil ilma hiireta. Fookuse järjekord on loogiline ja nähtav.
**Nõudetase:** required (WCAG AA osa)

**Põhjendus:** [Web Content Accessibility Guidelines](https://en.wikipedia.org/wiki/Web_Content_Accessibility_Guidelines) 2.2; Keyboard accessibility; Screen reader support.

---

### 8.3 Vähendatud liikumine (reduced motion)

**Nõue:** Rakendus võtab arvesse kasutaja eelistust vähendatud animatsioonide suhtes (prefers-reduced-motion). Animaatud sisu võib alternatiivina olla staatiline.
**Nõudetase:** recommended

**Põhjendus:** [Web Content Accessibility Guidelines](https://en.wikipedia.org/wiki/Web_Content_Accessibility_Guidelines) 2.2; Accessibility; Vestibular disorders.

---

## 9. Muudatuste juhtimine

### 9.1 Funktsioonilipud (feature flags)

**Nõue:** Uued funktsioonid saab juurutada funktsioonilipude (feature flags) kaudu, võimaldades järk-järgulist roll-out'i ja kiiret tagasivõtmist ilma uue versiooni väljastamiseta.
**Nõudetase:** recommended

**Põhjendus:** [Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery); Risk mitigation; A/B testing.

---

### 9.2 Tagasivõtmise võimalus (rollback)

**Nõue:** Juurutusprotsess võimaldab kiirelt naasta eelmise töötava versiooni juurde (rollback) ilma andmekaotusteta. Rollback on testitud ja dokumenteeritud.
**Nõudetase:** expected

**Põhjendus:** [Blue-green deployment](https://en.wikipedia.org/wiki/Blue-green_deployment); Canary; Deployment safety.

---

## 10. Andmete haldus

### 10.1 Varundamine ja taastamine

**Nõue:** Andmebaasi ja kriitiliste andmete varundamine on automatiseeritud. Varunduste taastamine on perioodiliselt testitud. Varunduste säilitusaeg on määratletud.
**Nõudetase:** required

**Põhjendus:** BCP; RPO; Data protection; [ISO 22301](https://en.wikipedia.org/wiki/ISO_22301).

---

### 10.2 Andmete säilituspoliitika

**Nõue:** Andmete säilitustähtajad on määratletud vastavalt õigusaktidele ja ärivajadustele. Säilitusaja ületanud andmed kustutatakse või anonüümiseeritakse automatiseeritult.
**Nõudetase:** required

**Põhjendus:** [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation); Data lifecycle; Retention policies.

---

## 11. Tehniline võlg ja elutsükkel

### 11.1 Deprecation’i kommunikatsioon

**Nõue:** Komponentide, API-de ja tehnoloogiate kasutuselt võtmine (deprecation) tehakse teada vähemalt 6 kuud ette. Alternatiivid ja migratsiooniteed on dokumenteeritud.
**Nõudetase:** expected

**Põhjendus:** Change management; User communication; Breaking changes.

---

### 11.2 Tehnilise võla jälgimine

**Nõue:** Tehniline võlg on identifitseeritud ja dokumenteeritud. Kriitilise võla puhul on plaanis parandusmeetmed ja ajastus.
**Nõudetase:** recommended

**Põhjendus:** Technical debt management; Code quality; [Software quality assurance](https://en.wikipedia.org/wiki/Software_quality_assurance); Maintainability.

---

## 12. Compliance ja audit

### 12.1 Auditijälgitavus

**Nõue:** Kõik olulised tegevused (sh konfiguratsiooni muudatused, õiguste muudatused) on audititavalt logitud. Auditilogid on muutmata ja säilitatavad määratud perioodi.
**Nõudetase:** required (osaliselt kaetud 5.1-ga, täiendav rõhk)

**Põhjendus:** [System and Organization Controls](https://en.wikipedia.org/wiki/System_and_Organization_Controls) (SOC 2); [ISO/IEC 27001](https://en.wikipedia.org/wiki/ISO/IEC_27001); Compliance; Forensics.

---

### 12.2 Ligipääsuõiguste ülevaatus

**Nõue:** Kasutajate ja süsteemikontode ligipääsuõigusi ülevaadatakse regulaarselt (nt kord aastas). Üleliigsed õigused eemaldatakse.
**Nõudetase:** expected

**Põhjendus:** Least privilege; Access review; [ISO/IEC 27001](https://en.wikipedia.org/wiki/ISO/IEC_27001) A.9.2.5.

---

## Kokkuvõte

| Kategooria | Uued kandidaadid | Soovituslik taseme jaotus |
|------------|------------------|---------------------------|
| Jõudlus | 3 | 2 expected, 1 expected |
| Kättesaadavus | 2 | expected |
| Privaatsus/GDPR | 3 | 2 required, 1 expected |
| Turvalisus | 4 | 2 required, 1 expected, 1 recommended |
| Observability/SRE | 3 | 1 expected, 2 recommended |
| API disain | 3 | 2 expected, 1 recommended |
| Dokumentatsioon | 2 | 1 expected, 1 recommended |
| Kasutajakogemus | 3 | 1 required, 2 expected/recommended |
| Muudatuste juhtimine | 2 | 1 expected, 1 recommended |
| Andmete haldus | 2 | required |
| Tehniline võlg | 2 | 1 expected, 1 recommended |
| Compliance | 2 | 1 required, 1 expected |
| **Kokku** | **31** | |


## Viidatud standardid ja allikad (Wikipedia jms)

| Standard / kontseptsioon | Viide |
|--------------------------|-------|
| ISO/IEC 25010 (tarkvara kvaliteet) | https://en.wikipedia.org/wiki/ISO/IEC_9126 |
| ITIL | https://en.wikipedia.org/wiki/ITIL |
| DevOps | https://en.wikipedia.org/wiki/DevOps |
| Site Reliability Engineering | https://en.wikipedia.org/wiki/Site_reliability_engineering |
| OWASP | https://en.wikipedia.org/wiki/OWASP |
| GDPR | https://en.wikipedia.org/wiki/General_Data_Protection_Regulation |
| ISO 22301 (BCM) | https://en.wikipedia.org/wiki/ISO_22301 |
| ISO/IEC 27701 (privaatsus) | https://en.wikipedia.org/wiki/ISO/IEC_27701 |
| Content Security Policy | https://en.wikipedia.org/wiki/Content_Security_Policy |
| Cross-site request forgery | https://en.wikipedia.org/wiki/Cross-site_request_forgery |
| Software bill of materials | https://en.wikipedia.org/wiki/Software_bill_of_materials |
| OpenTelemetry | https://opentelemetry.io/ |
| Distributed tracing | https://en.wikipedia.org/wiki/Distributed_tracing |
| Web Content Accessibility Guidelines | https://en.wikipedia.org/wiki/Web_Content_Accessibility_Guidelines |
| RFC 7807 (Problem Details) | https://www.rfc-editor.org/rfc/rfc7807 |
| Circuit breaker pattern | https://en.wikipedia.org/wiki/Circuit_breaker_design_pattern |
| Blue-green deployment | https://en.wikipedia.org/wiki/Blue-green_deployment |
| Continuous delivery | https://en.wikipedia.org/wiki/Continuous_delivery |
| Architectural decision | https://en.wikipedia.org/wiki/Architectural_decision |
| Representational state transfer | https://en.wikipedia.org/wiki/Representational_state_transfer |
| ISO/IEC 27001 | https://en.wikipedia.org/wiki/ISO/IEC_27001 |
| SOC 2 | https://en.wikipedia.org/wiki/System_and_Organization_Controls |
| Twelve-Factor App | https://en.wikipedia.org/wiki/Twelve-Factor_App_methodology |
