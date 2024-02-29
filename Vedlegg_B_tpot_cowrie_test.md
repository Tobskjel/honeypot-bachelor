# Test av Cowrie honeypot
I forbindelse med testing av Cowrie, en ssh honeypot implementert i T-Pot, har vi testet funksjonalitetene til denne.

## Spesifikasjoner
For å teste etablerte vi en Kali-maskin i samme VLAN. Under følger spesifikasjonene til denne maskinen:

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/eda16bf7-2115-4ada-b220-6ef295c024c7)

## SSH
Først gjorde vi en nmap scan
```bash
  nmap <your ip>
```
Deretter ser man at port 22 er åpen for ssh

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/a91caa04-c66c-4263-9470-d960ee29f3c3)

Så lagde vi en fil med en rekke brukernavn som vi ønsket å teste

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/7318ac8f-5f3e-4e92-a049-1fdabf96e9aa)

Etter dette ble gjort benyttet vi programmet "hydra" i kali for å teste ulike kombinasjoner av brukernavn og passord med den kjente rockyou.txt, en stor samling av mange kjente passord.

```bash
  hydra -L users.txt -P /usr/share/wordlists/rockyou.txt <your ip> ssh -t 40 -I -V -f
```
<img width="241" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/d21d6672-5095-4309-9ca1-e99d125a8e27">

```bash
  ssh root@<your ip>
```

Man skriver deretter inn passordet som ble funnet og logger inn. 

## Testing fra CLI
Da vi kom inn testet vi at vi kunne gjøre endringer i Cowrie.

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/b6c972bb-42df-4d1d-b013-f2f132e15c12)

Vi lagde en mappe "test", gikk inn på den og avsluttet koblingen. Da vi igjen koblet oss på Cowrie var ikke mappen der lenger:

![image](https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/44c79f67-c180-423d-8302-78a5f26229f4)

## Logger fra T-Pot
På dashbordet til T-Pot inni oversikten til Cowrie ble aktiviteten gjort i forrige steg logget

<img width="957" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/84c8139c-9e6b-40d4-8285-329b9fc2fcb8">

<img width="959" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/c9f4edd1-a612-4e57-98ad-f241ba715007">

<img width="959" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/4d81b68a-eaba-49d4-8a1a-df0077afdaa2">

<img width="950" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/f2ac339d-e695-4cc5-8cd0-17b2d49d8f0c">

<img width="959" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/cbddb6c9-ee41-4220-a2b0-acd1ab608159">

Flere andre honeypots reagerte på nmap skannen gjort tidligere i testingen:

<img width="959" alt="image" src="https://github.com/Tobskjel/honeypot-bachelor/assets/17578354/028cf75f-1220-48e0-a002-8a826fe738fa">
