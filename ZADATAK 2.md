ZADATAK 2.


1. Ključni dijelovi sustava
Naplata parkiranja: Ovo je najvažniji dio sustava, jer omogućava naplatu parkiranja prema vremenu zauzetosti parkirališnog mjesta. Proces naplate treba biti precizan i siguran, bez mogućnosti pogrešaka.
Praćenje slobodnih mjesta: Sustav mora prikazivati broj slobodnih mjesta u garaži, uključujući broj slobodnih mjesta po katu. Ovaj podatak mora biti ažuriran u stvarnom vremenu.
Mjesečni reporti: Vlasnik garaže treba imati uvid u mjesečne izvještaje o poslovanju garaže, uključujući analizu popunjenosti i financijsku isplativost "kišne akcije".
Identifikacija korisnika: Potrebno je osigurati identifikaciju korisnika garaže, kako bi se osigurao pravilan pristup i naplata.
2. Ključni procesi
Proces naplate: Na naplatnim aparatima korisnici plaćaju prema vremenu parkiranja. Sustav treba pratiti vrijeme koje je korisnik proveo na parkiralištu i obračunati cijenu.
Praćenje slobodnih mjesta: Sustav mora stalno pratiti broj slobodnih mjesta u garaži i prikazivati ovu informaciju korisnicima.
„Kišna akcija“: Ako je automobil parkiran na nenatkrivenom mjestu i bio izložen kiši više od 33% vremena parkiranja, primjenjuje se popust od 50% na cijenu.
Izvještaji za vlasnika garaže: Sustav mora generirati mjesečne izvještaje s podacima o popunjenosti, prihodima i učinkovitosti "kišne akcije".
3. Potencijalni problemi
Točnost naplate: Klijent zahtijeva da naplata bude točna i bez grešaka, što znači da sustav mora biti vrlo precizan u praćenju vremena parkiranja i obračunu cijene.
Ažuriranje podataka: Praćenje slobodnih mjesta mora biti ažurirano u stvarnom vremenu, što može predstavljati tehničke izazove u većim garažama.
Kišna akcija: Potrebno je pravilno pratiti uvjete za primjenu "kišne akcije" (kada je automobil bio parkiran na kiši 33% vremena).
Sigurnost podataka: Sustav mora osigurati identitet korisnika i zaštitu osobnih podataka.
4. Arhitektura rješenja
4.1. Dizajn baze podataka
Baza podataka treba pohranjivati podatke o korisnicima, parkirnim mjestima, naplatama i izvještajima. Evo osnovne ideje za dizajn baze:

Tablica korisnici: Pohranjuje informacije o korisnicima (ID, ime, prezime, način naplate).
Tablica parkirna_mjesta: Sadrži podatke o parkirnim mjestima (ID, kat, natkriveno/nenatkriveno, zauzetost).
Tablica naplate: Pohranjuje podatke o naplati (ID, korisnik, vrijeme ulaska, vrijeme izlaska, cijena).
Tablica izvještaji: Pohranjuje mjesečne izvještaje o poslovanju (mjesečni izvještaj, broj slobodnih mjesta, prihod).

DIJAGRAMI

1.Dijagram arhitekture sustava

         
┌────────────────────┐
│  Korisnik (Aplikacija)  │
└────────────────────┘
     ↓
┌────────────┐  ┌────────────┐  ┌────────────────────┐
│  Naplatni aparat │  │ Garaža (Server) │  │   Baza podataka   |
└────────────┘  └────────────┘  └────────────────────┘
     ↓     ↓     ↓
┌────────────┐  ┌────────────┐  ┌────────────────────┐
│  Naplata podataka|  │  Ažuriranje   |  │ Pohrana podataka     |
└────────────┘  └────────────┘  └────────────────────┘
     ↓     ↓
┌────────────┐  ┌────────────┐
│  slobodnih mjesta │  │ i izvještaji   |
└────────────┘  └────────────┘
     ↓
┌────────────────────┐
│  Mjesečni izvještaj|
└────────────────────┘


  2.Dijagram procesa naplate

      +-------------------+
    |   Korisnik ulazi  |
    |   u garažu        |
    +-------------------+
             |
             v
    +---------------------+
    |  Započni mjerenje    |
    |  vremena parkiranja |
    +---------------------+
             |
             v
    +---------------------+
    |  Plaćanje na        |
    |  naplatnom aparatu  |
    +---------------------+
             |
             v
    +---------------------+
    |  Izlazak iz garaže  |
    +---------------------+
PSEUDOKOD KLJUČNIH PROCESA 

1.Pseudokod za naplatu parkiranja:

Function IzracunajCijenu(parkingStart, parkingEnd, natkriveno, pokisnuto):
    cijena = (parkingEnd - parkingStart) * osnovna_cijena_po_satu
    if natkriveno == False:
        cijena = cijena * 0.5  // Kišni popust za nenatkrivena mjesta
    if pokisnuto == True:
        cijena = cijena * 0.5  // Kišni popust za pokisnuta mjesta
    return cijena

2.Pseudokod za praćenje slobodnih mjesta:

Function AžurirajSlobodnaMjesta():
    for svaki kat u garaži:
        brojSlobodnih = 0
        for svako parkirno mjesto u katu:
            if mjesto je slobodno:
                brojSlobodnih += 1
        prikazi(brojSlobodnih)  // Ažuriraj broj slobodnih mjesta na ekranu

ZAKLJUČAK
Sustav za vođenje parkirališta mora biti precizan u naplati parkiranja, osigurati ažuriranje informacija u stvarnom vremenu i generirati izvještaje za analizu poslovanja. Uz to, sustav mora omogućiti praćenje "kišnih akcija", slobodnih mjesta, te osigurati siguran pristup i identifikaciju korisnika.

