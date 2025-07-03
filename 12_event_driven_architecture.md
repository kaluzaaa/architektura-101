# 12. Event-Driven Architecture - Rozszerzony TL;DR

## 🎯 Kluczowe Koncepty

**Event-Driven Architecture (EDA)** to wzorzec architektoniczny, w którym **eventy stanowią główny mechanizm komunikacji** między serwisami. Zamiast bezpośredniego wywoływania funkcji, serwisy publikują eventy o tym, co się stało, a inne serwisy mogą reagować na te eventy.

**CloudEvents** - międzynarodowy standard formatowania eventów, który definiuje wspólny format dla eventów niezależnie od dostawcy czy platformy. Zapewnia interoperacyjność między różnymi systemami.

**Outbox Pattern** - wzorzec gwarantujący **atomiczną transakcję** między zapisem do bazy danych a wysłaniem wiadomości na kolejkę. Eliminuje ryzyko utraty eventów.

**Inbox Pattern** - mechanizm chroniący przed **ponownym przetwarzaniem tej samej wiadomości** (duplicate handling). Zapewnia, że każdy event zostanie przetworzony dokładnie raz.

**Idempotencja** - właściwość systemu, dzięki której **wielokrotne przetwarzanie tej samej wiadomości nie powoduje negatywnych skutków**. Kluczowa w systemach rozproszonych.

**Event Sourcing** - wzorzec, w którym **eventy są przechowywane jako źródło prawdy** zamiast aktualnego stanu. Pozwala na odtworzenie stanu systemu w dowolnym momencie. UWAZAJ - to nie jest łatwe.

**Eventual Consistency** - model spójności akceptujący **przejściowe niespójności** w systemie, z gwarancją, że w końcu wszystkie kopie danych będą spójne.

## ⚡ Najważniejsze Zasady

**Asynchroniczność > synchroniczność**: Event-driven jako domyślne podejście eliminuje blokowanie operacji i zwiększa odporność systemu.

**"Fire and forget" z gwarancjami**: Serwis publikuje event i nie czeka na potwierdzenie przetworzenia, ale system gwarantuje dostarczenie.

**Idempotencja jest obowiązkowa**: "System radzi sobie z wielokrotnym przetwarzaniem tej samej wiadomości" - każdy handler eventów musi być idempotentny.

**Eventual Consistency**: "Akceptacja przejściowych niespójności" - system może być chwilowo niespójny, ale w końcu osiągnie spójność.

**Atomiczność operacji**: Outbox Pattern zapewnia, że "zapis do bazy + wysyłka na kolejkę" to jedna atomiczna operacja.

## 🚨 Typowe Problemy i Rozwiązania

**Problem: Utrata eventów**
- **Rozwiązanie**: Outbox Pattern - "atomiczna transakcja: zapis do bazy + wysyłka na kolejkę"
- Event jest najpierw zapisywany w bazie danych, a następnie wysyłany na kolejkę przez background job

**Problem: Duplikacja eventów**
- **Rozwiązanie**: Inbox Pattern + idempotencja
- Każdy event ma unikalny ID, system sprawdza czy już przetworzył ten event

**Problem: "Wszystko wysokim priorytetem"**
- **Cytat**: "Problem 'wszystko wysokim priorytetem' = nic nie ma priorytetu"
- **Rozwiązanie**: Slow/Fast queues - różne kolejki dla różnych priorytetów

**Problem: Brak gwarancji dostarczenia**
- **Rozwiązanie**: "Różne strategie (retries, outbox, acknowledgments)"
- Implementacja mechanizmów retry z exponential backoff

**Problem: Ordering eventów**
- **Rozwiązanie**: Partycjonowanie kolejek po kluczach biznesowych
- Eventy dla tego samego klienta zawsze trafiają do tej samej partycji

## 🛠️ Narzędzia i Technologie

**CloudEvents** - https://cloudevents.io/
- standard formatowania eventów
- Wsparcie dla różnych formatów (JSON, Avro, Protocol Buffers)
- Integracja z głównymi dostawcami chmury

**Apache Kafka**
- Najbardziej popularna platforma do event streaming
- Wysokie throughput, partycjonowanie, replikacja
- Idealna do high-volume event processing

**Apache Pulsar**
- Alternatywa dla Kafka z lepszą separacją storage/compute
- Multi-tenancy, geo-replication

**RabbitMQ**
- Message broker z szerokim wsparciem wzorców messagingu
- Prostszy niż Kafka, ale mniejsze throughput

**Azure Event Hub / AWS EventBridge / Google Cloud Pub/Sub**
- Zarządzane usługi event streaming w chmurze
- Automatyczne skalowanie, integracja z ekosystemem chmury

## 📝 Przykłady z Materiałów

**Outbox Pattern w praktyce**:
"Gwarantuje dostarczalność wiadomości, zapewniając, że wiadomość zostanie zapisana do bazy danych, zanim zostanie wysłana do kolejki."

**Event-Driven jako standard**:
"Często stosuje się podejście low-level, skupiając się na konkretnych technologiach i wzorcach już na etapie projektowania systemu, np. dla centralnego gateway'a do webhooków."

**Praktyczne zastosowanie**:
"Projektowanie 'w locie' jest praktyką dostosowania się do zwinności, pilnując pierwotnych założeń."

## ✅ Checklista Do Działania

### Projektowanie Event-Driven System
- [ ] Zdefiniuj schema eventów zgodnie z CloudEvents
- [ ] Zaplanuj strategię partycjonowania eventów
- [ ] Zaprojektuj idempotentne handlery eventów
- [ ] Określ poziomy spójności dla poszczególnych operacji

### Implementacja Outbox Pattern
- [ ] Stwórz tabelę outbox w bazie danych
- [ ] Zaimplementuj transakcyjny zapis: business logic + outbox
- [ ] Dodaj background job do publikowania eventów z outbox
- [ ] Ustaw monitoring długości kolejki outbox

### Zapewnienie Idempotencji
- [ ] Dodaj unikalne ID do każdego eventu
- [ ] Zaimplementuj mechanizm deduplication
- [ ] Przetestuj obsługę duplikatów eventów
- [ ] Ustaw TTL dla zapisów deduplication

### Monitoring i Alerting
- [ ] Monitoruj lag konsumerów eventów
- [ ] Ustaw alerty na długie kolejki
- [ ] Śledź failure rate przetwarzania eventów
- [ ] Monitoruj end-to-end latency eventów

### Zarządzanie Schematami
- [ ] Użyj Schema Registry dla ewolucji schematów
- [ ] Zaplanuj backwards compatibility
- [ ] Wersjonuj eventy zgodnie z semantic versioning
- [ ] Przetestuj migracje schematów

## 🔗 Dodatkowe Zasoby

**Standardy i Specifications**:
- [CloudEvents Specification](https://cloudevents.io/) - oficjalna specyfikacja
- [AsyncAPI](https://www.asyncapi.com/en) - dokumentacja API dla event-driven architecture

**Wzorce i Best Practices**:
- [The Outbox Pattern](https://www.kamilgrzybek.com/blog/posts/the-outbox-pattern) - szczegółowy opis wzorca
- [Event-Driven.io](https://event-driven-io.github.io/emmett/overview.html) - framework i wzorce Event Sourcing
- [Enterprise Integration Patterns](https://www.enterpriseintegrationpatterns.com/) - katalog wzorców integracji

**Webhook Infrastructure**:
- [Webhook Infrastructure Components](https://hookdeck.com/webhooks/guides/webhook-infrastructure-components-and-their-functions) - kompendium webhook'ów

**Implementacje Reference**:
- [Emmett Framework](https://github.com/event-driven-io/emmett/tree/main/src/docs/.vitepress) - Event Sourcing w praktyce
- [Patoarchitekci #152](https://patoarchitekci.io/152/) - polski podcast o architekturze

**Zasady Projektowania**:
- [Removability over Maintainability](https://event-driven.io/en/removability_over_maintainability/) - filozofia projektowania
- [Vertical Slices in Practice](https://event-driven.io/en/vertical_slices_in_practice/) - organizacja kodu w event-driven systems

**Monitoring i Observability**:
- [RED Method](https://grafana.com/blog/2018/08/02/the-red-method-how-to-instrument-your-services/) - Rate, Errors, Duration dla event-driven systemów
