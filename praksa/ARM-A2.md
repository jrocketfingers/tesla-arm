Windows Deployment Service - mrezna instalacija
===============================================

Informacije:
------------
# Server:
OS: Windows Server 2008
RAM: 512MB
HDD1: 20GB; HDD2: 20GB - NE SMEJU BITI NA SATA CONTROLLERU!

U instalaciji odabrati Enterprise (full installation!)

# Client:
OS: Windows 7(x64)

Na serveru:
-----------
Instalirati Guest Additions
Napraviti snapshot (u virtualbox-u) pod nazivom "clean".

Instalirati Windows AIK

Instalirati dcpromo (AD + DNS)

Instalirati DHCP (poslednjih 20 adresa iz opsega, bez WINS-a, bez DHCPv6)

Proveri da li se vidi drugi disk. Ako treba formatiraj ga u computer management (quick format!)

Instaliraj Windows Deployment Service (role)

U Windows Deployment Service-u desni klik na server pa configure server.
U zavisnosti od oznake drugog diska napravi putanju. U mom slucaju je bila G:\RemInstall
Stikliraj obe opcije.
Stavi respond to all comupters. NE stikliraj add images.

Montirajte Windows 7 instalacioni disk na CD ROM u VBox-u.
U Windows Deployment Server desni klik na Boot Images, pa Add Boot Image.
Tamo treba naci CD, pa sources, pa boot.wim
Postupak je isti za Install Images. Kao ime grupe stavi Windows 7 il tako nesto.
Od ponudjenih slika odaberi samo Windows 7 Professional. Ostavi stiklirano use default name and desc

Napravi folder Capture u X:\RemInst\Images (X je tvoj drugi disk)

U WDS izaberi Windows 7 instalacionu sliku koju si dodao, desnoklik na Export, pronadji folder koji si napravio, i sacuvaj sliku pod imenom capture.wim

Start->All Programs->Microsoft WAIK->Windows System Image Manager

Napravite Dis_share na drugom disku.
Create distribution share, pa na drugom disku napravite Dis_share.

Desnoklik na Windows Image, pa Select Windows Image, pa nadjite create.wim
