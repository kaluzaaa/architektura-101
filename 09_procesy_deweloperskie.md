# 9. Procesy Deweloperskie - Rozszerzony TL;DR

## 🎯 Kluczowe Koncepty

**CI/CD jako Standard**
- Continuous Integration/Continuous Deployment to podstawa nowoczesnego developmentu
- Główny cel: **eliminacja błędów ludzkich** przez automatyzację
- Standard branżowy, ale utrzymanie i adaptacja mogą być wyzwaniem

**Trzy Filary Observability**
- **Metryki**: infrastruktura (CPU, RAM, dyski), aplikacyjne (response time, throughput), biznesowe (transakcje, konwersje)
- **Logi**: techniczne vs audytowe, strukturalne formatowanie (JSON), standaryzacja
- **Tracing**: szczegółowa analiza przepływu żądań przez wiele serwisów

**RED Method**
- **Rate**: ilość żądań na sekundę
- **Errors**: procent błędów
- **Duration**: czas odpowiedzi
- Standard dla metryk aplikacyjnych

**Konfiguracja Dwupoziomowa**
- **Techniczna**: ustawienia aplikacji, przechowywana w ConfigMaps (limit 1MB)
- **Biznesowa**: listy banków, polityki cenowe, wymaga dedykowanych serwisów z GUI i audytowaniem

## 💡 Praktyczne Zastosowania

**Testowanie Wielopoziomowe**
- **Unit testy**: łatwe do uruchomienia lokalnie, oznaczanie projektów testowych w solucji
- **E2E testy**: bardziej złożone, przez cały system od UI do bazy
- **Testy manualne**: scenariusze krok po kroku z danymi wejściowymi i oczekiwanymi rezultatami
- **Format Cucumber/Gherkin**: czytelny dla biznesu i techników

**Monitoring Biznesowy**
- Śledzenie statusu wiadomości przez wzorzec Outbox Pattern
- Wykrywanie zatkanych pipeline'ów (slow vs fast queues)
- Aplikacje muszą **wystawiać biznesowe metryki**, nie tylko techniczne

**Automatyzacja Workflow**
- Automatyzacja ticketów przez API
- Zarządzanie uprawnieniami (szybkie nadawanie/odbieranie dostępów)
- Automatyzacja powtarzalnych operacji (restartowanie, pobieranie logów)

## ⚡ Najważniejsze Zasady

**Observability First**
- "Metryki powinny być wystawiane jako metryki, a nie umieszczane w logach"
- Standaryzacja formatów logów od początku projektu
- OpenTelemetry jako standard dla różnych języków programowania

**Separacja Odpowiedzialności w Logach**
- **Logi techniczne**: wyjątki, debugowanie → system logowania (Loki)
- **Logi audytowe**: zmiany użytkownika na obiekcie → baza danych lub płaskie pliki

**Konfiguracja Centralna**
- Centralne serwisy dla konfiguracji biznesowej w dużych systemach rozproszonych
- GUI, audytowanie zmian, zarządzanie uprawnieniami
- Unikanie nadmiaru ConfigMapów

**Automatyzacja vs Procesy Manualne**
- Automatyzacja minimalizuje "ułańską fantazję" i wymusza procedury
- Procesy manualne dają często "złudne poczucie kontroli"

## 🚨 Typowe Problemy i Rozwiązania

**Alert Fatigue**
- **Problem**: Za dużo alertów = ignorowanie alertów
- **Rozwiązanie**: Selekcja krytycznych metryk, unikanie szumu

**Chaos w Logach**
- **Problem**: "Ludzie przyzwyczaili się wrzucać łajno do elastyka, bo można zrobić full text search"
- **Rozwiązanie**: Loki z przemyślaną strukturą logów i labelami

**Debugowanie na Produkcji**
- **Problem**: Brak odpowiednich narzędzi observability
- **Rozwiązanie**: Anomaly Detection, strukturalne logi, selektywne tracing

**Problemy z ConfigMaps**
- **Problem**: Nadmiar ConfigMapów prowadzi do problemów z zarządzaniem
- **Rozwiązanie**: Centralne serwisy dla konfiguracji biznesowej

**Brak Standardów Logowania**
- **Problem**: Każdy serwis loguje inaczej
- **Rozwiązanie**: Ustrukturyzowane logi (JSON), OpenTelemetry, narzucenie standardów przez architekta

## 🛠️ Narzędzia i Technologie

**Monitoring Stack**
- **Prometheus**: metryki i anomaly detection
- **Grafana**: wizualizacja metryk i dashboardy
- **Loki**: logi z dynamicznymi labelami, brak full-text search
- **ELK Stack**: Elasticsearch/Logstash/Kibana - może być problematyczny w utrzymaniu

**Testing Tools**
- **Copilot**: wspomaganie generowania scenariuszy testowych
- **Cucumber/Gherkin**: format testów zrozumiały dla biznesu
- **Postman/cURL**: testowanie API w scenariuszach manualnych

**CI/CD i Automatyzacja**
- **GitHub Actions**: automatyzacja workflow
- **ArgoCD**: GitOps deployment
- **Rundeck**: automatyzacja operacji IT

**Konfiguracja i Zarządzanie**
- **Kubernetes ConfigMaps**: konfiguracja techniczna
- **Feature Flags**: kontrola funkcjonalności bez deploymenta
- **Centralne serwisy**: konfiguracja biznesowa z GUI

**AI/LLM Support**
- **GitHub Copilot**: wspomaganie kodowania
- **Claude/ChatGPT**: analiza kodu, generowanie dokumentacji
- **Prompt Engineering**: precyzyjne instrukcje dla lepszych wyników

## 📝 Przykłady z Materiałów

**Successful Observability Implementation**
> "Pełna obserwowalność systemu składa się z trzech kluczowych elementów: metryk, logów i traces"

**Loki vs ELK Experience**
> "Loki jest wskazywany jako dobra alternatywa dla ELK w mniejszych systemach, skaluje się dobrze i jest prosty w użyciu"

**Configuration Management Reality**
> "ConfigMapy mają limit rozmiaru (1MB), co utrudnia przechowywanie dużych danych biznesowych, np. listy banków zagranicznych"

**AI in Development**
> "LLM-y mogą generować wstępne wersje dokumentacji na podstawie opisu lub kodu. Są używane do analizy codebase'u, śledzenia przepływów funkcjonalności"

## ✅ Checklista Do Działania

**Observability Setup**
- [ ] Zdefiniuj i wdrożaj RED Method dla kluczowych serwisów
- [ ] Ustanów standardy logowania (JSON, OpenTelemetry)
- [ ] Rozdziel logi techniczne od audytowych
- [ ] Skonfiguruj anomaly detection w Prometheus
- [ ] Unikaj alert fatigue - selekcja krytycznych alertów

**Testing Strategy**
- [ ] Oznacz projekty testowe w solucji dla łatwej identyfikacji
- [ ] Udokumentuj scenariusze testów manualnych (format Cucumber/Gherkin)
- [ ] Zapewnij łatwe uruchamianie testów unit lokalnie
- [ ] Rozważ wykorzystanie AI do generowania scenariuszy testowych

**Configuration Management**
- [ ] Rozdziel konfigurację techniczną od biznesowej
- [ ] Dla konfiguracji biznesowej rozważ centralny serwis z GUI
- [ ] Wdrożaj audytowanie zmian konfiguracji
- [ ] Unikaj nadmiaru ConfigMapów

**Automation Implementation**
- [ ] Zidentyfikuj powtarzalne zadania do automatyzacji
- [ ] Wdrożaj automatyzację zarządzania uprawnieniami
- [ ] Skonfiguruj CI/CD pipeline
- [ ] Wykorzystaj AI/LLM do wspomagania development process

**Development Hygiene**
- [ ] Ustanów "Definition of Done" dla historyjek
- [ ] Rozważ rotację ról (Quality Officer)
- [ ] Automatyzuj tworzenie ticketów przez API
- [ ] Formalizuj procesy eliminujące "ułańską fantazję"

## 🔗 Dodatkowe Zasoby

**Monitoring i Observability**
- [RED Method - Grafana](https://grafana.com/blog/2018/08/02/the-red-method-how-to-instrument-your-services/)
- [Loki Labels Guide](https://grafana.com/docs/loki/latest/get-started/labels/)
- [Prometheus Anomaly Detection](https://about.gitlab.com/blog/anomaly-detection-using-prometheus/)
- [OpenTelemetry](https://opentelemetry.io/)

**Testing i Quality**
- [Cucumber/Gherkin Documentation](https://cucumber.io/docs/gherkin/)
- [Testing Best Practices](https://testing.googleblog.com/)

**Automation Tools**
- [GitHub Actions](https://github.com/features/actions)
- [Rundeck](https://www.rundeck.com/)
- [ArgoCD](https://argoproj.github.io/argo-cd/)

**AI Coding Assistance**
- [GitHub Copilot Best Practices](https://docs.github.com/en/copilot/how-tos/custom-instructions/adding-repository-custom-instructions-for-github-copilot)
- [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)
- [AI Coding Gist](https://gist.github.com/kaluzaaa/5271b5f2d9d64512f0bc52e74311afd9)

**Configuration Management**
- [Kubernetes ConfigMaps](https://kubernetes.io/docs/concepts/configuration/configmap/)
- [Feature Flags Best Practices](https://launchdarkly.com/blog/feature-flag-best-practices/)

**CNCF Ecosystem**
- [CNCF Landscape](https://landscape.cncf.io/)
- [Cloud Native Computing Foundation](https://www.cncf.io/)
