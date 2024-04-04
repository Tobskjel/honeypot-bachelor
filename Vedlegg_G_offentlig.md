# Test av T-Pot med offentlig IP

I forbindelse med testing av T-Pot fikk vi anskaffet en offentlig IP-adresse slik at den ble tilgjenglig på det åpne internett. Den forble åpen fra 15. Mars 2024 til 4. April 2024, en periode på 20 dager. Vi skal nå gå gjennom hva slags resultater dette har gitt oss

## Generelt

Over denne perioden har det vært en rekke aktivitet over ulike honeypots på T-Pot. Bildet viser oversikten over antall angrep på de 10 honeypots som var mest angrepet

<img width="803" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/7a518704-5948-4831-b6c0-5f30e8917339">

En bedre oversikt over alle de ulike typene og skalaen på hvor mye disse ble angrepet kan ses på neste bilde:

<img width="312" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/2d365d18-4759-4bdd-b4be-e64ea0947ef1">

Allikevel viser ikke denne oversikten hvor mange som angrep, men kun antallet angrep. Bildene under gir et bilde av at noen aktører har vært mer aktive enn andre:

<img width="308" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/c9c40cfd-095f-40ca-bf26-ecaf323d3d7d">

<img width="220" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/90e2fcb2-a50e-4458-b1f4-2249535e8391">

Under er et kart som gir en god oversikt over hvor mesteparten av aktiviteten har kommet fra.

<img width="598" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/339fa103-fb41-4fa7-9d12-ab1b82a9407c">

Videre kan man se mer spesifikt på hvilke ASN som er slått inn flest ganger, og hvilke IP adresser som har angrepet mest

<img width="394" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/021183c6-2454-4c23-8b8d-3e08ecc14bd6">

Søker man opp disse IP-adressene får man opp at disse tilhører datasentere fra ulike land. Mange av disse er markert som spam, og de er dermed ikke de mest relevante å se på. Videre kan man se på hva slags sårbarheter som ble mest utnyttet, og hvilke brukernavn og passord som ble benyttet.

<img width="520" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/d341479e-82d4-4c18-ad40-2daf1dc47daa">

<img width="953" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/8010711d-6349-4de6-9a6a-a6ed0cacc1ef">

I tillegg kan man se hva slags operativsystemer som aktørene har benyttet: 

<img width="230" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/cb5bff67-3fb7-4430-8823-8c09e34f88f2">

## Cowrie
En av honeypotene som ble truffet mest var Cowrie, en SSH-honeypot
