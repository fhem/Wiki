# CPAN

## Clients

### Direkte Clients

#### cpanminus
[cpanminus](https://metacpan.org/pod/distribution/App-cpanminus/bin/cpanm) (``cpanm``) ist der bevorzugte Weg, wie CPAN-Pakete installiert werden sollten. cpan-minus ist, wie ``cpan`` ein CPAN-Paket, das aber auch für viele Betriebssystem als fertiges Paket portiert wurde. Dies ist auch der zu bevorzugende Weg.

cpan-minus bietet einen [Quickstart](http://cpanmin.us/) an, der auf jedem System läuft, auf dem Perl installiert ist. Dazu muss folgender Befehl auf der Kommandozeile ausgeführ werden:

    curl -L https://cpanmin.us | perl - App::cpanminus
    
Aus Sicherheitsgründen sollte vor Ausführung des Befehls überprüft werden, was unter [cpanmin.us](http://cpanmin.us/) zu finden ist, da ggf. Schadcode unbemerkt eingeschmuggelt werden könnte.

Ist der Client ``cpanm`` installiert, kann mit 

    cpanm Paket::Name
    
ein Paket (in diesem Falle das nicht-existende Paket ``Paket::Name``) installiert werden. Die Option ``--sudo`` sorgt dafür, dass cpanminus  die Installation als Superuser versucht (ggf. muss ein Passwort eingegeben werden).

#### Exkurs: cpan-outdated

Das Paket [``cpan-outdated``](https://metacpan.org/pod/distribution/cpan-outdated/script/cpan-outdated) erzeugt eine cpanminus-kompatible Liste an CPAN-Paketen, die aktualisiert werden können, z.B.

    $ cpan-outdated 
    A/AN/ANDK/CPAN-2.27.tar.gz
    L/LE/LEONT/Test-Harness-3.42.tar.gz
    B/BI/BINGOS/Archive-Tar-2.36.tar.gz
    T/TO/TODDR/autodie-2.32.tar.gz
    R/RU/RURBAN/B-Debug-1.26.tar.gz
    I/IL/ILMARI/bareword-filehandles-0.007.tar.gz
    P/PJ/PJACKLAM/bignum-0.51.tar.gz
    X/XS/XSAWYERX/Carp-1.50.tar.gz
    L/LE/LEEJO/CGI-4.47.tar.gz
    A/AT/ATOOMIC/Clone-0.45.tar.gz
    M/ML/MLEHMANN/common-sense-3.75.tar.gz
    P/PM/PMQS/Compress-Raw-Bzip2-2.093.tar.gz
    P/PM/PMQS/Compress-Raw-Zlib-2.093.tar.gz
    P/PM/PMQS/IO-Compress-2.093.tar.gz
    H/HM/HMBRAND/Config-Perl-V-0.31.tgz
    A/AT/ATOOMIC/TimeDate-2.33.tar.gz
    P/PM/PMQS/DB_File-1.853.tar.gz
    H/HU/HURRICUP/Devel-Camelcadedb-v2019.1.tar.gz
    P/PJ/PJCJ/Devel-Cover-1.36.tar.gz
    A/AT/ATOOMIC/Devel-PPPort-3.58.tar.gz
    M/MS/MSHELOR/Digest-SHA-6.02.tar.gz
    R/RJ/RJBS/Email-Sender-1.300034.tar.gz

Sehr nützlich ist die Kombination aus cpanminus und cpan-outdated:

    cpan-outdated | cpanm --sudo
    
Diese Befehlssequenz aktualisiert alle aktualisierbaren CPAN-Pakete mit Hilfe von cpanminus (als Superuser).

#### cpan

[``cpan``](https://metacpan.org/pod/CPAN) ist der mit jeder Perl-Installation mitgelieferte Client für das CPAN und lässt sich entweder mit

    perl -MCPAN -e shell

oder

    cpan
    
starten. Es wird ein interaktiver Client gestartet; mit ``h`` kann eine sehr umfangreiche Hilfe aufgerufen werden.

Ein Modul lässt sich am einfachsten mit

    cpan install PAKET::NAME
    
installieren (hier das nicht-existente Paket ``PAKET::NAME``). ``cpan`` eignet sich weniger gut um Module zu installieren oder zu aktualisieren, aber sehr gut um nach Paketen zu suchen:

    i /JSON/
    
findet jedes Paket, das die Zeichenkette ``JSON`` im Bereich Autor, Bundle, Distribution oder Modul enthält. Das sind meist viele Ergebnisse, aber liefert einen Überblick "was geht".

Erfahrungsgemäß ist ``cpan`` recht störrisch in der Handhabung. Deshalb empfehle ich die Nutzung von cpanminus.

### OS-Paketmanager

#### Debian und Derivate (Raspbian, etc.)


#### MacOS

#### Windows

#### SuSE Linux

#### Ubuntu

#### RedHat Linux


## Empfohlene Pakete

[[Kategorie:HOWTOS]]
[[Kategorie:Systemadministration]]
[[Kategorie:Perl]]