---
title: Instalacja w systemie Windows
isChild: true
---

## Instalacja w systemie Windows

PHP w systemie Windows można zainstalować na kilka sposobów. Pierwszym z nich jest instalacja
[binariów](php-downloads). Do wersji 5.3.0 można było korzystać z instalatora .msi, obecnie ten sposób instalacji
nie jest już wspierany.

Do nauki i lokalnego rozwijania aplikacji oprartych o PHP najlepiej użyć serwera WWW wbudowanego w dystrybucję.
Używając go, nie musisz się martwić o jego konfigurację. Jeżeli potrzebujesz czegoś więcej, możesz użyć jednego z
pakietów "all-in-one", który sprawnie zainstaluje dedykowany serwer WWW, PHP oraz bazę danych MysQL. Najbardziej
znanymi rozwiązaniami tego typu są [Web Platform Installer][wpi], [Zend Server CE][zsce], [XAMPP][xampp] oraz
[WAMP][wamp]. Używając ich, pamiętaj o tym, że takie środowisko może różnić się od produkcyjnego, działajcego np. na
Linuksie.

Jeżeli chcesz stworzyć środowisko produkcyjne w systemie Windows, najlepszym rozwiązaniem jest użycie serwera IIS7,
który uznawany jest obecnie za najszybszy i najbardziej stabilny serwer WWW dla Windows. Aby skonfigurować PHP na
serwerze IIS7 możesz użyć pluginu [phpmanager][phpmanager]. Pomocna może się okazać strona
[http://php.iis.net][php-iis].

Pamiętaj o tym, że development aplikacji w systemie znacznie różniącym się od docelowego może prowadzić do problemów
podczas instalacji aplikacji na serwerze produkcyjnym. Jeżeli tworzysz aplikację pod Windowsem, a uruchamiasz ją pod
Linuksem, rozważ możliwość użycia maszyny wirtualnej. W tym celu zainteresuj się projektami [Vagrant][vagrant], a także
[Puppet][puppet] lub [Chef][chef].

[php-downloads]: http://windows.php.net
[phpmanager]: http://phpmanager.codeplex.com/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[zsce]: http://www.zend.com/en/products/server-ce/
[xampp]: http://www.apachefriends.org/en/xampp.html
[wamp]: http://www.wampserver.com/
[php-iis]: http://php.iis.net/
[vagrant]: http://vagrantup.com/
[puppet]: http://www.puppetlabs.com/
[chef]: http://www.opscode.com/
