# moja-firma-logistyka

**Agent zleceń transportowych dla polskiej firmy: usługi logistyczne.** Czyta zlecenie transportowe z PDF, sprawdza płatnika, liczy marżę z kosztu trasy i wariant z podwykonawcą, dobiera auto i proponuje decyzję z warunkami.

Pakiet branżowy paczki [moja-firma](https://github.com/majchrzycki-com/moja-firma). Procedura w formacie [Agent Skills](https://agentskills.io/specification) (`SKILL.md`) działa w Claude, ChatGPT i Codex, Microsoft 365 Copilot, Gemini oraz OpenClaw.

## Czego agent nie zrobi

Nie przyjmie zlecenia i nie ustali stawki. Przyjęcie należy do spedytora, stawka poniżej progu do kierownika spedycji, zwolnienie limitu do finansów, a termin płatności dłuższy niż dopuszcza polityka — do zarządu. Agent pokazuje, ile ten przewóz naprawdę kosztuje, czy płatnik mieści się w limicie i które auto może pojechać, żeby te decyzje zapadły na danych, a nie na tym, że „nazwa płatnika jest znajoma”.

Nie zastąpi też porządku w danych. Jeśli koszt trasy na relacji nie jest nigdzie zapisany, bo paliwo i opłaty drogowe księgujecie zbiorczo, agent nie ma z czym porównać stawki — i to jest najczęstszy powód, dla którego pierwsze podejście do takiego agenta kończy się ładną tabelą z pustą kolumną. W prawdziwej firmie zacznijcie od jednego arkusza z kosztem rzeczywistym pięciu najczęstszych relacji z ostatniego kwartału. Dopiero potem agent.

## Wypróbuj na danych ćwiczeniowych

W katalogu [`dane-cwiczeniowe/`](dane-cwiczeniowe/) są fikcyjne dane firmy: `flota.csv`, `flota.xlsx`, `parametry.csv`, `parametry.xlsx`, `platnicy.csv`, `platnicy.xlsx`, `relacje.csv`, `relacje.xlsx`, `zlecenie.pdf`. Pliki XLSX i CSV mają tę samą treść.

1. Zainstaluj procedurę `zlecenie-transportowe` (niżej).
2. Dodaj pliki ćwiczeniowe do wiedzy agenta albo załącz je do rozmowy.
3. Napisz:

```text
Mamy nowe zlecenie. Przeprowadź analizę według instrukcji projektu, licząc kodem na plikach z wiedzy.
```

4. Porównaj odpowiedź z [WYNIK-KONTROLNY.md](WYNIK-KONTROLNY.md). Jest tam też „krok z rzeczywistością”: jedna zmiana w danych i wynik, który agent powinien po niej pokazać.

## Instalacja

### Claude Code

```text
/plugin marketplace add majchrzycki-com/moja-firma
/plugin install moja-firma-logistyka@moja-firma
```

### Pozostałe narzędzia

```bash
node scripts/build.mjs
```

Skrypt tworzy `dist/skills/` dla Claude, Codex, OpenClaw i Copilot Cowork oraz `dist/instrukcje/` z tekstem do wklejenia w agencie Microsoft 365 Copilot, Gemie albo projekcie ChatGPT. Szczegóły instalacji w każdym narzędziu: [README rdzenia moja-firma](https://github.com/majchrzycki-com/moja-firma#instalacja).

## Ten sam agent krok po kroku

- [Agent zleceń transportowych w Claude](https://majchrzycki.com/blog/agent-zlecen-transportowych-w-claude-krok-po-kroku?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zlecenie-transportowe)
- [Agent zleceń transportowych w Microsoft 365 Copilot](https://majchrzycki.com/blog/agent-zlecen-transportowych-w-microsoft-365-copilot-krok-po-kroku?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zlecenie-transportowe)
- [Agent zleceń transportowych w ChatGPT](https://majchrzycki.com/blog/agent-zlecen-transportowych-w-chatgpt-krok-po-kroku?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zlecenie-transportowe)
- [Agent zleceń transportowych w Gemini](https://majchrzycki.com/blog/agent-zlecen-transportowych-w-gemini-krok-po-kroku?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zlecenie-transportowe)

Gdzie ten agent mieści się w całej firmie i jakich jeszcze agentów potrzebuje usługi logistyczne: [darmowy poradnik branżowy](https://majchrzycki.com/transformacja-agenci-ai/uslugi-logistyczne?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zlecenie-transportowe#pobierz).

## Na własnych danych

Zacznij od procedury `kontrola-danych` z rdzenia moja-firma na eksporcie z Waszego programu. Jeśli kolumny nazywają się inaczej, agent pokaże przypisanie i poprosi o potwierdzenie. Pierwszy tydzień puść agenta obok normalnej pracy jednej osoby i porównuj wyniki.

Procedura nie jest poradą prawną, podatkową ani handlową. Wynik sprawdza osoba, która za niego odpowiada.

## Licencja

[MIT](LICENSE), dla procedur, skryptów i danych ćwiczeniowych.

Autor: [Krzysztof Majchrzycki](https://majchrzycki.com/o-mnie?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zlecenie-transportowe), wdrożenia AI w polskich firmach.

---

**English:** moja-firma-logistyka is an industry pack of the open [moja-firma](https://github.com/majchrzycki-com/moja-firma) Agent Skills for Polish SMBs. It contains one `SKILL.md` procedure (in Polish), fictional practice data and expected results. MIT licence.
