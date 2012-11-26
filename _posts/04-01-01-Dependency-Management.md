---
title: Zarządzanie zależnościami
---

# Zarządzanie zależnościami {#dependency_management_title}

PHP posiada tysiące bibliotek, frameworków i komponentów. Tworząc swój projekt wybierzesz prawdopodobnie kilka z nich
- będą to jego zależności. Przez wiele lat PHP nie posiadał sprawnie działającego sposobu na zarządzanie zależnościami.
Nawet jeżeli udało Ci się zestawić razem potrzebne Ci biblioteki, musiałeś ręcznie zadbać o ich dołączenie do projektu.
Nigdy więcej. 

PHP dysponuje dwoma niezależnymi systemami pakietów. Są nimi Composer i PEAR. Zastanawiasz się pewnie który wybrać.
Otóż wszystko zależy od tego w jaki sposób chcesz go użyć.

 * Jeżeli potrzebujesz stworzyć zależności dla konkretnego projektu - użyj **Composera**.
 * Jeżeli potrzebujesz zarządzać zależnościami dla całej instalacji PHP - użyj **PEARa**.

Innymi słowy, pakiety Composera będą dostępne jedynie w projekcie, dla którego je przygotujesz, podczas gdy biblioteki
PEARa będą dostępne dla wszystkich aplikacji w obrębie instalacji PHP. Mimo, że PEAR wydaje się być łatwiejszym
podejściem, istnieje wiele przesłanek, aby zarządzać swoimi zależnościami per projekt, czyli używając Composera.
