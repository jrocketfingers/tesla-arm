PRIMARNI DNS:
=============

Priprema:
=========
Desni klik na my computer, properties. Pogledati computer name i ako je ima <ime servera>.nesto (ns1.skola.com) treba obrisati suffix klikom na more i brisanjem suffixa.

Podesiti IP adresu na DNS-u.

Instalacija DNS servisa na serveru:
===================================
Add remove windows components -> Networking services -> stiklirati DNS. Ubaciti prvi instalacioni CD posto ce ga traziti u okviru instalacije.

Konfiguracija DNS-a:
====================
Administrative tools -> DNS -> <ime servera u listi> -> desni klik na new zone.

Next

Odabrati primary zone.

Ime zone treba biti po postavci zadatka (npr: skola.com).

Next

Next

Finish

Konfiguracija lookup zona (dodavanje A zapisa)
==============================================
U forward lookup zone naci domen, i desnim klikom na domen odabrati New Host (A).

Uneti ime servera i IP adresu.

---

Zatim desni klik na zonu pa properties zone.

U Start of authority (SOA):
---------------------------
U primary server polje dopisati suffix (ns1 -> ns1.skola.com i hostmaster -> hostmaster.skola.com)

U Name servers:
---------------
Treba kliknuti edit na postojeci unos i dodati suffix, opet. Klik na resolve bi trebao da automatski doda adresu dole u IP adresses.
Ako se to ne desi, onda nesto nije u redu. Moze se uneti IP adresa rucno, i kliknuti na add.

Ideja je imati vezan name i ip adresu.

U Zone Transfers:
-----------------
Kada se doda sekundarni DNS server, ovde mu se dozvoljava da prima update-ove od primarnog servera.

Provera konfiguracije primarnog servera:
========================================
U cmd promptu bi trebalo da uspesno pingujemo uz pomoc imena. (ping ns1.skola.com)



SEKUNDARNI DNS:
===============

Priprema:
=========
Ponovo, obrisati suffix servera (kao i na pocetku).

Podesiti IP adresu (kao i na pocetku).

Intalirati DNS:
===============
Kao i na pocetku! (isto je kao i za primarni dns)

Konfiguracija DNS-a:
====================
Administrative tools -> DNS -> <ime servera u listi> -> Forward lookup zone -> New zone

Next

Odabrati Secondary zone

U zone name ukuacti skola.com

Master DNS je primarni DNS server - uneti adresu primarnog DNS servera i kliknuti Add

Finish


Konfiguracija lookup zona (dodavanje A zapisa)
==============================================
U forward lookup zone naci domen, i desnim klikom na domen odabrati New Host (A).

Uneti ime sekundarnog servera (ns2) i njegovu IP adresu.

Dodavanje Name server zapisa
===========================
Na primarnom serveru otvoriti DNS (Administrative tools -> DNS -> <ime servera u listi>) desni klik na zonu skola.com -> Properties -> Kartica Name servers
Dodati dugi name server:
Uneti ns2.skola.com i kliknuti na Resolve, pa odabrati ip adresu koja se pojavila u listi

Preci na karticu Zone Transfers
Odabrati Only to servers listed on the name servers tab

Transfer zone
===============
Na sekundarnom serveru otvoriti DNS (Administrative tools -> DNS -> <ime servera u listi> -> Forward lookup zone)
Desni klik na skola.com zonu -> Transfer from master