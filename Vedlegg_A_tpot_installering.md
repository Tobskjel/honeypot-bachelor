# T-Pot installering

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

