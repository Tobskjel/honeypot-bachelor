# Checkpot test på T-Pot
Her var hensikten å kjøre programmet checkpot.py for å se om den kunne oppdage noen av honeypot-instansene som T-Pot leverer

## Installering av checkpot
Under denne prosessen benyttet vi oss av denne lenken: https://github.com/honeynet/checkpot
På vår Kali-klient fulgte vi stegene gitt i lenken over.
Da lastet vi ned dette repoet med følgende kommando

```bash
git clone https://www.github.com/honeynet/checkpot.git
```
Deretter må man sjeke av man har følgende installert:
- python3 og pip (pip3)
- nmap
- mercurial (evt pip-install python-nmap)

Etter å ha sjekket dette går man i mappen med innholdet som ble installert i forrige steg og skriver følgende
```bash
pip install -r requirements.txt
```

Når dette er gjort kan man begynne testing

## Testing
For testingen sørget vi for å være på samme nett som T-Pot og kunne nå IP-adressen til denne. Da kan man benytte følgende kommando
```bash
python checkpot.py -t <IP> -l 3
```
Her betyr "-l 3" hvor grundig skanningen gjøres fra 1-3 der 3 er det høyeste

Ved spørsmål "Do you agree to these terms", skriv "i agree"

## Resultater
Fra skannen klarer T-Pot å fange opp følgende aktivitet:

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/829fbcae-ff08-4631-8ef0-6725df858cb4)

I tillegg kommer checkpot med oversikt over hva den selv har funnet. Dette var resultatene fra vår test:

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/ddcc90b9-b5f6-4ef9-a305-2bbc7e02e6a5)

Her ser man at Checkpot i tillegg kommer med lenker til deres nettside, der de kommer med anbefalinger på hva slags handlinger man kan gjøre for å kunne unngå å bli oppdaget.

# Metasploit
Vi benyttet Metasploit, et datasikkerhetsprosjekt som gir informasjon om sikkerhetssårbarheter og hjelper til med penetrasjonstesting og utvikling av IDS-signaturer.
Hensikten var å se hva slags resultater dette programmet ga oss, og om den klarer å oppdage noen honeypots

## msfconsole
For å benytte Metasploit må man gjøre følgende:
```bash
systemctl start postgresql
sudo msfdb init
msfconsole
```
Da er man inne i Metasploitkonsollen

## Nmap skann
Når man er inne i Metasploitkonsollen skriver man inn følgende kommando

```bash
db_nmap -sV -sC -p- <ip-adresse>
```
db_nmap: Dette er en Metasploitkommando som lar deg bruke Nmap-skanninger. Den lagrer resultatene i Metasploit sin database for å analyse resultatene.

-sV: Denne ber Nmap gjøre en tjenesteskanning, altså at den vil forsøke å identifisere hvilke tjenester som kjører på målmaskinen, og hvilke programvare og versjoner som brukes.

-sC: Denne ber Nmap gjøre en skriptskanning, altså at Nmap vil bruke vanlige skript for å utføre ulike typer tester og samle inn mer informasjon om tjenestene som kjører på målmaskinen.

-p-: Denne ber Nmap skanne alle porter på målmaskinen, altså fra 1 til 65535. Normalt vil Nmap bare skanne de vanlige portene hvis det ikke blir spesifisert noe annet.

Denne testen startet vi 11. Mars 08:43 CET, den tok 139004 sekunder, i underkant av 2 døgn.
