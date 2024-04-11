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

## Resultater
Skannen kjørte gjennom alle portene, og mange av de ga ingenting. Allikevel fikk skannen noen resultater.

På 9 porter klarte den ikke identifisere hvilke tjenester som kjørte. Portene var som følger:

|Porter|Tilknyttet tjeneste|
|---|---|
|23|Cowrie, Heralding, qHoneypots|
|110|Heralding, qHoneypots|
|143|Heralding, qHoneypots|
|445|Dionaea, qHoneypots|
|465|Ingen|
|993|Heralding|
|995|Heralding|
|1024|Ingen|
|1026|Ingen|
|1027|Ingen|

Den klarte å identifisere port 1443 til å være tilknyttet en honeypot:

<img width="315" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/f40000c3-2ede-44ed-853b-d8c3cead04c4">

Selve skannen ga også mye aktivitet. Her er alle treffene i tidsperioden denne skannen kjørte:

<img width="958" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/d9ae2fd6-23fa-4522-8a7e-8fe7bf087c11">

Selv om skannen viste aktivitet betyr ikke det nødvendigvis at noe ble avslørt. Ser man mer i detaljene på loggene ser man at det blant annet er blitt forsøkt utnyttet noen sårbarheter:

<img width="198" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/6a53db96-d46b-47f8-8ec1-faa8ff03eaad">

Man får også en del varsler på ulike IDer fra Suricata:

<img width="322" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/e53b7c84-8a4f-46d4-9da5-adeac31c1728">

På port 80 fikk man dette treffet:

<img width="311" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/b994aaca-4eac-4a39-ac33-ed0cc6600690">

På port 80 ligger Snare (Tanner), så den ene nettsiden denne kan utgi seg som er en wordpress bloggside. En trusselaktør vet nok fra før at Wordpress kan ha en del sårbarheter, og vil vurdere å utnytte disse. 
