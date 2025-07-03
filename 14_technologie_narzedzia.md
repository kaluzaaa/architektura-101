# 14. Technologie i Narzędzia - Rozszerzony TL;DR

## 🎯 Kluczowe Koncepty

**Paradygmat "Managed > Self-hosted"**: Kluczowa zasada współczesnej architektury - deleguj infrastrukturę chmurowym dostawcom, aby skupić się na logice biznesowej. Jak mówi motto - "PostgreSQL do wszystkiego" (przykład Revolut).

**Commodity vs Custom**: Wykorzystuj **Wardley Maps** do mapowania technologii. Wszystko co jest "commodity" (standardowe w branży) kupuj/używaj gotowe. Buduj tylko to, co daje przewagę biznesową.

**Build vs Buy vs Open Source**: Fundamentalna trójka decyzyjna. **"Buy" jest często tańsze niż "Build"** - nawet droga licencja może kosztować mniej niż własne rozwiązanie. Open Source wymaga "sklejania wszystkiego" i własnego wsparcia.

**Cognitive Load**: Zbyt wiele warstw abstrakcji utrudnia pracę deweloperom. Każda technologia powinna mieć jasne uzasadnienie biznesowe.

## 💡 Praktyczne Zastosowania  

**Kubernetes jako Standardowe Rozwiązanie**:
- **Zarządzany K8s (EKS, AKS, GKE)** > on-premise dla łatwiejszego dzielenia zasobów
- **Cert-Manager** do automatycznego zarządzania certyfikatami
- **Network Policies** dla mikrosegmentacji ruchu
- **KEDA** do autoskalowania na podstawie długości kolejek

**Service Mesh dla Zaawansowanych**:
- **Istio** oferuje mTLS, routing, observability "out-of-the-box"
- Uwaga na złożoność - "Service Mesh może być przyczyną dodania mTLS w komunikacji wewnętrznej"
- Balansuj funkcjonalność z prostotą implementacji

**Wybory Cloud vs On-Premise**:
- **Cloud dla startupów** - szybkość, elastyczność, dostęp do zarządzanych usług
- **On-premise dla enterprise** - często tańsze w perspektywie 5+ lat dla dużych, stabilnych systemów
- **Hybrid** - wykorzystuj mocne strony obu podejść

## ⚡ Najważniejsze Zasady

**"PostgreSQL do wszystkiego"**: Przykład z Revolut - jeden typ bazy danych znacznie upraszcza operacje i redukuje Cognitive Load zespołów.

**Automatyzacja nad Procedurami**: "Kod zamiast procedur" - **Rundeck** do automatyzacji operacji IT, **GitOps** (ArgoCD, Flagger) dla deploymentów.

**Observability-first**: Implementuj **3 filary** (metryki, logi, tracing) od początku, nie dodawaj później. **RED Method** dla metryk aplikacyjnych.

**Security by Design**: **"Model Szwajcarskiego Sera"** - wiele warstw ochrony. Używaj **OWASP Top 10**, **NIST**, **CIS Benchmarks**.

## 🚨 Typowe Problemy i Rozwiązania

**Problem**: "Not Invented Here" syndrome - chęć budowania wszystkiego samemu  
**Rozwiązanie**: Używaj **CNCF Landscape** do identyfikacji sprawdzonych rozwiązań. Pytaj: "Czy to daje przewagę biznesową?"

**Problem**: Nadmierne ConfigMapy w Kubernetes (limit 1MB)  
**Rozwiązanie**: **Rozróżnij konfigurację techniczną vs biznesową**. Konfiguracja biznesowa (listy banków, polityki) - dedykowane serwisy.

**Problem**: Alert fatigue - za dużo alertów = ignorowanie alertów  
**Rozwiązanie**: **Anomaly Detection** w Prometheus, biznesowe metryki zamiast technicznych alertów.

**Problem**: Vendor lock-in w chmurze  
**Rozwiązanie**: **Standardy otwarte** (OpenTelemetry, CloudEvents), unikaj vendor-specific rozwiązań dla krytycznych komponentów.

## 🛠️ Narzędzia i Technologie

**Kubernetes Ecosystem**:
- **Cert-Manager**: https://cert-manager.io/ - automatyczne zarządzanie certyfikatami
- **Trivy**: https://github.com/aquasecurity/trivy - skanowanie kontenerów i konfiguracji
- **CloudNative PostgreSQL**: https://cloudnative-pg.io/ - PostgreSQL operator

**Monitoring i Observability**:
- **Loki vs ELK**: "Loki ma dobrą skalowalność, labels i cardinality, ale brak full-text search"
- **Grafana Stack**: https://grafana.com/docs/loki/latest/
- **OpenTelemetry**: standard dla strukturalnego logowania

**Security Tools**:
- **Trivy Scanner**: skanowanie pod kątem podatności
- **JFrog Artifactory**: https://jfrog.com/artifactory/ - zarządzanie zależnościami
- **OWASP ZAP**: automatyczne testy bezpieczeństwa

**GitOps i Deployment**:
- **ArgoCD**: https://argoproj.github.io/argo-rollouts/
- **Flagger**: https://flagger.app/ - progressive delivery
- **Rundeck**: https://www.rundeck.com/ - automatyzacja operacji IT

## 📝 Przykłady z Materiałów

**Revolut Case Study**: "PostgreSQL do wszystkiego" - jeden typ bazy danych znacznie upraszcza operacje i redukuje koszty utrzymania.

**Cloudflare Performance**: "55 million requests/sec with just 15 PostgreSQL clusters" - pokazuje potęgę prostych, sprawdzonych rozwiązań.

**Service Mesh Reality Check**: "Wyzwanie: Zarządzanie certyfikatami w Service Mesh może być skomplikowane" - balansuj funkcjonalność z prostotą.

**ConfigMap Limitations**: "ConfigMapy mają limit 1MB, co utrudnia przechowywanie dużych danych biznesowych, np. listy banków zagranicznych".

## ✅ Checklista Do Działania

### Przed Wyborem Technologii
- [ ] Zidentyfikuj czy problem to "commodity" czy "custom value"
- [ ] Sprawdź **CNCF Landscape** dla sprawdzonych rozwiązań
- [ ] Oceń **Total Cost of Ownership** (TCO) - licencja vs własne utrzymanie
- [ ] Przeanalizuj **Cognitive Load** dla zespołów

### Implementacja Cloud Native
- [ ] Wybierz **zarządzany Kubernetes** zamiast self-hosted
- [ ] Zaimplementuj **Cert-Manager** dla automatycznych certyfikatów
- [ ] Skonfiguruj **Network Policies** dla mikrosegmentacji
- [ ] Używaj **KEDA** do autoskalowania kolejek

### Monitoring i Observability
- [ ] Zaimplementuj **RED Method** (Rate, Errors, Duration)
- [ ] Standaryzuj logi do **JSON** z **OpenTelemetry**
- [ ] Rozróżnij **logi techniczne vs audytowe**
- [ ] Skonfiguruj **Anomaly Detection** w Prometheus

### Security Checklist
- [ ] Skanuj obrazy kontenerów **Trivy**
- [ ] Implementuj **OWASP Top 10** recommendations
- [ ] Kontroluj **ruch wychodzący** (egress) - często pomijane!
- [ ] Używaj **mTLS** między serwisami w Service Mesh

### Operacje i Automatyzacja
- [ ] Zaimplementuj **GitOps** z ArgoCD/Flagger
- [ ] Automatyzuj repetitive tasks z **Rundeck**
- [ ] Stwórz **centralne serwisy** dla konfiguracji biznesowej
- [ ] Regularnie aktualizuj zależności (**"Update Hygiene"**)

## 🔗 Dodatkowe Zasoby

### Frameworks i Standardy
- **CNCF Landscape**: https://landscape.cncf.io/ - kompletny przegląd narzędzi cloud native
- **OpenTelemetry**: https://opentelemetry.io/ - standard observability
- **CloudEvents**: https://cloudevents.io/ - standardy event-driven architecture

### Case Studies i Performance
- **Cloudflare PostgreSQL**: https://dev.to/devangtomar/how-cloudflare-achieved-55-million-requests-per-second-with-just-15-postgresql-clusters-3mm8
- **Monzo Resilience**: https://monzo.com/blog/tolerating-full-cloud-outages-with-monzo-stand-in

### Security Resources
- **OWASP Top 10**: https://owasp.org/www-project-top-ten/
- **NIST Cybersecurity**: https://www.nist.gov/cyberframework
- **CIS Benchmarks**: https://www.cisecurity.org/cis-benchmarks

### Monitoring i Observability
- **RED Method**: https://grafana.com/blog/2018/08/02/the-red-method-how-to-instrument-your-services/
- **Grafana Loki**: https://grafana.com/docs/loki/latest/get-started/labels/

### AI i Automatyzacja
- **GitHub Copilot Custom Instructions**: https://docs.github.com/en/copilot/how-tos/custom-instructions/adding-repository-custom-instructions-for-github-copilot
- **Cursor Rules**: https://docs.cursor.com/context/rules
- **AI Coding Best Practices**: https://gist.github.com/kaluzaaa/5271b5f2d9d64512f0bc52e74311afd9

### Strategia Technologiczna
- **Wardley Maps**: https://learnwardleymapping.com/ - mapowanie strategiczne technologii
- **Team Topologies**: https://teamtopologies.com/ - organizacja zespołów
- **Hacker Laws**: https://github.com/dwmkerr/hacker-laws - prawa architektury

### Dodatkowe Narzędzia
- **Cert-Manager**: https://cert-manager.io/
- **Trivy Scanner**: https://github.com/aquasecurity/trivy
- **ArgoCD**: https://argoproj.github.io/argo-rollouts/
- **Rundeck**: https://www.rundeck.com/