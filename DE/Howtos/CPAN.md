_Achtung_

Im [Wiki](https://wiki.fhem.de/wiki/CPAN) veröffentlicht!




# CPAN

Das CPAN, Comprehensive Perl Archive Network, ist ein weltweit verteiltes Netzwerk für Perl-Module, das seit 1995 besteht und aktuell etwa 200 000 Module umfasst.

Siehe auch hier eine [Zusammenfassung des CPAN-Projektes](https://www.cpan.org/modules/INSTALL.html).

## Clients

### Plattformunabhängig

Das CPAN bietet drei plattformunabhängige Clients an, von denen zwei hier beschrieben werden. Die _Empfehlung_ ist, `cpanm` zu nutzen.

#### cpanminus
[cpanminus](https://metacpan.org/pod/distribution/App-cpanminus/bin/cpanm) (``cpanm``) ist der bevorzugte Weg, wie CPAN-Pakete installiert werden sollten. cpan-minus ist, wie ``cpan`` ein CPAN-Paket, das aber auch für viele Betriebssystem als fertiges Paket portiert wurde. 

cpan-minus bietet einen [Quickstart](http://cpanmin.us/) an, der auf jedem System läuft, auf dem Perl installiert ist. Dazu muss folgender Befehl auf der Kommandozeile ausgeführt werden:

    curl -L https://cpanmin.us | perl - App::cpanminus
    
Aus Sicherheitsgründen sollte vor Ausführung des Befehls überprüft werden, was unter [cpanmin.us](http://cpanmin.us/) zu finden ist, da ggf. Schadcode unbemerkt eingeschmuggelt werden könnte.

Ist der Client ``cpanm`` installiert, kann mit 

    cpanm Paket::Name
    
ein Paket (in diesem Falle das nicht-existende Paket ``Paket::Name``) installiert werden. Die Option ``--sudo`` sorgt dafür, dass cpanminus  die Installation als Superuser versucht (ggf. muss ein Passwort eingegeben werden).

#### Exkurs: cpan-outdated

Das Paket [`cpan-outdated`](https://metacpan.org/pod/distribution/cpan-outdated/script/cpan-outdated) erzeugt eine cpanminus-kompatible Liste an CPAN-Paketen, die aktualisiert werden können, z.B.

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

#### Debian und Derivate (Ubuntu, Raspbian, etc.)

Vom Debian-Projekt werden viele, aber lange nicht alle, Pakete des CPAN auch als Pakete für den eingebauten Paketmanager `apt` [bereitsgestellt](https://packages.debian.org/stable/perl/). Dort sind momentan etwa 4 000 Pakete verfügbar, d.h. rund 2% der im CPAN verfügbaren Pakete. Es ist nicht immer trivial, ein Paket zu finden. Ein einfacher Fall ist z.B. das Paket `Readonly`, der über `cpanm Readonly` oder `apt-get install libreadonly-perl` installiert werden könnte. Im Allgemeinen kann man sagen, dass sich der Name des `apt`-Paketes aus dem Prefix `lib`, gefolgt vom Paketnamen in Kleinbuchstaben, bei dem die `::` durch `-` ersetzt wurden, und dem Suffix `-perl` zusammensetzt:

| CPAN                | Debian-Paket              |
|---------------------|---------------------------|
| Rose::URI           | librose-uri-perl          |
| Sah::Schemas::Rinci | libsah-schemas-rinci-perl |

Kein Beispiel wäre vollständig ohne Ausnahme, z.B.:

[`libromana-perligata-perl`](https://metacpan.org/pod/distribution/Lingua-Romana-Perligata/lib/Lingua/Romana/Perligata.pm) installiert das Perl-Paket [`Lingua::Romana::Perligata`](https://metacpan.org/pod/distribution/Lingua-Romana-Perligata/lib/Lingua/Romana/Perligata.pm), müsste nach der selbstgewählten Konvention aber `liblingua-romana-perligata-perl` heißen.


Vorteilhaft ist, dass man die Pakete zusammen mit anderen Debian-Paketen automatisch auf dem aktuellen Stand halten kann, z.B. [`unattended-upgrades`](https://wiki.debian.org/UnattendedUpgrades) - man spart so eine doppelte Implementierung der Updates.

Wiederum von Nachteil ist, dass man mit einer auf ein Release festgelegten Quelle irgendwann auch keine Updates der Perl-Pakete mehr enthält. 

#### SuSE Linux

YaST bietet aktuell etwa 3 121 der rund 200 000 Pakete in [`devel:languages:perl`](https://build.opensuse.org/project/show/devel:languages:perl) an, dazu kommen noch einige Community-Pakete mit einer trivial nicht feststellbaren Anzahl an Paketen. Im Paket [`perl-App-cpanminus`](https://build.opensuse.org/package/show/devel:languages:perl:CPAN-A/perl-App-cpanminus) ist `cpanm` enthalten.

#### RedHat Linux



#### MacOS

Für MacOS gilt, dass das installierte Perl den `cpan`-Client und eine Auswahl an Module mitbringt. `cpanm` lässt sich installieren und sollte auch der Weg der Wahl sein. Es ist außerdem möglich, Pakete über [MacPorts](https://www.macports.org/) zu installieren. MacPorts bietet noch weniger Pakete (aktuell 1 797 für Perl 5.26, 1 799 für Perl 5.28) als Debian.

#### Windows

[ActiveState](https://www.activestate.com/products/perl/downloads/) bietet eine Perl-Distribution an, die bereits mit einigen Module, 214 bei [Perl 5.28](https://platform.activestate.com/ActiveState/ActivePerl-5.28), ausgeliefert wird. 


## Empfohlene Pakete

Im FHEM-Umfeld werden aktuell rund 120 CPAN-Pakete (mit Sub-Paketen) eingesetzt die keine [Core-Module](https://www.perl.com/article/what-is-the-perl-core-/) sind und ggf. für ein FHEM-Modul [nachinstalliert]([Meta]) werden müssen:

* Authen::OATH
* AutoLoader
* B
* Carp
* Color
* Compress::Zlib
* Convert::Base32
* Cpanel::JSON::XS
* Crypt::Argon2
* Crypt::CBC
* Crypt::Cipher::AES
* Crypt::ECB
* Crypt::Mode::CBC
* Crypt::MySQL
* Crypt::NaCl::Sodium
* Crypt::Rijndael
* Crypt::Rijndael_PP
* Crypt::URandom
* DBI
* DBI::Const::GetInfoType
* Data::Dumper
* Data::UUID
* Date::Parse
* DateTime
* Device::Firmata
* Device::Firmata::Base
* Device::Firmata::Constants
* Device::Firmata::Error
* Device::Firmata::Language
* Device::Firmata::Platform
* Device::Firmata::Protocol
* Device::SerialPort
* Device::USB
* Digest::CRC
* Digest::SHA1
* Encode::Detect::Detector
* Expect
* File::HomeDir
* HTML::Entities
* HTML::Parser
* HTTP::Cookies
* HTTP::Daemon
* HTTP::Headers
* HTTP::Request
* HTTP::Request::Common
* IO::Interface::Simple
* IO::Socket::Multicast
* IO::Socket::Multicast6
* IO::Socket::SSL
* IO::Socket::Timeout
* IO::String
* Image::ExifTool
* Image::LibRSVG
* Image::Size
* Inline
* JSON
* JSON::MaybeXS
* JSON::XS
* JSON::backportPP
* JsonMod::JSON::Path::Node
* LWP
* LWP::Simple
* LWP::UserAgent~6
* Linux::Inotify2
* LiquidCrystal
* Lirc::Client
* List::MoreUtils
* MIME::Lite
* MP3::Info
* MP3::Tag
* MP3::Tag::CDDB_File
* MP3::Tag::Cue
* MP3::Tag::File
* MP3::Tag::ID3v1
* MP3::Tag::ID3v2
* MP3::Tag::ImageExifTool
* MP3::Tag::ImageSize
* MP3::Tag::Inf
* MP3::Tag::LastResort
* MP3::Tag::ParseData
* Mail::IMAPClient
* Mojolicious~5.54
* Net::Address::IP::Local
* Net::Bonjour
* Net::FTPSSL
* Net::Jabber
* Net::MQTT::Constants
* Net::MQTT::Message
* Net::MQTT::Message::JustMessageId
* Net::Rendezvous
* Net::SIP
* Net::SIP::Packet
* Net::SMTP::SSL
* Net::Telnet
* Net::UPnP::AV::MediaRenderer
* Net::UPnP::AV::MediaServer
* Net::UPnP::ControlPoint
* Net::UPnP::Device
* Net::UPnP::Service
* Net::XMPP::Namespaces
* Nmap::Parser
* Path::Tiny
* Paws::Polly
* Perl::PrereqScanner::NotQuiteLite
* RPC::XML::Client
* RPC::XML::Server
* RiveScript
* SOAP::Lite
* Text::Iconv
* Try::Tiny
* UPnP::Common
* UPnP::ControlPoint
* URI::Escape
* WWW::Jawbone::Up
* Win32::SerialPort
* XML::LibXML
* XML::Parser::Lite

[Liste als plain text](https://raw.githubusercontent.com/fhem/doc-wiki/master/DE/Howtos/fhem-cpan-modules.txt), z.B. um sie bei einer automatisierten Installation verwenden zu können. Die Liste wurde mit `Perl::PrereqScanner` aus dem `FHEM/`-Verzeichnis erstellt, durch `Core::List` gefiltert und mit `cpanm` auf Nicht-CPAN-Module (z.B. `FHEM::Meta` oder `DevIO`) geprüft.

[[Kategorie:HOWTOS]]
[[Kategorie:Systemadministration]]
[[Kategorie:Perl]]
