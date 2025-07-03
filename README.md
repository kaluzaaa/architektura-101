# Architektura 101

## Spis Treści

### [01. Filozofia i Kultura Architektury](01_filozofia_kultura.md)
### [02. Rola Architekta](02_rola_architekta.md)
### [03. Koszty i Biznes](03_koszty_biznes.md)
### [04. Dokumentacja i Komunikacja](04_dokumentacja_komunikacja.md)
### [05. Modelowanie Architektury](05_modelowanie_architektury.md)
### [06. Architektura i Decyzje](06_architektura_decyzje.md)
### [07. Zarządzanie Konfiguracją](07_zarzadzanie_konfiguracja.md)
### [08. Praktyczne Zasady](08_praktyczne_zasady.md)
### [09. Procesy Deweloperskie](09_procesy_deweloperskie.md)
### [10. Testowanie](10_testowanie.md)
### [11. Bezpieczeństwo - Model Szwajcarskiego Sera](11_bezpieczenstwo_model_szwajcarskiego_sera.md)
### [12. Event-Driven Architecture](12_event_driven_architecture.md)
### [13. Skalowalność i Wysoka Dostępność](13_skalowalnosc_wysoka_dostepnosc.md)
### [14. Technologie i Narzędzia](14_technologie_narzedzia.md)
### [15. AI i Dokumentacja](15_ai_dokumentacja.md)
### [16. Charakterystyki Architektoniczne i Modularność](16_charakterystyki_architektoniczne_modularnosc.md)

---

## **PRAWA ARCHITEKTURY OPROGRAMOWANIA**

### **Pierwsze Prawo Architektury Oprogramowania**
**"Wszystko w architekturze oprogramowania to kompromis"**
- Jeśli architekt myśli, że znalazł coś, co nie jest kompromisem, prawdopodobnie jeszcze nie zidentyfikował tego kompromisu
- Nie istnieją idealne rozwiązania - każde ma swoje wady i zalety
- Umiejętność dostrzegania i analizowania kompromisów (trade-offs) jest kluczowa

### **Drugie Prawo Architektury Oprogramowania**
**"Dlaczego jest ważniejsze niż jak"**
- Ważniejsze jest zapisywanie powodów decyzji architektonicznych niż tylko ich struktury
- **Architecture Decision Records (ADRs)** - narzędzie do dokumentowania decyzji i ich uzasadnień
- Zrozumienie kontekstu i motywacji pomaga w przyszłych modyfikacjach

---

## **CZĘŚĆ I: WHY - DLACZEGO (Fundamenty i Motywacja)**

### **1. Filozofia i Kultura Architektury**
- "Kultura zjada strategię na śniadanie" - najważniejszy czynnik sukcesu
- Teoria wybitych szyb i opór przed zmianami ("Nie ruszaj, bo działa")
- Automatyzacja procesów i eliminacja błędów ludzkich
- Team Topologies i organizacja zespołów - struktura odbija architekturę
- Przezwyciężanie oporu i budowanie kultury zmian
- Przekuwanie wiedzy plemiennej w dokumentację
- **Syndrom Sztokholmski** - akceptacja złych rozwiązań jako "normy"

### **2. Rola Architekta**
- Generalista z szeroką wiedzą, nie tylko kod
- Mentor i coach, nie dyktator - zespół kodujący ma najwięcej do powiedzenia
- "Klej" między zespołami i obszarami (Glue Work)
- Ciągłe zadawanie pytania "dlaczego?" zamiast tylko "jak?"
- Dostosowywanie języka do odbiorcy (techniczny vs biznesowy)
- Staff/Principal Engineer - focus na wpływ i mentoring
- **Wewnętrzny konsultant** - nośnik informacji "co u innych nie wypaliło"
- **Budowanie "chińskiego muru"** - oddzielanie technologii od biznesu gdy potrzeba

### **3. Koszty i Biznes**
- "Follow the money" - zrozum motywację biznesową
- Business Impact Analysis (BIA) - ile kosztuje przestój?
- Kwantyfikacja: transakcje/rok, użytkownicy, wzrost, zasoby
- Każda dodatkowa "dziewiątka" w SLA = wykładniczy wzrost kosztów
- Koszt utrzymania dev > prod environments
- ROI może być ujemne w pierwszym roku (szczególnie AI projekty)
- **Gry statusów i polityka**: walka o budżet, decyzyjność, pokazywanie ważności
- **Nielogiczne procesy biznesowe**: często wynikają z niedopracowania lub ukrytej wiedzy plemiennej
- **"Kupowanie spokoju kosztem logiczności"**: delegowanie ryzyka pieniędzmi, nawet gdy nieoptymalne
- **Polityka klienta**: w projektach musisz radzić sobie z polityką obu stron (swojej i klienta)
- **Pomijanie fazy analizy**: szybka implementacja kosztem zrozumienia wymagań
- **Awersja do OSS contribucji** - "to nie nasz czas sprintu"

## **CZĘŚĆ II: HOW - JAK (Metody i Procesy)**

### **4. Dokumentacja i Komunikacja**
- Markdown w repozytorium > Confluence/Wiki - blisko kodu, łatwiej aktualizować
- Zawsze określ odbiorcę: techniczny vs biznesowy (jedna grupa = jeden dokument)
- Wizualizacje > tekst - ludzie preferują diagramy nad "ściany tekstu"
- ADRy dla ważnych decyzji - "git blame dla architektury"
- Setup Guide - poziom szczegółowości zależy od rotacji w zespole
- AI/LLM jako wsparcie, ale zawsze weryfikuj wyniki
- **Szablony promptów** dla ujednolicenia stylu
- **Automatyczne generowanie TOC** - GitHub Actions

### **5. Modelowanie Architektury**
- **Diagramy C4** - złota zasada: używaj głównie L1 (System Context) i L2 (Container)
- **L3 Component i L4 Code** - zbyt szczegółowe, trudne w utrzymaniu
- **Event Storming** (Exploratory, Big Picture) - warsztatowe odkrywanie procesów biznesowych
- **Diagramy UML**: Sequence Diagrams dla przepływów, Use Case dla procesów biznesowych
- **Swimlanes** - ścieżki biznesowe przez mikroserwisy
- **Deployment Diagramy** - mapowanie kontenerów na infrastrukturę
- **Wardley Maps** - mapowanie strategiczne "commodity vs unique value"
- **Diagram as Code** - Mermaid, PlantUML (renderowane online, w repo)
- **Automatyczne generowanie** diagramów z kodu przez AI/LLM

### **6. Architektura i Decyzje**
- Architektura = odkładanie kosztownych decyzji w czasie
- KISS i YAGNI - prostota ponad skomplikowanie
- Build vs Buy - zazwyczaj kupuj/używaj gotowych dla "commodity"
- Architektura = kompromis - brak idealnych rozwiązań
- Prawo Conwaya - organizacja odzwierciedla architekturę systemów
- CAP Theorem - wybierz 2 z 3: Consistency, Availability, Partition Tolerance
- **"Not Invented Here" syndrome** - chęć budowania wszystkiego samemu
- **"Najmniej zła architektura"** zamiast perfekcji
- **Poziomy dojrzałości M0-M3** - dostosuj do potrzeb biznesowych

### **7. Zarządzanie Konfiguracją**
- **Konfiguracja techniczna vs biznesowa** - fundamentalna różnica!
- **ConfigMaps** (Kubernetes) - tylko dla konfiguracji technicznej, limit 1MB
- **Centralne serwisy** dla konfiguracji biznesowej (listy banków, polityki cenowe)
- **Feature flags** - kontrola funkcjonalności bez deploymentu
- **GUI i audytowanie** dla zmian konfiguracji biznesowej
- **Zarządzanie uprawnieniami** do konfiguracji
- **Problem nadmiaru ConfigMapów** - trudności z zarządzaniem

### **8. Praktyczne Zasady**
- Ewolucyjna architektura - adaptacja do zmieniających się wymagań
- Wspólny język w firmie - must have dla komunikacji
- Definition of Done - formalizacja procesów
- Rotacja ról (Quality Officer) dla odpowiedzialności zespołowej
- **Przekuwanie wiedzy plemiennej** w procesy i dokumentację
- **Unikanie "ułańskiej fantazji"** przez automatyzację
- **Conway's Law przez K** - namespace'y w Kubernetes = struktura organizacyjna
- **Prawo Parkinsona** - praca rozszerza się aby wypełnić dostępny czas
- **Cognitive Load** - zbyt wiele abstrakcji utrudnia pracę deweloperom

### **9. Procesy Deweloperskie**
- CI/CD jako standard - automatyzacja eliminuje błędy ludzkie
- Observability: 3 filary - metryki, logi, tracing
- **RED Method**: Rate, Errors, Duration dla metryk
- Standaryzacja logów (JSON, OpenTelemetry) od początku
- **Logi techniczne vs audytowe** - różne cele, miejsca i częstotliwość
- **Anomaly Detection** - wykrywanie nietypowych zachowań (Prometheus)
- **Alert fatigue** - za dużo alertów = ignorowanie alertów
- Środowiska testowe: anonimizacja danych, kontrola dostępu
- **"Update Hygiene"** - regularne aktualizacje jako podstawa bezpieczeństwa

### **10. Testowanie**
- **Testy jednostkowe** - łatwe do uruchomienia lokalnie (kluczowe dla DX)
- **Testy End-to-End (E2E)** - przez cały system, od UI do bazy
- **Testy manualne** - krytyczne ścieżki biznesowe krok po kroku
- **Format Cucumber/Gherkin** - czytelny dla biznesu i techników
- **Testy bezpieczeństwa**: regularne pen-testy, red teaming, SAST/DAST
- **AI w generowaniu testów** - potencjalna pomoc w tworzeniu scenariuszy
- **Scenariusze testowe** - dane wejściowe, metody wykonania, oczekiwane rezultaty
- **Oznaczanie projektów testowych** w solucji dla łatwej identyfikacji

## **CZĘŚĆ III: WHAT - CO (Konkretne Rozwiązania Techniczne)**

### **11. Bezpieczeństwo - Model Szwajcarskiego Sera**
- Wiele warstw ochrony - każda ma luki, razem chronią
- Używaj sprawdzonych standardów: OWASP Top 10, NIST, CIS Benchmarks
- **STRIDE** - 6 kategorii zagrożeń (Spoofing, Tampering, Repudiation, Info Disclosure, DoS, Privilege Escalation)
- **MITRE ATT&CK** - macierz taktyk i technik atakujących
- Kontroluj ruch wychodzący - często pomijane! (zapobieganie exfiltracji)
- Walidacja na API Gateway poziomie - OpenAPI/Swagger schematy
- Zarządzanie sekretami centralnie - NIE hardkoduj w kodzie
- Mikrosegmentacja sieci i mTLS między serwisami
- **SBOM (Software Bill of Materials)** - zarządzanie zależnościami
- **Zero Trust** - nie ufaj, weryfikuj wszystko

### **12. Event-Driven Architecture**
- **CloudEvents** - standardy formatowania eventów
- **Outbox Pattern** - atomiczna transakcja: zapis do bazy + wysyłka na kolejkę
- **Inbox Pattern** - ochrona przed ponownym przetwarzaniem wiadomości
- **Idempotencja** - system radzi sobie z wielokrotnym przetwarzaniem tej samej wiadomości
- **Event Sourcing** - przechowywanie eventów jako źródło prawdy
- **Gwarancja dostarczenia** - różne strategie (retries, outbox, acknowledgments)
- **Eventual Consistency** - akceptacja przejściowych niespójności
- **Rate Limiting i kolejki priorytetowe** - slow/fast queues
- **Problem "wszystko wysokim priorytetem"** = nic nie ma priorytetu

### **13. Skalowalność i Wysoka Dostępność**
- Kwantyfikuj skalę - liczby są kluczowe dla decyzji
- Różnica HA vs DR: lokalne awarie vs katastrofy regionalne
- **RPO (Recovery Point Objective)** - maksymalna utrata danych
- **RTO (Recovery Time Objective)** - maksymalny czas przywrócenia
- SLA < SLO < rzeczywista dostępność (bufor na awarie)
- **Composite SLA**: dostępność = iloczyn komponentów (3x99.9% = ~99.7%)
- Złożoność obniża dostępność całego systemu
- **Capacity Planning** - przewidywanie potrzebnych zasobów
- **KEDA** - autoskalowanie na podstawie długości kolejek
- **Deployment Stamps** - replikacja całych środowisk

### **14. Technologie i Narzędzia**
- **Kubernetes zarządzany** (EKS, AKS, GKE) > on-premise dla łatwiejszego dzielenia zasobów
- **Cloud dla startupów** (szybkość, elastyczność) vs **on-premise dla enterprise** (koszty długoterminowe)
- **PostgreSQL jako uniwersalne rozwiązanie** - "PostgreSQL do wszystkiego" (Revolut)
- **Service Mesh** (Istio) - mTLS, routing, observability "out-of-the-box", ale uwaga na complexity
- **Loki vs ELK**: prostota i cardinality vs full-text search i funkcjonalność
- **Cert-Manager** - automatyczne zarządzanie certyfikatami w Kubernetes
- **Network Policies** - mikrosegmentacja w Kubernetes
- **Trivy** - skanowanie kontenerów i konfiguracji pod kątem podatności
- **Rundeck** - automatyzacja operacji IT
- **GitOps** - ArgoCD, Flagger dla progressive delivery

### **15. AI i Automatyzacja Dokumentacji**
- Wykorzystanie AI do generowania diagramów (Mermaid, C4) z kodu
- **Szablony promptów** dla ujednolicenia stylu dokumentacji
- **Prompt Engineering** - precyzyjne instrukcje dla lepszych wyników
- Analizy stack trace i przepływów kodu przez AI
- **System prompts** dla konsystentnych rezultatów
- **Vibe Coding** - AI wspomagane prototypowanie i eksploracja
- **Przełamywanie blokady twórczej** - AI pomaga ruszyć z miejsca
- **Krytyczne podejście** - AI może "przewalać" lub nadmiernie przytakiwać
- **Custom Instructions** - GitHub Copilot, Cursor Rules
- **Weryfikacja wyników** - AI jako narzędzie, nie zamiennik myślenia

---

## Polecane Książki

### **Architektura Oprogramowania**

**1. Fundamentals of Software Architecture: An Engineering Approach**
- **Autorzy:** Mark Richards, Neal Ford
- **ISBN:** 9781492043454
- **Link:** [Amazon](https://www.amazon.com/Fundamentals-Software-Architecture-Comprehensive-Characteristics/dp/1492043451)
- Kompleksowy przewodnik po architekturze oprogramowania z praktycznym podejściem inżynierskim

**2. Enterprise Integration Patterns: Designing, Building, and Deploying Messaging Solutions**
- **Autorzy:** Gregor Hohpe, Bobby Woolf
- **ISBN:** 9780321200686
- **Link:** [Amazon](https://www.amazon.com/Enterprise-Integration-Patterns-Designing-Deploying/dp/0321200683)
- Katalog 65 wzorców integracji przedsiębiorstwa z rzeczywistymi rozwiązaniami

**3. Master Software Architecture**
- **Autor:** Maciej Jedrzejewski
- **Link:** [mastersoftwarearchitecturebook.com](https://mastersoftwarearchitecturebook.com/)
- Praktyczny przewodnik po rzeczywistej architekturze oprogramowania z wieloma diagramami i przykładami

**4. Building Evolutionary Architectures: Support Constant Change**
- **Autorzy:** Neal Ford, Rebecca Parsons, Patrick Kua
- **ISBN:** 9781491986363
- **Link:** [Amazon](https://www.amazon.com/Building-Evolutionary-Architectures-Support-Constant/dp/1491986360)
- Przewodnik po tworzeniu architektur, które mogą się stale zmieniać i ewoluować

**5. Building Evolutionary Architectures, 2nd Edition**
- **Autorzy:** Neal Ford, Rebecca Parsons, Patrick Kua, Pramod Sadalage
- **ISBN:** 9781492097549
- **Link:** [O'Reilly](https://www.oreilly.com/library/view/building-evolutionary-architectures/9781492097532/)
- Zaktualizowana wersja klasycznej książki o architekturach ewolucyjnych

**6. Software Architecture: The Hard Parts**
- **Autorzy:** Neal Ford, Mark Richards, Pramod Sadalage, Zhamak Dehghani
- **ISBN:** 9781492086895
- **Link:** [Amazon](https://www.amazon.com/Software-Architecture-Trade-Off-Distributed-Architectures/dp/1492086894)
- Analiza kompromisów i trudnych decyzji w architekturach rozproszonych

### **DevOps i Kultura**

**7. The Phoenix Project: A Novel About IT, DevOps, and Helping Your Business Win**
- **Autorzy:** Gene Kim, Kevin Behr, George Spafford
- **ISBN:** 9780988262591
- **Link:** [Amazon](https://www.amazon.com/Phoenix-Project-DevOps-Helping-Business/dp/0988262592)
- Powieść biznesowa wprowadzająca zasady DevOps i "Trzy Drogi"

**8. The Unicorn Project: A Novel about Developers, Digital Disruption, and Thriving in the Age of Data**
- **Autor:** Gene Kim
- **ISBN:** 9781942788768
- **Link:** [Amazon](https://www.amazon.com/Unicorn-Project-Developers-Disruption-Thriving/dp/1942788762)
- Kontynuacja Phoenix Project z perspektywy deweloperów, wprowadzająca "Pięć Ideałów"

**9. The DevOps Handbook: How to Create World-Class Agility, Reliability, and Security in Technology Organizations**
- **Autorzy:** Gene Kim, Jez Humble, Patrick Debois, John Willis, Nicole Forsgren
- **ISBN:** 9781950508402
- **Link:** [Amazon](https://www.amazon.com/DevOps-Handbook-World-Class-Reliability-Organizations/dp/1950508404)
- Praktyczny przewodnik po implementacji praktyk DevOps w organizacji

**10. Accelerate: The Science of Lean Software and DevOps**
- **Autorzy:** Nicole Forsgren, Jez Humble, Gene Kim
- **ISBN:** 9781942788331
- **Link:** [Amazon](https://www.amazon.com/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339)
- Naukowe podejście do mierzenia wydajności zespołów deweloperskich - zwycięzca Shingo Publication Award

### **Strony Autorów**
- **Neal Ford:** [nealford.com](https://nealford.com)
- **Gregor Hohpe:** [enterpriseintegrationpatterns.com](https://www.enterpriseintegrationpatterns.com/gregor.html)
- **Mark Richards:** [DeveloperToArchitect.com](http://DeveloperToArchitect.com)

---

## Najważniejsze Narzędzia i Frameworki

### **Frameworks i Standardy**
- **OWASP**: https://owasp.org/www-project-top-ten/
- **NIST Cybersecurity**: https://www.nist.gov/cyberframework
- **CIS Benchmarks**: https://www.cisecurity.org/cis-benchmarks
- **Arc42 Templates**: https://arc42.org/
- **MITRE ATT&CK**: https://attack.mitre.org/

### **Narzędzia i Technologie**
- **CNCF Landscape**: https://landscape.cncf.io/
- **Trivy Scanner**: https://github.com/aquasecurity/trivy
- **Grafana Observability**: https://grafana.com/docs/loki/latest/
- **Cert-Manager**: https://cert-manager.io/
- **CloudEvents**: https://cloudevents.io/

### **Event-Driven i Patterns**
- **Outbox Pattern**: https://www.kamilgrzybek.com/blog/posts/the-outbox-pattern
- **Event-Driven.io**: https://event-driven-io.github.io/emmett/overview.html
- **Enterprise Integration Patterns**: https://www.enterpriseintegrationpatterns.com/

### **Metodyki i Praktyki**
- **Wardley Maps**: https://learnwardleymapping.com/
- **Architecture Katas**: https://nealford.com/katas/
- **Hacker Laws**: https://github.com/dwmkerr/hacker-laws
- **RED Method**: https://grafana.com/blog/2018/08/02/the-red-method-how-to-instrument-your-services/

---

## Szybkie Przypomnienie - Top 24 Takeaways

### **WHY - DLACZEGO:**
1. **Kultura > Strategia** - najważniejszy czynnik sukcesu
2. **Architekt = Mentor** - nie dyktator, wspiera zespoły
3. **"Follow the money"** - zrozum prawdziwą motywację biznesową
4. **Gry statusów i polityka** - wpływają na decyzje architektoniczne
5. **Kwantyfikuj wszystko** - liczby są podstawą decyzji
6. **"Dlaczego" > "Jak"** - zrozum cel przed implementacją

### **HOW - JAK:**
7. **Markdown w repo** - najlepsza dokumentacja blisko kodu
8. **C4 L1+L2** - złota zasada modelowania architektury
9. **Konfiguracja techniczna ≠ biznesowa** - fundamentalna różnica
10. **"Najmniej zła architektura"** - kompromis, nie perfekcja
11. **Observability = 3 filary** - metryki, logi, tracing
12. **Testuj logikę biznesową** - unit testy dla wartości biznesowej, znajdź kompromis między pokryciem a kosztem
13. **ADRy dla ważnych decyzji** - dokumentuj "dlaczego", nie tylko "co"
14. **Build vs Buy** - zazwyczaj kupuj gotowe rozwiązania
15. **Conway's Law** - organizacja odzwierciedla architekturę
16. **KISS i YAGNI** - prostota ponad skomplikowanie

### **WHAT - CO:**
17. **Asynchroniczność > synchroniczność** - event-driven jako domyślne podejście
18. **Managed > self-hosted** - deleguj infrastrukturę, focus na biznes
19. **Observability-first** - widzialność przed optymalizacją
20. **Defense in depth** - bezpieczeństwo wielowarstwowe
21. **Commodity tech choices** - PostgreSQL, Kubernetes, sprawdzone rozwiązania
22. **Configuration as code** - wszystko w repozytorium, nic ad-hoc
23. **Automation over processes** - kod zamiast procedur
24. **Tools amplify thinking** - AI/tooling jako wzmacniacz, nie zamiennik
