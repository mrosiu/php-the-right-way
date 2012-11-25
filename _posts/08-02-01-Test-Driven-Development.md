---
title: Test-Driven Development
isChild: true
---

## Test-Driven Development

Cytując [Wikipedię](http://pl.wikipedia.org/wiki/Test-driven_development):

> Test-driven development (TDD) jest techniką tworzenia oprogramowania, która polega na wielokrotnym powtarzaniu kilku kroków: najpierw programista pisze automatyczny test sprawdzający dodawaną funkcjonalność. Test w tym momencie nie powinien się udać. Później następuje implementacja funkcjonalności. W tym momencie wcześniej napisany test powinien się udać. W ostatnim kroku, programista dokonuje refaktoryzacji napisanego kodu, żeby spełniał on oczekiwane standardy. Technika została stworzona przez Kenta Becka. Można jej też używać do poprawiania istniejącego kodu.

Istnieje kilka sposób testowania aplikacji, których możesz użyć podczas rozwijania swojej aplikacji.

### Testy jednostkowe

Testy jednostkowe są techniką, która umożliwia sprawdzenie, czy funkcje, klasy i metody działają tak jak powinny -
przez cały cykl ich życia. Sprawdzanie ich wewnętrznej logiki odbywa się poprzez ich wywoływanie z różnymi parametrami
wejściowymi i badaniu ich odpowiedzi za pomocą odpowiednich asercji. Jeszcze dokładniejsze wyniki testów oraz bardziej
kompletne pokrycie kodu testami można uzyskać dzięki wstrzykiwaniu zależności oraz korzystaniu z "mocków".

Kiedy tworzysz klasę lub funkcję, powinieneś napisać test jednostkowy pokrywający i testujący zachowanie, które powinna
posiadać. Najprostszym przykładem jest stworzenie testu, który sprawdzi, czy dla poprawnych danych wejściowych
funkcja/metoda działa prawidłowo, a dla złych - odpowiednio to obsługuje. Dzięki temu wykonując kolejne zmiany i
refaktoryzacje masz pewność, że kod wciąż działa tak jak powinien.

Testy jednostkowe znajdują zastosowanie również w open-source - dzięki nim możesz w łatwy sposób pokazać, że dana
funkcjonalność nie działa prawidłowo, a następnie po wprowadzeniu poprawki sprawdzić, że ona faktycznie działa. Jeżeli
prowadzisz projekt, w którym korzystasz z tzw. "pull requests", zdecydowanie powinieneś wymagać wykonania odpowiednich
testów jednostkowych.

[PHPUnit](http://phpunit.de) jest najbardziej znanym frameworkiem, dzięki którym łatwo rozpoczniesz korzystanie z
testów jednostkowych. Są również alternatywy:

* [SimpleTest](http://simpletest.org)
* [Enhance PHP](http://www.enhance-php.com/)
* [PUnit](http://punit.smf.me.uk/)

### Testy integracyjne

Cytując [Wikipedię](http://en.wikipedia.org/wiki/Integration_testing) (polskie tłumaczenie):

> Testowanie integracyjne, zwane także Integracją i Testowaniem (ang. Integration and Testing, "I&T") jest fazą produkcji oprogramowania polegającą na automatycznym testowaniu odpowiednich grup modułów jako całość. Testy integracyjne wykonuje się zwykle po wykonaniu odpowiednich testów jednostkowych, a przed testami funkcjonalnymi. Testowanie integracyjne odbywa się na modułach, które zostały przetestowane jednostkowo. Moduły grupuje się w większe zbiory, na których stosuje się odpowiednie testy ujęte w planie testu integracyjnego i dostarcza się zintegrowany produkt, gotowy do testowania funkcjonalnego.

Proces wykonywania testów integracyjnych rządzi się zasadami podobnymi do testowania jednostkowego, więc do ich
wykonywania możesz używać tych samych narzędzi.

### Testy funkcjonalne

Czasami znane również jako testy akceptacyjne. W odrożnieniu od testów jednostkowych, zamiast konkretnych fragmentów
kodu, testują one pełną aplikację. Takie testy zwykle korzystają z rzeczywistych danych i symulują zachowanie
prawdziwych użytkowników.

#### Narzędzia do testów funkcjonalnych

* [Selenium](http://seleniumhq.com)
* [Mink](http://mink.behat.org)
* [Codeception](http://codeception.com) framework do testowania zawierający narzędzia do testów akceptacyjnych
