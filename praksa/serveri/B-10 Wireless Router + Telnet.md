OSNOVNA PODESAVANJA
===================

1. Povezati jedan racunar na ethernet port 1 (jedan od 4 porta koji NISU oznaceni kao internet)

2. Podesiti staticku IP adresu na racunaru da pripada opsegu 192.168.1.0/24

3. Pristupiti ruteru pomocu adrese 192.168.1.1, user: admin, pass:admin

4. Treba podesiti Static IP za Internet Connection type, u kartici Setup (default kartici koja se otvara po odlasku na stranicu rutera, 192.168.1.1)

5. IP adresa rutera ka internetu ce biti 192.168.253.33, maska /24, default gateway 192.168.253.1, DNS moze biti 8.8.8.8 ili 4.2.2.1

6. Lokalna IP adresa rutera treba biti konfigurisana po postavci zadatka (nesto poput 192.168.2.1)
	NAPOMENA: Nakon sto se promeni adresa rutera, neophodno je podesiti adresu racunara kojim se pristupa da bude clan te mreze (192.168.2.2 ili neka druga adresa iz 192.168.2.0/24)

7. DHCP treba enable-ovati, podesiti pocetnu adresu opsega prema postavci zadatka (npr. 192.168.1.100 da bi adrese pocinjale od stote). I podesiti broj DHCP adresa takodje prema postavci zadatka.

8. U toj fazi treba snimiti (save na stranici rutera) i proveriti da li je pristup internetu omogucen.

WIRELESS
========

1. Otvoriti karticu Wireless, i podkarticu Basic Wireless Settings

2. Tu se bira mod rada, npr Mixed

4. Treba podesiti SSID prema postavci zadatka (npr. lab55)

5. Treba odabrati kanal na kom ce raditi, opet, prema postavci zadatka

6. Treba disable-ovati SSID broadcast (onemoguciti javno prikazivanje mreze)

7. Tad treba snimiti, i preci na podkarticu Wireless Security

8. Tip zastite treba biti WEP

9. Sifra se upisuje u polje Key 1 i ono se bira u default key

10. Ovde je gotovo podesavanje wireless-a. Treba snimiti, i proveriti da li je wireless funkcionalan.

TELNET
======
Napomena: u ovom scenariju postoje 2 racunara koji ostvaruju telnet client/server komunikaciju.
	Telnet Server ostaje u lokalnoj mrezi (ethernet portovi na ruteru), a Telnet Client se povezuje na internet port na ruteru.

1. Neophodno je povezati client racunar na internet port rutera

2. Adresu client racunara treba konfigurisati tako da postoji vidljivost izmedju njega i internet porta rutera. (192.168.253.2 ili tako nesto, postoji u postavci zadatka)

3. Preko server racunara treba ponovo pristupiti ruteru, i otvoriti karticu Applications & Gaming, podkarticu Port Range Forward

4. U toj kartici treba dozvoliti pristup preko porta 23 ka adresi server racunara (npr. 192.168.2.15, uglavnom, staticku adresu)

5. Na server racunaru treba instalirati Telnet Server i Telnet Client uz pomoc Control Panel->Programs & Features->Turn On Windows Components

6. Na klientskom racunaru treba instalirati samo Telnet client

7. Na server racunaru treba pokrenuti telnet servis. (Win+R, services.msc, naci Telnet servis, promeniti startup type sa Disabled na Manual, pa se klikne apply, da bi se onda start dugme enable-ovalo, potom pokrenuti servis)

8. Na serveru treba pokrenuti u command promptu (sa admin pravima) tlntadmn -u <ime korisnika>, potom ukucati lozinku prema upitu

9. Korisnika koji ce se koristiti za konektovanje treba uclaniti u grupu Telnet Clients (Win+R, compmgmt.msc, Local Users and Groups, Groups, dupli klik na Telnet Clients, Add, i dodati odgovarajuceg korisnika)

10. Pokretanjem tlntadmn proveriti da li je telnet server pokrenut (u logu koji izbaci treba da pise running)

11. Sa klienta treba probati konekciju telnet <adresa internet porta rutera> (telnet 192.168.253.33). Koristiti korisnicko ime i lozinku korsnika kome je omogucen telnet pristup.

SNIMANJE KONFIGURACIJE
======================
1. Otvoriti Administration karticu na ruteru, podkartica Config Management

2. Pritiskom na backup, on ce ponuditi download fajla pod odredjenim imenom.

3. Za povratak konfiguracija ovaj fajl se moze odabrati pomocu Choose File

4. Pritiskom na Restore, snimljene konfiguracije se vracaju na ruter.
