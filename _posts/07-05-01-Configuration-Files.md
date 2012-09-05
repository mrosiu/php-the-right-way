---
title: Pliki konfiguracyjne
isChild: true
---

## Pliki konfiguracyjne

Jeżeli Twoja aplikacja używa zewnętrznych plików konfiguracyjnych, pamiętaj, że nie powinny być obe dostepne dla
zewnętrznego świata. Zalecane jest użycie jednego z poniższych sposobó ich zabezpieczenia:

- Trzymaj pliki konfiguracyjne poza DocumentRoot'em, dzięki czemu nie będą dostępne przez serwer WWW.
- Jeżeli musisz przechowywać je w DocumentRoot'cie, zmień ich rozszerzenie na `.php`. W tym przypadku, nawet jeżeli
skrypt zostanie wywołany bezpośrednio, jego zawartość nie będzie zwrócona do przeglądarki w oryginalnej formie.
- Zawartość plików konfiguracyjnych powinna zostać odpowiednio zabezpieczona - albo poprzez ich szyfrowanie, albo przy
użyciu zabezpieczeń oferowanych przez system plików (zmiana właściciela i/lub praw dostepu).
