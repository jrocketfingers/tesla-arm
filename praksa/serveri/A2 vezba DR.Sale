#NAPOMENA: za izradu ove vezbe potrebne su 2 virtuelne masine, jedna pod Win2k8 i jedna na kojoj ce biti instaliran windows 7 .
Server : 
VM sa win2k8: RAM: 512MB HDD1: 20GB; HDD2: 20GB - DISKOVI NE SMEJU BITI NA SATA CONTROLLERU!
Client : 
VM SA Windows 7(64x). RAM:512MB, HDD:20GB, boot order treba da bude network, hdd (flopy i cd treba da su iskljuceni) HDD takodje mora biti na SATA kontroleru

Pravljenje virtuelne masine sa win2k8
1)Ides New Virtual Machine - 
Name :windowsdeployment 
Operating Sistem: Microsoft Windows
Version:Windows 2008

2) RAM:512 mb

3)Kreiras Hard disk 20gb

4)Settings-Storage( obrises ovaj jedan posto ne smeju da budu na SATA Controller-u)
Dodas dva hard diska na IDE Controller-a.

5)Ubacis instalacioni disk za win2k8  en_windows_server_2008_datacente_enterpri...

6)Pokreni instal.

7)Tamo Odaberes Enterprise (Full Instal),Biras Custom,Hard 1 i pokrene se proces instalacije

8)Kad se pokrene server po prvi put treba podesiti password (!passw0rd) pa onda instalirati Guest Additions(Devices-Instal Guest Additions) za virturelnu masinu

8.5 Ovde je zgodno napraviti SNAPSHOT ( u virtualbox-u pod nazivom clean), kamerica u uglu (ili Machine  - Take Snapshot uneti clean, OK)

9)Dodeliti serveru ip adresu: 192.168.1.1,(ovo zavisi od postavke zadatka, obicno prvu ili poslednju adresu iz mreze koja vam je data u postavci treba da dodelite serveru)

10)ovde je potrebno instalirati .NET Framework 3.5 a prethodno dodati Shared Folder sa instalacijomNetFrameworka3.5( Devices-Shared Folder- Add Shared Folder (plavi kofercic sa plusicem u gornjem desnom uglu dijaloga) nacu folder u kome se nalazi instalacije (C:\Users\409\mreznainstalacija\ pa izaberes NETFramework3_5) 

11)Moras da dozvolis u Control Panel-Network and Sharing Center-Network discovery - on)

12)My Computer-Map Network Drive-Browse-NetFramework pa instaliras .NETFramework

13)Izbaci share i obrisi ga (disconnect) jer ti vise ne treba

14)Devices-CD-KB3AIK (ovo je disk sa instalacijom Windows Automated installation Kit-a) potom instaliraj WAIK 

15)instalirati aktivni direktorijum , start-dcpromo , create new domain-skola.com-Win 2008- Gore u Devices ubaciti instalacioni disk za server 2008

16)instalirati DHCP server: ides na server add roles-dhcp , uraditi validaciju DNSa ( validate treba da pozeleni)  - wins is not required
add scope (parametri opsega su dati u postavci zadatka , procitajte postavku)
Scope Name: reminst
starting ip ad : 192.168.1.10
ending ip ad: 192.168.1.30
subnet mask : 255.255.255.0
default gate: 192.168.1.1
potom next- i disable DHCPV6
samo next do kraja

17)Proveri da li se vidi drugi hard disk kad otvorite Computer, ako se ne vidi ides na start-Administrattive Tools- Computer Management - Storage - Disk Management automatski ce vam ponuditi da napravi MBR tabelu particija , samo kliknuti OK. Potom desni klik
na drugi disk (Disk1), pa potom - New Volume , napraviti novi volumen , samo stiklirati Perfom a quick format i sacekati da se zavrsi formatiranje diska.

18)Instalirati Windows Deployment Services: start-server manager-add roles - windows deployment services (stiklirati oba ponudjena servisa tokom instalacije, Transport Server i Deployment Server)
ides u start-administative tools- windows deployment services-expandujes server pa desni klik na njega i configure server-(stavi putanju drugog diska za repozitorijum E:\RemoteInstall ) - potom stikliras port 67 i Dhcp option 60
obelezi respond to all comoputers (samoto , NE opciju ispod) - potom na kraju NE STIKLIRAJ ADD IMAGES

20)Dodati Boot i install images u repozitorijum 
ubaci win7 instalacioni disk pa ides na windows deployment service potom za folder Boot images - Add Boot images(desnoklik) - Add boot image (na cd-u pronaci folder sources oa u njemu boot.wim - Image name :Windows 7 BootImage) i Next, sacekati da doda sliku.
potom Instal images, desnoklik - Add Instal imagee (za Image Group Name staviti Windows 7 Image Group ,na cd-u sources-instal.wim - stiklirati samo Windows 7 Proffesional - ostavi default name stiklirano, Next i sacekati da se doda.


21)Napravi folder Capture u E:\RemoteInstall\Images (E je tvoj drugi disk , ako nije stavi odgovarajuce slovo)

22)U windows deployment services exportuj instalacionu sliku 
 folderu Install Images,desnoklik na Windows 7(ime koje si dao u predhodnom koraku image grupi (Windows 7 Image Group)) Export image pronadji folder koji si napravio u 21. sacuvaj sliku pod imenom capture.wim u tom folderu (E:\RemoteInstall\Images\Capture)

23)Potom Start->All Programs->Microsoft AIK->Windows System Image Manager
Create distribution share- napravi dis_share na drugom disku ( u prozorcetu new-folder) - otvori ga potom-

24)Desno klik na windows image pa Select WIndows Image pa nadjite capture.wim (Na drugom disku pa vas folder remoteinstal-images-capture)
25)File-New Answer File
http://www.2shared.com/document/uk74Qi-j/Unattend.html fajl Unattend.doc
26)Iz Unattend.doc fajla konfigurises ,rastvoris u Windows Image-Componenets
i kad nadjes komponentu ides desni klik Add setting to Pass 1 windowsPE
i onda zavisno od podesavanja namestas.
27)Kad zavrsis sa celim WDSUnattend.xml fajlom ides- gore ikonica lici na papir preko njega je stiklirano(Validate Answer File)
Sacuvati fajl File-Save-nadjes folder E:\RemoteInstall\WdsClienUnattend i tu sacuvas kao wdsunattend.xml
28)Ides na Windows Deployment Services-otvoris server i onda desni klik (na WIN-RQPB...) pa otvoriti Properties, potom karticu  Client i stiklirati enable unattended installation a u x64 architecture - browse nadjes taj fajl  wdsunattend.xml
29)sad pravis new answer fail, prvo ides close answer file pa pravis new answer file
30)Microsoft-Windows-Shell-Setup
NAPOMENA. prvo ides add setting to pass 4 specialize i obrises sve sto se nalazi u ovome 
zato sto ti to ovde ne treba i odradis podesavanja.
31)Microsoft-Windows-UnattendedJoin\Identification ISTO KAO I U KORAKU 30)

32)Microsoft-Windows-International-Core napomena(imas dva takva radis
na ovme sto nema WINPe njega ne mozesda add , a i onako radis oobeSystem) sad ides
add setting to pass 7 oobeSystem .

33)Microsoft-Windows-Shell-Setup - desni klik add setting to pass 7 oobeSystem
i obrises sem ova dva sto ti trebaju : OOBE,UserAccounts

Sva podesavanja uraditi prema uputstvu u Unattend.doc, u tabeli sa razvijenim parametrima. 

34)potom sacuvas ImageUnattend.xml
potom ides na windows deployment services otvoris server-pa install images
- folder capture i u njemu desni klik na windows 7 Professional potom u njemu
ides desniklik Properties pa stikliras Allow image to install in unattended mode,select file
i tu nadjes imageunattend.xml

35) potom opet desni kilk na server WIN-RQPB(tj na server)-Directory Services
i u Format das mu PC%02# (ovime cete obeybediti da se imenuju instalirane masine kao PC01, PC02, PC03 ...), potom stikliras The following location , potom Browse i odaberes Computers

36)to je to sad kreiras novu masinu (kilijentsku) das joj ime test - windows 7 64bit sve normalno dalje
potom u settings , u IDE Controller hard disk stavis U IDE a ovaj obrises sto je u SATA cont.
u system Boot Order - samo 1)Network 2)Hard Disk i to je to.

37)Pokrenes klijentusku masinu i pritisnes f12 da bi se pokrenula mrezna instalacija

******bitno je da budu u istoj intnet mrezi..network adapters-name intnet :)
