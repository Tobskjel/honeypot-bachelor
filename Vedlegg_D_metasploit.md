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

### Resultater
Skannen kjørte gjennom alle portene, og mange av de ga ingenting. Allikevel fikk skannen noen resultater.

På 9 porter klarte den ikke identifisere hvilke tjenester som kjørte. Portene var som følger:
23
110
143
445
465
993
995
1024
1026

|23|test|   |   |   |
|---|---|---|---|---|
|23|   |   |   |   |
|   |   |   |   |   |
|   |   |   |   |   |

Den klarte å identifisere port 1443 til å være tilknyttet en honeypot:

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/60b4c36f-70ca-4d52-ae49-5addabafc98d)



