# 6. Architektura i Decyzje - Rozszerzony TL;DR

## 🎯 Kluczowe Koncepty

**Architektura to zarządzanie czasem decyzji**
- Architektura = możliwość **odkładania kosztownych decyzji w czasie**
- Celem jest uniknięcie "zabetonowania się" w złych rozwiązaniach
- Odwlekanie rzeczy, które ciężko zmienić lub się z nich wycofać

**Architektura jako kompromis**
- W każdej architekturze **wszystko jest kompromisem**
- Jeśli nie widzisz kompromisów, oznacza to, że czegoś jeszcze nie znalazłeś
- Cel: **"najmniej zła architektura"**, nie perfekcja
- Nie ma uniwersalnej metody na wszystko

**Wymagania niefunkcjonalne jako drivery**
- **Operacyjne**: dostępność, skalowalność, odporność na awarie, bezpieczeństwo
- **Strukturalne**: utrzymywalność, konfigurowalność, rozszerzalność
- **Przekrojowe**: uwierzytelnianie, autoryzacja, zgodność z przepisami, prywatność

## 💡 Praktyczne Zastosowania

**Proces decyzyjny w architekturze**
- **"Dlaczego" ważniejsze niż "Jak"** - zrozumienie celu biznesowego i technologicznego
- Ciągłe zadawanie pytania "dlaczego?" przed implementacją
- Kwantyfikacja wymagań: ile transakcji rocznie, ilu użytkowników, jaki wzrost
- Przekształcanie wymagań biznesowych na techniczne

**Podejście do projektowania**
- Często brak formalnej analizy na początku - model danych powstaje "w locie"
- Projektowanie "w locie" jako dostosowanie do zwinności przy pilnowaniu założeń
- Unikanie zbyt szczegółowego projektowania z góry (upfront design)

**Dylematy technologiczne**
- **Build vs Buy vs Open Source** - kluczowa decyzja architektoniczna
- **"Buy"** dla "commodity solutions" - często tańsze, nawet przy drogich licencjach
- **"Build"** tylko tam, gdzie tworzy wartość biznesową i wyróżnia firmę
- **"Open Source"** - koszt "sklejania wszystkiego" i utrzymania

## ⚡ Najważniejsze Zasady

**Fundamentalne prawa architektury**
- **KISS (Keep It Simple, Stupid)**: hołdowanie prostocie, unikanie nadmiernej inżynierii
- **YAGNI (You Ain't Gonna Need It)**: nie buduj funkcjonalności "na zapas"
- **DRY (Don't Repeat Yourself)**: unikaj powielania, ale nie przesadzaj z abstrakcją
- **SRP (Single Responsibility Principle)**: każdy komponent jedna odpowiedzialność

**Prawa organizacyjne**
- **Prawo Conwaya**: struktura organizacji odzwierciedla architekturę systemów
- **"Conway's Law przez K"**: namespace'y Kubernetes = struktura organizacyjna
- Komunikacja w firmie = komunikacja między serwisami

**Zasady pragmatyczne**
- **Nie ma idealnych rozwiązań** - balansowanie między prostotą a funkcjonalnością
- **Unikanie "Not Invented Here" syndrome** - nie wymyślaj koła na nowo
- **Tworzenie abstrakcji tylko gdy potrzebne** - unikaj nadmiernej abstrakcji
- **Removability over Maintainability** - łatwość usunięcia ważniejsza od utrzymania

## 🚨 Typowe Problemy i Rozwiązania

**Problemy kulturowe**
- **"Nie ruszaj, bo działa"** - opór przed zmianami i aktualizacjami
- **"Zawsze tak robiliśmy"** - przywiązanie do starych sposobów
- **Mentalność "napiszemy to lepiej"** - przecenianie własnych możliwości

**Rozwiązania organizacyjne**
- Stopniowe wprowadzanie zmian, nie rewolucja
- Edukacja i szkolenia zespołów
- Pokazywanie korzyści biznesowych z nowych rozwiązań
- Wspólny język w firmie jako "must have"

**Problemy procesowe**
- **Pomijanie fazy analizy** na rzecz szybkiej implementacji
- **Nielogiczne procesy biznesowe** - często ukryta "wiedza plemienna"
- **Silosy kompetencyjne** - zespoły w izolacji

**Rozwiązania praktyczne**
- Formalizacja "Definition of Done" - historyjki nie trafiają do deweloperów bez analizy
- Rotacja ról (np. Quality Officer) dla odpowiedzialności zespołowej
- Przekuwanie wiedzy plemiennej w procesy i dokumentację

## 🛠️ Narzędzia i Technologie

**Narzędzia decyzyjne**
- **Wardley Maps**: mapowanie strategiczne "commodity vs unique value"
  - https://www.wardleymaps.com/
  - https://learnwardleymapping.com/
- **Architecture Katas**: ćwiczenia architektoniczne
  - https://nealford.com/katas/
- **5 Why Analysis**: metoda analizy przyczyn

**Frameworki i standardy**
- **arc42**: szablon dokumentacji architektury - https://arc42.org/
- **ADR (Architecture Decision Records)**: https://adr.github.io/
- **CNCF Landscape**: https://landscape.cncf.io/

**Narzędzia wspomagające**
- **AI/LLM**: generowanie wstępnych analiz i diagramów
- **Copilot**: wsparcie w prototypowaniu i eksploracji
- **Automation tools**: Rundeck - https://www.rundeck.com/

## 📜 Decyzje Architektoniczne - Szczegóły

### Architecture Decision Records (ADRs)
**ADRs** to narzędzie do dokumentowania decyzji architektonicznych i ich uzasadnień - "git blame dla architektury". Każdy ADR powinien zawierać:

- **Kontekst** - jakie były okoliczności decyzji
- **Rozważane opcje** - jakie były alternatywy
- **Decyzja** - co zostalo wybrane
- **Konsekwencje** - jakie są skutki tej decyzji

**Dlaczego ADRy są ważne:**
- Umożliwiają zrozumienie historii decyzji
- Pomagają w przyszłych zmianach architektury
- Dokumentują odrzucone opcje (unikają powtórnych dyskusji)
- Są przechowywane w repozytorium blisko kodu

### Variance - Uzasadnione Odstepstwa
**Variance** to uzasadnione odstępstwo od decyzji architektonicznej. Nie każde naruśenie zasady to błąd - czasami są uzasadnione wyjątki:

- **Ograniczenia czasowe** - pilny fix wymagający tymczasowego obejścia
- **Ograniczenia techniczne** - niemożliwość zastosowania standardowego podejścia
- **Wymagania specjalne** - unikalne potrzeby części systemu

**Ważne**: Variance musi być **udokumentowany i zaakceptowany** przez architekta.

### Design Principles - Zasady Projektowe
**Design Principles** są bardziej **elastyczne niż decyzje** architektoniczne. Stanowią wytyczne, a nie sztywne reguły:

- **Przewodnictwo** - pomagają w podejmowaniu decyzji w nieoczekiwanych sytuacjach
- **Elastyczność** - mogą być interpretowane w kontekście
- **Kierunek** - określają preferowane podejście, ale nie zabraniają alternatyw

**Przykłady Design Principles:**
- "Preferuj asynchroniczność nad synchroniczność"
- "Wybieraj proven technology nad bleeding edge"
- "Priorytetyzuj developer experience"
- "Dokumentuj 'dlaczego', nie tylko 'co'"

### Struktury Architektoniczne - 4 Elementy
Architektura oprogramowania składa się z czterech głównych elementów:

1. **Structure** (Struktura) - rodzaj stylu architektury (monolit, mikroserwisy, SOA)
2. **Architecture characteristics** (Charakterystyki architektury) - cechy "-ilities"
3. **Architecture decisions** (Decyzje architektoniczne) - reguły i ograniczenia
4. **Design principles** (Zasady projektowe) - elastyczne wytyczne

**Ważne**: Sama struktura nie definiuje w pełni architektury. Charakterystyki, decyzje i zasady są równie istotne.

## 📝 Przykłady z Materiałów

**Przykład złożoności organizacyjnej**
> "Ambicje (np. budowa całej platformy deweloperskiej na Kubernetesie dla jednej aplikacji) mogą prowadzić do przekombinowanych rozwiązań"

**Przykład praktyczny Build vs Buy**
> "Nawet droga licencja może być tańsza niż budowanie - problem 'commodity solutions'"

**Przykład wpływu kultury**
> "Kultura zjada strategię na śniadanie - nawet najlepsze plany architektoniczne nie zadziałają bez odpowiedniej kultury organizacyjnej"

**Przykład CAP Theorem w praktyce**
- **Last write wins** - prosta strategia, ale może gubić dane
- **Custom policies** - złożone reguły biznesowe
- **Eventual consistency** - akceptacja przejściowych niespójności

**Przykład Composite SLA**
> "3 serwisy po 99.9% = ~99.7% całego systemu - złożoność architektury obniża skumulowaną dostępność"

## ✅ Checklista Do Działania

### Pre-projekt
- [ ] Zdefiniuj wymagania niefunkcjonalne (operacyjne, strukturalne, przekrojowe)
- [ ] Przeprowadź Business Impact Analysis (BIA) - ile kosztuje przestój?
- [ ] Kwantyfikuj skalę: transakcje/rok, użytkownicy, wzrost, zasoby
- [ ] Określ poziom dojrzałości potrzebny dla organizacji (M0-M3)

### Proces decyzyjny
- [ ] Zadaj pytanie "dlaczego?" przed "jak?" - zrozum cel biznesowy
- [ ] Rozważ Build vs Buy vs Open Source dla każdego komponentu
- [ ] Użyj Wardley Maps do zmapowania wartości biznesowej
- [ ] Zidentyfikuj "commodity" vs "unique value" elementy

### Dokumentacja decyzji
- [ ] Stwórz ADR dla kluczowych decyzji architektonicznych
- [ ] Udokumentuj odrzucone opcje i powody ich odrzucenia
- [ ] Określ kto podjął decyzję i jakie były założenia
- [ ] Przechowuj ADR w repozytorium blisko kodu

### Implementacja
- [ ] Zastosuj zasady KISS i YAGNI - unikaj nadmiernej inżynierii
- [ ] Nie twórz abstrakcji "na zapas" - YAGNI
- [ ] Zapewnij idempotencję w systemach rozproszonych
- [ ] Zaimplementuj monitoring i observability od początku

### Post-implementacja
- [ ] Regularnie przegląj i aktualizuj decyzje architektoniczne
- [ ] Mierz rzeczywiste vs przewidywane metryki
- [ ] Dokumentuj lessons learned dla przyszłych projektów
- [ ] Propaguj wiedzę między zespołami

## 🔗 Dodatkowe Zasoby

### Książki i Artykuły
- **Event-Driven.io**: https://event-driven-io.github.io/emmett/overview.html
- **Removability over Maintainability**: https://event-driven.io/en/removability_over_maintainability/
- **Vertical Slices in Practice**: https://event-driven.io/en/vertical_slices_in_practice/

### Prawa i Zasady
- **Hacker Laws**: https://github.com/dwmkerr/hacker-laws
- **Mechanical Sympathy**: https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.concept.mechanical-sympathy.en.html

### Case Studies
- **Cloudflare**: 55M requests/sec with 15 PostgreSQL clusters
  - https://dev.to/devangtomar/how-cloudflare-achieved-55-million-requests-per-second-with-just-15-postgresql-clusters-3mm8
- **Monzo**: Tolerating full cloud outages
  - https://monzo.com/blog/tolerating-full-cloud-outages-with-monzo-stand-in

### Narzędzia i Frameworki
- **Google Cloud Microservices Demo**: https://github.com/GoogleCloudPlatform/microservices-demo
- **Microsoft eShopOnContainers**: https://learn.microsoft.com/en-us/dotnet/architecture/cloud-native/introduce-eshoponcontainers-reference-app
- **Azure Well-Architected**: https://learn.microsoft.com/en-us/azure/well-architected/

### AI i Automatyzacja
- **Claude Code Best Practices**: https://www.anthropic.com/engineering/claude-code-best-practices
- **GitHub Copilot Custom Instructions**: https://docs.github.com/en/copilot/how-tos/custom-instructions/adding-repository-custom-instructions-for-github-copilot
- **Cursor Rules**: https://docs.cursor.com/context/rules

### Podcast
- **Patoarchitekci #152**: https://patoarchitekci.io/152/
