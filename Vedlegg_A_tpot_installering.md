# T-Pot 22.04.0 installering

## Last ned ISO fil
https://github.com/telekom-security/tpotce/releases 

Vi benyttet "tpot_amd64.io"

## Mount ISO filen i en VM
Vi benyttet VM workstation. Følgende hardware ble valgt til vår VM:
- CPU: 4
- RAM: 16 GB
- Hard disk: 512 GB

**Sørg for at VMet er koblet til internett under installering**

_Vi benyttet skolen sin serverpark for å lage en VM_

Videre krav for oppsettet av tpot kan leses her: 

https://github.com/telekom-security/tpotce?tab=readme-ov-file

## Start VMen
I VM workstation **FØR** oppstart, velg ISO filen man lastet ned i forrige steg og start VMen
<img width="778" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/a36a0896-f3dc-479b-b1f2-c3e97baaf38b">

Velg "T-Pot 22.04.0 (AMD64)" og klikk ENTER

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/852a160f-4728-4104-a34e-930d4cda1dcf)

Velg deretter land, språk til keyboard og "debian archive mirror country". Vi valgte "Norway", "Norwegian" og "Norway"

Velg så "Debian mirror archive". Vi valgte "deb.debian.org"

Neste steg var å velge "HTTP proxy information". Vi lot den være blank og klikket continue

Vent litt til neste steg vises. Velg deretter hvilken type tpot man ønsker å installere. Vi valgte "Standard"

Velg deretter passord, web-brukernavn og -passord. Når dette er gjort vil installeringen fortsette. Dette kan ta opptil 10 minutter

## Konfigurering av tpot
Når installeringen er ferdig, benytt brukernavn "tsec" og passord konfigurert i forrige steg.

Start deretter filen "dps.sh":

```bash
  cd /opt/tpot/bin
  sudo ./dps.sh
```
Her får du en oversikt over alle tjenester tpot gir, hvor lenge de har vært aktive og status på disse.

## T-Pot Web UI
IP-adressen kommer opp når man først starter opp T-Pot (IP-adressene skjult med gul farge):

<img width="266" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/abbe1a46-a663-41b8-993c-8f8bfc79c3a8">

På en annen klient (vi benytter en Windows 10 klient) koblet til samme VLAN, gå inn på https://<your.ip>:64297

Logg inn med Web UI brukernavn og passord. Da vil man få opp dashboard til T-Pot:

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/730b391d-8677-45fc-8b59-14d2c0d926d8)

Herifra har man tilgang til diverse verktøy for å holde oversikt over T-Pot.

Går man inn på https://<your.ip>:64294 og logger inn med administrator brukernavn og passord, vil man få administratorverktøy. Her fikk vi en feilmelding, samme feilmelding som man får på oppstart til T-Pot "Failed to start, raise network interfaces"

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/41c7d689-251e-418e-83c2-d6cd82ec6215)
![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/2b15edd8-bc35-4bc1-be44-1906e0ac3495)

Måten vi løser dette på er å gjøre følgende i CLI på T-pot:
```bash
  sudo route
```
Her ser du hvilken interface (iface) som er tilknyttet destination: default. Når man har denne skriver man følgende
```bash
  cd /etc/network
  sudo nano interfaces
```
Deretter endrer man "The Primary Network Interface" til den man fant i forrige steg

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/244165f0-afc9-4638-a0f9-803860657a8b)

Kjør deretter:
```bash
  sudo reboot
```
Legg merke til at <your ip> endrer seg. 
```bash
  sudo systemctl status networking.service
```
Og bekreft at den er "aktiv"

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/e46f9d88-4e0b-40f0-a5d7-c84e9044f539)

## Oppsett
Under er et bilde av hvordan T-Pot er bygd opp:

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/c5551ba6-67f4-4125-8644-cfeb2ebfa80c)

