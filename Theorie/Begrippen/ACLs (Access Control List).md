**Access Control List:**
Is een lijst van regels die bepaalde trafiek toelaat en blokkeert.
Er is een SRC en een DST IP.

**Normale ACLs:**
- IP van waar + subnetmask
- Permit of deny
- Laag 3

**Extended ACLs:**
- IP van waar + subnetmask
- IP naar waar + subnetmask
- Poort meegeven
- Extra specifieke regels
- Laag 3 & 4

Een statement in een ACL heet een ACE
- Access Control Entry

De volgorde van de ACL list is belangrijk.
De eerste regel die matcht wordt gebruikt.

Voordelen ACLs:
- Performantie
- Veiligheid

ACLs worden aan een interface gehangen.
Interface --> een fysieke poort.
Richting van de ACL is belangrijk.

Matches --> is de hoeveelheid dat de regel is aangesproken geweest.