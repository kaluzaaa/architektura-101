# 10. Testowanie - Rozszerzony TL;DR

## 🎯 Kluczowe Koncepty

**Testowanie jako fundament jakości** - różnorodne poziomy testów mają różne cele i wymagania. Kluczowe jest zrozumienie, że **nie wszystkie testy są równe** - każdy poziom ma swoje miejsce w piramidzie testów.

**Piramida testowania** - klasyczny model wskazuje hierarchię:
- **Testy jednostkowe** (unit tests) - podstawa piramidy, najszybsze i najłatwiejsze
- **Testy integracyjne** - testowanie współpracy komponentów
- **Testy end-to-end** - najwolniejsze ale najbardziej realistyczne
- **Testy manualne** - krytyczne ścieżki biznesowe wymagające ludzkiej weryfikacji

**Developer Experience (DX)** - "Łatwe do uruchomienia lokalnie" jest kluczowe dla adopcji testów przez deweloperów. Testy, które wymagają skomplikowanej konfiguracji, będą ignorowane.

## 💡 Praktyczne Zastosowania

**Scenariusze testowe z rzeczywistymi danymi**:
- Tworzenie "dokumentu testing" z najbardziej krytycznymi scenariuszami
- Każdy scenariusz zawiera: dane wejściowe, metody wykonania, oczekiwane rezultaty
- Przykład: "Strzelanie do API z Postmanem/cURLem" z konkretnymi payloadami

**Oznaczanie projektów testowych w solucji** - praktyczny trick dla łatwiejszej identyfikacji i uruchamiania testów.

**Formatowanie w stylu Cucumber/Gherkin** - czytelne dla biznesu i techników:
```gherkin
Given użytkownik ma konto z saldem 1000 PLN
When wykonuje przelew na 150 PLN
Then saldo powinno wynosić 850 PLN
And powinna zostać utworzona transakcja wychodzaca
```

## ⚡ Najważniejsze Zasady

**"Testuj logikę biznesową, nie implementację"** - koncentruj się na zachowaniu systemu, nie na wewnętrznych szczegółach implementacji.

**"Smooth test" vs funkcjonalne vs regresyjne** - trzy typy testów manualnych:
- **Smooth test** - "szczęśliwa ścieżka" bez błędów
- **Testy funkcjonalne** - weryfikacja konkretnych funkcji
- **Testy regresyjne** - sprawdzanie czy nowe zmiany nie zepsuly istniejących funkcji

**Bezpieczeństwo testów**:
- "Anonimizacja danych wrażliwych na środowiskach testowych"
- "Unikanie wystawiania środowisk testowych do internetu"
- Oddzielna kontrola dostępu dla każdego środowiska

## 🚨 Typowe Problemy i Rozwiązania

**Problem: Testy E2E są złożone i niestabilne**
- *Rozwiązanie*: Nie traktuj ich jako standardu, ale dokumentuj ich istnienie
- Uruchamiaj je rzadziej, ale w kluczowych momentach (przed releasem)

**Problem: Za mało testów jednostkowych**
- *Rozwiązanie*: Skoncentruj się na pokryciu krytycznych ścieżek biznesowych, nie na 100% coverage
- Znajdź kompromis między pokryciem a kosztem utrzymania

**Problem: Testy bezpieczeństwa są pomijane**
- *Rozwiązanie*: Zintegruj SAST/DAST z CI/CD pipeline
- Regularne pen-testy i red teaming jako część procesu

**Problem: Przestarzałe środowiska testowe**
- *Rozwiązanie*: "Update Hygiene" - regularne aktualizacje jak w produkcji
- Szczególnie ważne po incydentach typu Log4j

## 🛠️ Narzędzia i Technologie

**Testy bezpieczeństwa**:
- **SAST** (Static Application Security Testing) - analiza kodu źródłowego
- **DAST** (Dynamic Application Security Testing) - testowanie działającej aplikacji
- **SonarQube** - kompleksowa analiza jakości kodu
- **Trivy** - skanowanie kontenerów i zależności

**Automatyzacja testów**:
- **Cucumber/Gherkin** - format czytelny dla biznesu
- **Postman/Newman** - automatyzacja testów API
- **GitHub Actions** - CI/CD pipeline z testami

**Monitorowanie i alerty**:
- **Anomaly Detection** - wykrywanie nietypowych zachowań
- **Prometheus** - "tanio kosztowe" rozwiązanie do monitorowania
- **Alert fatigue** - problem zbyt wielu alertów prowadzący do ich ignorowania

## 📝 Przykłady z Materiałów

**Cytat o Developer Experience**:
> "Testy jednostkowe są podstawą i powinny być możliwe do uruchomienia lokalnie bez większych problemów"

**Praktyczny przykład scenariusza testowego**:
> "Scenariusze powinny zawierać krótkie, krok po kroku instrukcje, dane wejściowe, metody wykonania (np. strzelanie do API z Postmanem/cURLem) oraz oczekiwane rezultaty"

**O środowiskach testowych**:
> "W bankach i instytucjach finansowych często wymuszone przez regulatorów (np. KNF) dokumentacja procesu aktualizacji"

## ✅ Checklista Do Działania

### Przed rozpoczęciem testowania:
- [ ] Zdefiniuj krytyczne ścieżki biznesowe
- [ ] Stwórz "dokument testing" z najważniejszymi scenariuszami
- [ ] Skonfiguruj środowiska testowe z anonimizowanymi danymi
- [ ] Oznacz projekty testowe w solucji

### Testy jednostkowe:
- [ ] Upewnij się, że testy działają lokalnie bez konfiguracji
- [ ] Pokryj krytyczne ścieżki biznesowe
- [ ] Unikaj testowania implementacji - testuj zachowanie
- [ ] Zautomatyzuj uruchamianie w CI/CD

### Testy bezpieczeństwa:
- [ ] Zintegruj SAST/DAST z pipeline'em
- [ ] Zaplanuj regularne pen-testy
- [ ] Skanuj zależności pod kątem podatności
- [ ] Waliduj dane wejściowe na poziomie API Gateway

### Testy E2E:
- [ ] Przygotuj krytyczne scenariusze biznesowe
- [ ] Użyj formatu Cucumber/Gherkin dla czytelności
- [ ] Uruchamiaj przed ważnymi releasami
- [ ] Dokumentuj proces i wymagania

### Monitorowanie:
- [ ] Skonfiguruj podstawowe metryki (RED Method)
- [ ] Ustaw alerty dla krytycznych problemów
- [ ] Unikaj "alert fatigue" - tylko ważne alerty
- [ ] Monitoruj status wiadomości w systemie

## 🔗 Dodatkowe Zasoby

**Dokumentacja i standardy**:
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [NIST SP 800-190](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-190.pdf) - Container Security
- [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks) - konfiguracje zabezpieczeń

**Narzędzia**:
- [Trivy Scanner](https://github.com/aquasecurity/trivy) - skanowanie kontenerów
- [SonarQube](https://www.sonarqube.org/) - analiza jakości kodu
- [Postman](https://www.postman.com/) - testowanie API
- [Cucumber](https://cucumber.io/) - BDD framework

**Metodyki**:
- [RED Method](https://grafana.com/blog/2018/08/02/the-red-method-how-to-instrument-your-services/) - Rate, Errors, Duration
- [Shift-left testing](https://en.wikipedia.org/wiki/Shift-left_testing) - wcześniejsze testowanie w cyklu rozwoju
- [Test Pyramid](https://martinfowler.com/bliki/TestPyramid.html) - Martin Fowler o hierarchii testów

**Przypadki studyjne**:
- [Log4j vulnerability impact](https://www.cisa.gov/news-events/cybersecurity-advisories/aa21-356a) - przykład ważności Update Hygiene
- [Żabka API vulnerability](https://niebezpiecznik.pl/post/dziura-w-api-zabki-pozwalala-na-darmowe-zakupy/) - błędy w API
