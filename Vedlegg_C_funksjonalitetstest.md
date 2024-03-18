# Funksjonalitetstest av T-Pot
Ut ifra kravene definert i kapittel 4.2.1 vil vi gjennomføre en funksjonalitetstest for å bekrefte at kravene er på plass

Generelt alt av logger for de ulike typene honeypots finnes i ``/data``. Her vil vi gå gjennom hvordan disse kan representeres ved hjelp av Kibana.

## JA3 hash
Her er det ingen ferdiglagd oversikt, så man må dermed lage det selv. Det gjøres som følger:

- Lag et nytt dashboard ved å klikke på ``+ Create Dashboard``

<img width="955" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/cc957572-7bf9-4ce5-a6a6-f68833c583ad">

- Deretter ``Create visualization``

<img width="958" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/00b0d596-2d59-4d73-9c2b-c72990384c76">

- Søk deretter opp ``tls.ja3.hash.keyword`` og dra resultatet der det står du skal gjøre det

<img width="958" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/2fd579fb-bdcd-4f6a-9d16-74f529b81f63">

Da får man opp en oversikt over hvilke som er brukt over en viss tidsperiode. Det er en veldig mange forskjellige hasher, og alle får dermed ikke plass i en graf.
Under er et eksempel på hvordan en slik oversikt ser ut

<img width="541" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/27a4aeaa-4f28-4eed-9a29-3454332b857f">

## Login: brukernavn og passord
På den generelle oversikten over alle typene honeypots som eksisterer finner man en rekke informasjon, blant annet om hviolke brukernavn og passord som er forsøkt brukt.
Slik ser denne oversikten ut:

<img width="956" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/ed9a513d-b8be-4da6-a1a7-20b3f7268e7b">

Her 
