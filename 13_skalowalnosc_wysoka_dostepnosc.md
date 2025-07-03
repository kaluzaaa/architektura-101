# 13. Skalowalność i Wysoka Dostępność - Rozszerzony TL;DR

## 🎯 Kluczowe Koncepty

### Różnica między HA i DR
- **Wysoka Dostępność (HA)** - ochrona przed **lokalnymi awariami** (serwer, strefa dostępności)
- **Disaster Recovery (DR)** - odzyskiwanie po **katastrofach** (padnięcie całego regionu)
- **Availability Zones** w chmurze - idealne dla HA, replikacja między regionami dla DR

### Metryki Dostępności
- **RPO (Recovery Point Objective)** - maksymalna akceptowalna utrata danych ("ile danych możemy stracić?")
- **RTO (Recovery Time Objective)** - maksymalny akceptowalny czas przywrócenia ("jak szybko musimy wrócić?")
- **SLI → SLO → SLA** - hierarchia celów (konkretna metryka → wewnętrzny cel → umowa z klientem)

### CAP Theorem
Wybierz tylko 2 z 3:
- **Consistency** (spójność danych)
- **Availability** (dostępność systemu)  
- **Partition Tolerance** (tolerancja partycji sieciowych)

### Composite SLA
**Dostępność całej usługi = iloczyn dostępności komponentów**
- 3 serwisy po 99.9% = ~99.7% całego systemu
- Złożoność architektury obniża skumulowaną dostępność

## 💡 Praktyczne Zastosowania

### Kwantyfikacja Skali
**Podstawowe pytania biznesowe:**
- "Jaka jest przewidywana liczba aktywnych użytkowników (dziennie, miesięcznie)?"
- "Ile operacji na sekundę system będzie musiał obsłużyć?"
- "Jaki jest oczekiwany roczny wzrost finansowy?"
- "Ile kosztuje firma godzina przestoju danego systemu?"

**Analiza techniczna:**
- Wielkość rekordów i struktur danych
- Operacje na sekundę (IOPS)
- Przewidywanie zasobów (CPU, RAM, dyski)
- Szacowanie kosztów infrastruktury

### Zarządzanie Przepustowością
**Rate Limiting i Kolejki:**
- Implementacja na poziomie load balancera lub serwisu
- **Slow/Fast queues** - różne priorytety wiadomości
- **KEDA** - autoskalowanie na podstawie długości kolejek
- Problem: "wszystko wysokim priorytetem" = nic nie ma priorytetu

### Mikroserwisy i Skalowanie
- **Autoskalowanie** poszczególnych komponentów
- **Swimlanes** - wizualizacja przepływów biznesowych przez mikroserwisy
- **Capacity Planning** - przewidywanie potrzebnych zasobów

## ⚡ Najważniejsze Zasady

### 1. Kwantyfikuj Wszystko
> "Liczby są ważne" - bez kwantyfikacji nie ma dobrych decyzji architektonicznych

### 2. SLA < SLO < Rzeczywista Dostępność
- Zawsze zostaw bufor na nieprzewidziane awarie
- Każda dodatkowa "dziewiątka" w SLA = wykładniczy wzrost kosztów

### 3. Idempotencja w Systemach Rozproszonych
- System musi radzić sobie z wielokrotnym przetwarzaniem tej samej wiadomości
- Niezbędne dla gwarancji dostarczenia

### 4. Outbox Pattern dla Krytycznych Systemów
- **Atomiczna transakcja**: zapis do bazy + wysyłka na kolejkę
- Potwierdzenie (HTTP 200) po zapisie w bazie
- Wysyłka może być ponawiana w tle

### 5. Eventual Consistency
- Akceptacja przejściowych niespójności
- Strategia "Last write wins" vs złożone reguły biznesowe

## 🚨 Typowe Problemy i Rozwiązania

### Problem: Złożoność Obniża Dostępność
**Wyzwanie:** Więcej komponentów = więcej punktów awarii
**Rozwiązanie:** 
- Upraszczanie architektury gdzie to możliwe
- Eliminowanie niepotrzebnych zależności
- Monitoring całego łańcucha zależności

### Problem: Przewymiarowanie ("Wishful Thinking")
**Wyzwanie:** Nierealistyczne założenia o skali
**Rozwiązanie:**
- Dokładna kwantyfikacja na podstawie danych biznesowych
- Iteracyjne modelowanie i weryfikacja założeń
- Rozpoczęcie od MVP i stopniowe skalowanie

### Problem: Brak Gwarancji Dostarczenia
**Wyzwanie:** Utrata wiadomości przy awariach
**Rozwiązanie:**
- Implementacja Outbox Pattern
- Retry mechanism z exponential backoff
- Monitoring i alerting na poziomie kolejek

### Problem: Alert Fatigue
**Wyzwanie:** Za dużo alertów = ignorowanie problemów
**Rozwiązanie:**
- Hierarchia alertów (krytyczne vs informacyjne)
- Anomaly Detection zamiast stałych progów
- Inteligentne grupowanie alertów

## 🛠️ Narzędzia i Technologie

### Monitoring i Observability
- **Prometheus** - metryki i alerting
- **Grafana** - wizualizacja metryk
- **Loki** - strukturalne logowanie z dobrą skalowalnością
- **RED Method** - Rate, Errors, Duration dla metryk aplikacyjnych

### Autoskalowanie i Orchestracja
- **KEDA** - autoskalowanie na podstawie kolejek w Kubernetes
- **Managed Kubernetes** (EKS, AKS, GKE) - łatwiejsze dzielenie zasobów
- **Deployment Stamps** - replikacja całych środowisk

### Load Balancing i Traffic Management
- **Rate Limiting** na poziomie API Gateway
- **Circuit Breaker Pattern** - ochrona przed kaskadowymi awariami
- **Blue-Green Deployment** - bezpieczne wdrożenia

### Bazy Danych i Persistence
- **PostgreSQL** - "do wszystkiego" (przykład Revolut)
- **Replikacja synchroniczna vs asynchroniczna**
- **Multi-region** - wykorzystanie chmury do DR

## 📝 Przykłady z Materiałów

### Case Study: Cloudflare
> "55 million requests/sec with 15 PostgreSQL clusters"

**Kluczowe learnings:**
- Distributed PostgreSQL architecture
- Inteligentne cachowanie i CDN
- Geograficzna dystrybucja ruchu

### Case Study: Monzo
> "Tolerating full cloud outages with Monzo stand-in"

**Kluczowe learnings:**
- Processing payments during outages
- Graceful degradation funkcjonalności
- Backup systems for critical operations

### Praktyczny Przykład: Kwantyfikacja Kosztów
"Każda dodatkowa 'dziewiątka' w SLA zwiększa koszty"
- 99.9% → infrastruktura x2, development +20%
- 99.99% → development może wzrosnąć x10
- Uzasadnienie biznesowe każdego poziomu dostępności

## ✅ Checklista Do Działania

### Analiza Wymagań
- [ ] Określ różnicę między wymaganiami HA i DR
- [ ] Zdefiniuj RPO i RTO dla krytycznych procesów
- [ ] Oszacuj koszt przestoju dla każdego systemu
- [ ] Ustal hierarchię SLI → SLO → SLA

### Projektowanie Architektury
- [ ] Zaimplementuj Outbox Pattern dla krytycznych operacji
- [ ] Zapewnij idempotencję we wszystkich operacjach
- [ ] Zaplanuj strategię replikacji (synchroniczna vs asynchroniczna)
- [ ] Uwzględnij Composite SLA w kalkulacjach dostępności

### Kwantyfikacja i Planowanie
- [ ] Policz operacje na sekundę dla szczytowego obciążenia
- [ ] Oszacuj potrzebne zasoby (CPU, RAM, dyski)
- [ ] Zaplanuj capacity planning z przewidywanym wzrostem
- [ ] Przygotuj model kosztów dla różnych poziomów dostępności

### Monitoring i Alerting
- [ ] Zaimplementuj RED Method (Rate, Errors, Duration)
- [ ] Ustaw alerting na poziomie SLO, nie SLA
- [ ] Skonfiguruj anomaly detection
- [ ] Unikaj alert fatigue - hierarchia alertów

### Testowanie i Weryfikacja
- [ ] Przetestuj scenariusze awarii (chaos engineering)
- [ ] Zweryfikuj czasy odzyskiwania (RTO)
- [ ] Sprawdź rzeczywistą utratę danych (RPO)
- [ ] Przeprowadź disaster recovery drills

## 🔗 Dodatkowe Zasoby

### Case Studies i Architektury
- [Cloudflare: 55M requests/sec with PostgreSQL](https://dev.to/devangtomar/how-cloudflare-achieved-55-million-requests-per-second-with-just-15-postgresql-clusters-3mm8)
- [Cloudflare's Distributed PostgreSQL](https://www.infoq.com/articles/cloudflare-distributed-postgres/)
- [Monzo: Tolerating Cloud Outages](https://monzo.com/blog/tolerating-full-cloud-outages-with-monzo-stand-in)
- [Monzo: Processing Payments During Outages](https://monzo.com/blog/processing-payments-in-monzo-stand-in)

### Metryki i SLA
- [Calculating Composite SLA](https://alexewerlof.medium.com/calculating-composite-sla-d855eaf2c655)
- [Azure Well-Architected: Understanding SLAs](https://learn.microsoft.com/en-us/azure/well-architected/reliability/metrics#understand-service-level-agreements)
- [SLA in Cloud Computing](https://www.subhendumct.com/2019/04/01/sla-in-cloud/)

### Patterns i Best Practices
- [The Outbox Pattern](https://www.kamilgrzybek.com/blog/posts/the-outbox-pattern)
- [CloudEvents Standards](https://cloudevents.io/)
- [Event-Driven.io Framework](https://event-driven-io.github.io/emmett/overview.html)

### Narzędzia i Technologie
- [RED Method Monitoring](https://grafana.com/blog/2018/08/02/the-red-method-how-to-instrument-your-services/)
- [Prometheus Anomaly Detection](https://about.gitlab.com/blog/anomaly-detection-using-prometheus/)
- [CNCF Landscape](https://landscape.cncf.io/)

### Cosmos DB i Consistency
- [Azure Cosmos DB Consistency Levels](https://learn.microsoft.com/en-us/azure/cosmos-db/consistency-levels)
- [Cosmos DB Conflict Resolution](https://learn.microsoft.com/en-us/azure/cosmos-db/conflict-resolution-policies)

---

**💡 Kluczowy Takeaway:**
Skalowalność i wysoka dostępność to nie kwestia technologii, ale **biznesowego uzasadnienia i świadomego kompromisu** między kosztem a wymaganiami. Kwantyfikacja i "follow the money" pomagają podejmować właściwe decyzje architektoniczne.