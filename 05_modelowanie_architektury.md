# 5. Modelowanie Architektury - Rozszerzony TL;DR

## 🎯 Kluczowe Koncepty

**Diagramy C4 (Context, Container, Component, Code)** - fundamentalny framework do modelowania architektury opracowany przez Simona Browna. Składa się z czterech poziomów szczegółowości:

- **L1 (System Context)** - najwyższy poziom, pokazuje system w kontekście użytkowników i innych systemów
- **L2 (Container)** - aplikacje, bazy danych, mikroserwisy wewnątrz systemu  
- **L3 (Component)** - moduły wewnątrz aplikacji
- **L4 (Code)** - klasy, funkcje, szczegóły implementacji

**"Diagram as Code"** - podejście do tworzenia diagramów z kodu tekstowego (Mermaid, PlantUML), pozwalające na wersjonowanie i automatyzację.

**Event Storming** - warsztatowa metoda odkrywania procesów biznesowych przez identyfikację eventów i ich przepływów.

**Wardley Maps** - narzędzie strategiczne do mapowania wartości biznesowej i ewolucji technologicznej, pomagające określić co jest "commodity" a co przewagą konkurencyjną.

**Spotify System Model** - standardowy model metadanych składający się z 3 podstawowych encji (APIs, Components, Resources) oraz 2 abstrakcji wyższego poziomu (Systems, Domains) do opisu architektury na dużą skalę.

**System Landscape Diagram** - wysokopoziomowy widok pokazujący zbiór powiązanych systemów, ich połączenia i zależności zewnętrzne (np. wszystkie systemy w domenie biznesowej).

## 💡 Praktyczne Zastosowania

**Złota Zasada C4**: "Używaj głównie **L1 (System Context) i L2 (Container)**. L3 i L4 są zbyt szczegółowe dla wysokopoziomowej architektury i zaciemniają obraz."

**Swimlanes dla procesów biznesowych** - pokazują jak proces biznesowy przepływa przez różne mikroserwisy i systemy. Szczególnie przydatne w architekturze event-driven.

**Sequence Diagrams (UML)** - doskonałe do dokumentowania przepływów procesów i interakcji między serwisami w czasie.

**Deployment Diagramy** - mapują kontenery logiczne na fizyczną infrastrukturę, pokazując jak system jest faktycznie wdrożony.

**Spotify approach - od whiteboard'ów do standardów**: Przejście od ad-hoc "boxes and arrows" na tablicach do standardowego podejścia z C4 + własnym modelem metadanych. Rozwiązuje problem skalowalności i zrozumienia bez kontekstu.

**Automatyzacja diagramów w Backstage**: Wykorzystanie metadanych software'u do automatycznego generowania diagramów, które są zawsze aktualne i umożliwiają interaktywne przeglądanie architektury.

## ⚡ Najważniejsze Zasady

**Wizualizacje > Tekst**: "Ludzie wolą patrzeć na diagramy i zgrabne tabele niż przebijać się przez 'ścianę tekstu'. Diagramy powinny dawać wizualny punkt zaczepienia."

**Jedna grupa odbiorców = jeden diagram**: Mieszanie żargonu technicznego i biznesowego w jednym diagramie utrudnia zrozumienie.

**Opisuj strzałki przypadkami użycia**: Każda strzałka na diagramie powinna być podpisana konkretnym przypadkiem użycia lub typem komunikacji.

**Wysokopoziomowość**: Diagramy architektoniczne powinny skupiać się na kluczowych decyzjach, nie na szczegółach implementacji.

**Standardowy model metadanych**: Wspólny język i definicje pojęć są kluczowe dla komunikacji w dużej organizacji. Spotify System Model definiuje: APIs (granice między komponentami), Components (indywidualne elementy software), Resources (infrastruktura), Systems (kolekcje współpracujących elementów), Domains (encje związane z obszarami biznesowymi).

**Minimalizacja kontekstu**: Diagramy powinny być zrozumiałe z minimalnym kontekstem dodatkowym - unikaj sytuacji gdzie trzeba pytać "co oznaczają te strzałki i pudełka?"

## 🚨 Typowe Problemy i Rozwiązania

**Problem**: L2 (Container) staje się nieczytelny przy dużej liczbie mikroserwisów.
**Rozwiązanie**: Grupuj powiązane serwisy w logiczne obszary lub używaj System Landscape jako alternatywy.

**Problem**: Diagramy szybko się dezaktualizują.
**Rozwiązanie**: Trzymaj diagramy w repozytorium jako "Diagram as Code" i automatyzuj generowanie z metadanych.

**Problem**: Zbyt szczegółowe diagramy (L3, L4) są trudne w utrzymaniu.
**Rozwiązanie**: Skup się na L1 i L2, pozostaw szczegóły w kodzie i dokumentacji technicznej.

**Problem**: Brak standardów wizualizacji w organizacji.
**Rozwiązanie**: Wprowadź szablony i wspólne konwencje nazewnictwa i kolorowania.

**Problem**: "Whiteboard syndrome" - diagramy ad-hoc na tablicach nie skalują się.
**Rozwiązanie**: Przejście do standardowego modelu (C4 + model metadanych) z automatyzacją generowania diagramów z rzeczywistych metadanych systemu.

**Problem**: Diagramy wymagają dodatkowego kontekstu i wyjaśnień.
**Rozwiązanie**: Zastosuj standard notation (C4) i model metadanych, aby diagramy były samowyjaśniające się.

## 🛠️ Narzędzia i Technologie

**Narzędzia graficzne**:
- **Miro** - świetne do współpracy zespołowej i Event Storming
- **Excalidraw** - minimalistyczne, idealne do rysowania na żywo
- **Draw.io** - bezpłatne, z bibliotekami ikon AWS/Azure
- **Lucidchart** - zaawansowane funkcje, integracje

**Diagram as Code**:
- **Mermaid** - renderowane przez GitHub, proste w użyciu
- **PlantUML** - bardziej rozbudowane, lepsze dla skomplikowanych diagramów
- **Structurizr** - specjalnie dla diagramów C4

**Automatyzacja**:
- **GitHub Copilot/Claude** - generowanie diagramów z opisu lub analizy kodu
- **Automatyczne generowanie TOC** z nagłówków Markdown
- **Backstage** - platforma do software catalog z automatycznym generowaniem diagramów architektonicznych z metadanych

## 📝 Przykłady z Materiałów

> "Diagramy C4 L1 i L2 są najważniejsze i najbardziej użyteczne. L3 często staje się zbyt szczegółowe i trudne w utrzymaniu."

> "Markdown w repozytorium jest uważany za najlepsze podejście do dokumentacji, ponieważ jest 'najbardziej zielony' i aktualny, znajdując się blisko kodu."

> "Automatyczne generowanie diagramów z kodu jest możliwe dzięki narzędziom LLM (np. Copilot), które potrafią na podstawie kodu wygenerować wstępne diagramy C4."

**Przykład Spotify System Landscape**: Alternatywny sposób wizualizacji złożonych systemów, gdzie każdy system jest reprezentowany jako "planety" w "galaktyce" organizacji.

**Przykład Structurizr**: Diagram C4 Container pokazujący główne komponenty systemu bankowego z jasnym podziałem na warstwy frontend, backend i integracje.

**Spotify o visualizacji**: > "We needed a lightweight way to visualize software architecture, optimized for human-to-human communication. We wanted diagrams that would enable us to understand our software with minimal context."

**Spotify o automatyzacji**: > "One great benefit of automating architectural diagrams is that they will always stay up to date with the intentional design as expressed in metadata; there will be no need for updating these as the system evolves."

**Spotify o whiteboard syndrome**: > "Whiteboard diagrams may look simple at a glance, but they can be hard to grasp without context or explanation... It's not practical to carry whiteboards around to spread knowledge, so they are constrained to a physical space."

## ✅ Checklista Do Działania

### Przed rozpoczęciem modelowania:
- [ ] Określ grupę odbiorców (techniczna vs biznesowa)
- [ ] Ustal zakres i poziom szczegółowości
- [ ] Wybierz odpowiednie narzędzie do diagramowania
- [ ] Przygotuj glossariusz terminów biznesowych
- [ ] Zdefiniuj standardowy model metadanych (APIs, Components, Resources, Systems, Domains)
- [ ] Ustal wspólne konwencje notacji i kolorowania

### Podczas tworzenia diagramów:
- [ ] Zacznij od L1 (System Context) - najwyższy poziom
- [ ] Przejdź do L2 (Container) tylko gdy potrzebne
- [ ] Opisz wszystkie strzałki przypadkami użycia
- [ ] Użyj konsystentnego kodowania kolorami
- [ ] Dodaj legendę i objaśnienia

### Po utworzeniu diagramów:
- [ ] Zweryfikuj z zespołem technicznym i biznesowym
- [ ] Umieść diagramy w repozytorium jako "Diagram as Code"
- [ ] Ustaw proces regularnej aktualizacji
- [ ] Połącz z ADR (Architecture Decision Records)
- [ ] Rozważ automatyzację generowania z metadanych software'u
- [ ] Włącz interaktywne przeglądanie i linkowanie między diagramami
- [ ] Użyj diagramów do onboardingu nowych członków zespołu

## 🔗 Dodatkowe Zasoby

### Frameworks i Standardy:
- **C4 Model**: https://c4model.com/ - oficjalna dokumentacja
- **Arc42**: https://arc42.org/ - szablon dokumentacji architektury
- **Structurizr**: https://static.structurizr.com/workspace/36141/diagrams/Containers.png - przykład diagramu C4

### Narzędzia Diagram as Code:
- **Mermaid**: https://mermaid.js.org/ - dokumentacja i przykłady
- **PlantUML**: https://plantuml.com/ - zaawansowane diagramy

### Methodyki Strategiczne:
- **Wardley Maps**: https://learnwardleymapping.com/ - nauka mapowania strategicznego
- **Event Storming**: https://www.eventstorming.com/ - warsztatowe odkrywanie procesów

### Inspiracje i Case Studies:
- **Spotify Visualization**: https://engineering.atspotify.com/2022/07/software-visualization-challenge-accepted - kompleksowe podejście do wizualizacji architektury na dużą skalę
- **Spotify System Model**: https://backstage.io/docs/features/software-catalog/system-model - standardowy model metadanych
- **Backstage Software Catalog**: https://backstage.io/docs/features/software-catalog/software-catalog-overview - platforma do zarządzania software catalog
- **Architecture Katas**: https://nealford.com/katas/ - ćwiczenia architektoniczne

### AI i Automatyzacja:
- **GitHub Copilot Custom Instructions**: https://docs.github.com/en/copilot/how-tos/custom-instructions/adding-repository-custom-instructions-for-github-copilot
- **Cursor Rules**: https://docs.cursor.com/context/rules - konfiguracja AI assistant

---

*Kluczowe przesłanie: Dobre modelowanie architektury to balans między szczegółowością a czytelnością. Skup się na L1 i L2 diagramów C4, trzymaj je blisko kodu i regularnie aktualizuj. Wizualizacje są potężniejsze niż tekst - użyj ich mądrze. Jak pokazuje doświadczenie Spotify, standardowy model metadanych + automatyzacja generowania diagramów = zawsze aktualna dokumentacja architektoniczna, która wspiera onboarding, cross-team collaboration i podejmowanie decyzji.*