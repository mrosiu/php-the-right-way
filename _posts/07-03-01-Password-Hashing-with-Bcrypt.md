---
title Hashowanie haseł za pomocą Bcrypt
isChild: true
---

## Hashowanie haseł za pomocą Bcrypt

Każdy kiedyś napisze aplikację, w której jedną z funkcjonalności będzie możliwość zalogowania się użytkownika. W takiej
aplikacji, dane autoryzacyjne (login i hasło) zwykle przechowywane są w bazie danych, aby za ich pomocą zautentykować
użytkownika. W takim przypadku bardzo istotną kwestią jest odpowiednie zakodowanie (zahashowanie) zapisanych haseł, aby
uniknąć sytuacji, w której po ataku hackerskim na bazę danych, konta Twoich użytkowników pozostaną dostępne
włamywaczom.

Na szczęście w PHP wbudowany jest prosty, acz skuteczny mechanizm hashowania dowolnych danych - Bcrypt. Po zastosowaniu
go, na podstawie skrótu nie ma możliwości odgadnięcia pierwotnej postaci zakodowanego ciągu znaków.

w PHP dostępnych jest kilka bibliotek bazujących ba Bcyrpt, których móżesz użyć w swojej aplikacji. 

* [Artykuł "How to Safely Store a Password" na stronie Coda Hale][3]
* [Strona projektu PHPass][4]

[3]: http://codahale.com/how-to-safely-store-a-password/
[4]: http://www.openwall.com/phpass/
