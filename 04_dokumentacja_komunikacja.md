# 4. Dokumentacja i Komunikacja - Rozszerzony TL;DR

## 🎯 Kluczowe Koncepty

**Dokumentacja jako fundament architektury** - Głównym wyzwaniem jest zachowanie aktualności dokumentacji i dostosowanie jej do odbiorcy. Dokumentacja powinna być blisko kodu i łatwa w utrzymaniu.

**Lokalizacja dokumentacji** - Markdown w repozytorium > Confluence/Wiki. Dokumentacja powinna być blisko kodu, widoczna podczas code review i łatwa do aktualizowania.

**Wizualizacja ponad tekstem** - Ludzie preferują diagramy nad "ściany tekstu". Formy wizualne (diagramy, tabele) są zawsze lepsze niż długie opisy.

**Zawsze określ odbiorcę** - Jedna grupa docelowa = jeden dokument. Różnicuj między dokumentacją techniczną dla technicznych a biznesową dla niefachowców.

**ADR (Architecture Decision Records)** - "Git blame dla architektury". Lekki sposób dokumentowania ważnych decyzji architektonicznych, gdzie każda decyzja ma swoje uzasadnienie i kontekst. "Dlaczego" ważniejsze niż "jak". Pomaga zrozumieć przeszłe decyzje, szczególnie w większych zespołach i przy rotacji kadr.

## 💡 Praktyczne Zastosowania

**Struktura dokumentacji w repozytorium:**
- `README.md` - automatycznie wyświetla się jako domyślny
- `docs/` - folder z dokumentacją techniczną
- `ADR/` - folder z Architecture Decision Records
- Automatyczny generator TOC dla dużych dokumentów

**Diagramy C4 w praktyce:**
- **L1 (System Context)** - system w otoczeniu innych systemów/użytkowników
- **L2 (Container)** - aplikacje, bazy danych, serwisy wewnątrz systemu
- **Unikaj L3 i L4** - zbyt szczegółowe, trudne w utrzymaniu

**Narzędzia "Diagram as Code":**
- Mermaid, PlantUML - renderowane online, przechowywane w repo
- Automatyczne generowanie diagramów z kodu przez AI/LLM

**ADR w praktyce:**
- **Struktura ADR**: Problem/kontekst → Główne założenia → Wybrana opcja + uzasadnienie → Odrzucone opcje + powody → Kto podjął decyzję
- **Kiedy tworzyć**: Decyzje o dużym wpływie, trudne do cofnięcia, wprowadzenie/zmiana technologii, odstępstwa od standardów
- **Dobre praktyki**: Lekkie i szybkie (max 1 godzina), w repozytorium, Pull Request jako "work in progress"
- **Szablony promptów dla ADR**: Przygotowanie gotowych promptów do AI uspójniających styl i strukturę, pomagających w ustrukturyzowaniu myśli
- **Odrzucone ADRy też mają wartość** - historyczna wiedza
- **Nie przesadzaj z ilością** - nie każda drobna zmiana potrzebuje ADR
- **Rola architekta**: Mentor i coach w pisaniu ADRów, nie "policjant" wymuszający compliance

## ⚡ Najważniejsze Zasady

**"Markdown w repozytorium > Confluence/Wiki"** - Dokumentacja blisko kodu się nie dezaktualizuje.

**"Jeden dokument, jedna grupa docelowa"** - Nie mieszaj żargonu technicznego z komunikacją biznesową.

**"KISS dla dokumentacji"** - Krótkie akapity, punkty, wizualizacje zamiast długich opisów.

**"ADR tylko dla big impact"** - Nie dla każdej drobnej zmiany, ale dla decyzji trudnych do cofnięcia. Pomaga zrozumieć przeszłe decyzje przy rotacji kadr.

## 🚨 Typowe Problemy i Rozwiązania

**Problem: Dokumentacja się dezaktualizuje**
- Rozwiązanie: Markdown w repozytorium, widoczne podczas code review

**Problem: Nikt nie czyta dokumentacji**
- Rozwiązanie: Krótkie akapity, wizualizacje, TL;DR format

**Problem: Każdy rozumie architekturę inaczej**
- Rozwiązanie: Wspólny język w firmie, standardy dokumentacji

**Problem: Zbyt dużo lub za mało ADRów**
- Rozwiązanie: Lekkie szablony, mentoring zamiast wymuszania
- Wiele tematów można załatwić spotkaniem zamiast ADR
- Unikaj nadmiernej formalności i obciążenia zespołów

**Problem: Niechęć zespołów do pisania ADR**
- Przyczyny: Postrzeganie jako niepotrzebne obciążenie, brak czasu, nadmierna formalność
- Rozwiązanie: Architekt jako mentor (nie policjant), pokazywanie wartości, **AI i szablony promptów jako wsparcie**

**Problem: Wiedza plemienna zanika**
- Rozwiązanie: Przekuwanie w dokumentację, Setup Guide dla nowych
- ADR jako sposób na zachowanie historii decyzji

## 🛠️ Narzędzia i Technologie

**Dokumentacja:**
- [Arc42](https://arc42.org/) - szablon dokumentacji architektury
- [ADR Examples](https://github.com/joelparkerhenderson/architecture-decision-record) - wzorce dla Architecture Decision Records
- [TOC Generator](https://github.com/marketplace/actions/toc-generator) - automatyczny spis treści

**Diagramy:**
- Miro, Excalidraw - do rysowania na żywo
- Draw.io, Lucidchart - profesjonalne diagramy
- Mermaid, PlantUML - "diagram as code"

**AI/LLM dla dokumentacji:**
- GitHub Copilot, Cursor - generowanie diagramów z kodu
- **Szablony promptów dla uspójnienia stylu** - szczególnie dla ADRów
- **Szablony promptów do dokumentacji** - uspojnienie stylu dla całego zespołu
- Automatyczne generowanie TOC
- Wsparcie dla osób niebędących native speakerami

## 📝 Przykłady z Materiałów

**Cytaty kluczowe:**
- "Kultura zjada strategię na śniadanie" - dokumentacja musi być częścią kultury zespołu
- "Markdown w repozytorium jest najbardziej zielony" - aktualność przez bliskość kodu
- "Dokumentacja w Wiki/Confluence to ostateczne zło" - ze względu na szybką dezaktualizację
- "Szablony promptów do uspójnienia stylu i automatyzacji (np. dla ADRów)" - AI jako wsparcie w tworzeniu spoinej dokumentacji
- "Pomoc w pisaniu ADRów" - praktyczny aspekt roli architekta jako mentora

**Case study ADR:**
Request for Comments (RFC) vs lightweight ADR - RFC dla szerokiej dyskusji i "rozstrzelania" pomysłu, ADR dla szybkiej decyzji z kontekstem. RFC może być bardziej rozbudowanym dokumentem niż typowy ADR.

**AI w pisaniu ADR:**
Narzędzia LLM (np. Copilot) mogą wspierać poprzez generowanie wstępnych wersji, ustrukturyzowanie myśli, sugerowanie brakujących pytań lub identyfikowanie luk logicznych.

**Szablony promptów z materiałów:**
W pliku vibecodding.md znaleziono konkretne przykłady szablonów promptów:
- "Style Consistency Guidelines" - szablon do ujednolicenia stylu dokumentacji
- "Language Style Corrections" - szablon do poprawek językowych
- Przykład analizy systemu z wymaganiami dotyczącymi diagramów Mermaid
- Konwersja polskich zadań na angielskie prompty dla Claude Code

## ✅ Checklista Do Działania

### Przed rozpoczęciem dokumentowania:
- [ ] Określ grupę docelową (techniczna vs biznesowa)
- [ ] Wybierz format (Markdown w repo vs wiki)
- [ ] Przygotuj szablon zgodny z firmowymi standardami
- [ ] **Przygotuj szablony promptów** dla AI do uspójnienia stylu

### Podczas pisania dokumentacji:
- [ ] Używaj krótkich akapitów i punktów
- [ ] Dodaj wizualizacje (diagramy, tabele)
- [ ] Stosuj C4 L1-L2 dla architektury
- [ ] Generuj automatyczny spis treści

### Dla ADR:
- [ ] Sprawdź czy rzeczywiście potrzebny (duży wpływ, trudne do cofnięcia)
- [ ] **Przygotuj szablon promptu dla ADR** - uspojnienie struktury i stylu
- [ ] Użyj lekkiego szablonu (max 1 godzina pisania):
  - [ ] Problem/kontekst - dlaczego podejmujemy decyzję
  - [ ] Główne założenia - warunki brzegowe
  - [ ] Wybrana opcja + uzasadnienie
  - [ ] Odrzucone opcje + powody
  - [ ] Kto podjął decyzję
- [ ] Utwórz jako Pull Request "work in progress"
- [ ] Pozwól na komentowanie i udoskonalanie
- [ ] Przechowaj w repozytorium, nie w wiki

### Długoterminowe utrzymanie:
- [ ] Ustaw automatyczne przypomnienia o aktualizacji
- [ ] Zorganizuj regularne przeglądy dokumentacji
- [ ] Zbieraj feedback od zespołów

## 🔗 Dodatkowe Zasoby

**Szablony i Frameworks:**
- [Arc42 Templates](https://arc42.org/) - kompletny framework dokumentacji
- [ADR GitHub Collection](https://adr.github.io/) - wzorce ADR
- [Spotify System Visualization](https://engineering.atspotify.com/2022/07/software-visualization-challenge-accepted) - przykład dokumentacji wizualnej

**Narzędzia AI:**
- [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices) - AI w dokumentacji
- [GitHub Copilot Custom Instructions](https://docs.github.com/en/copilot/how-tos/custom-instructions/adding-repository-custom-instructions-for-github-copilot) - personalizacja AI
- [Cursor Rules](https://docs.cursor.com/context/rules) - konfiguracja AI coding

**Metodyki i Standardy:**
- [Team Topologies](https://teamtopologies.com/) - organizacja zespołów i komunikacji
- [Staff Engineer Introduction](https://blog.alexewerlof.com/p/introduction-to-the-role-of-staff) - rola architekta w dokumentacji

**Automation:**
- [GitHub Actions TOC Generator](https://github.com/marketplace/actions/toc-generator) - automatyzacja spisu treści
- [Mermaid Documentation](https://mermaid.js.org/) - diagram as code
- [PlantUML](https://plantuml.com/) - diagramy z tekstu