Title: Opzetten van een veilige LAMP-webserver
Date: 2017-11-19 18:00
Category: Web
Tags: web, websecurity, apache, php, mysql
Slug: opzetten-van-een-veilige-lamp-webserver
Authors: Sling
Summary: In deze tutorial gaan we een LAMP-setup bouwen die veilig genoeg is om aan het boze Internet te hangen en bekijken hoe we deze het beste kunnen onderhouden.

# Introductie

![Linux logo](images/lamp-linux.png)
![Apache logo](images/lamp-apache.png)
![MySQL logo](images/lamp-mysql.png)
![PHP logo](images/lamp-php.png)

De meeste lezers van deze tutorial zullen enige achtergrondkennis hebben over websites, en misschien zelfs wel wat weten over de hosting ervan. Voor mensen die niet beschikken over een eigen server, beperkt deze kennis zich helaas tot kant-en-klare hostingpakketten bij providers die maar weinig opties en knopjes aan jou als gebruiker beschikbaar stellen. Hierdoor kan er weinig fout gaan, maar je leert er ook erg weinig van en hebt niet veel flexibiliteit en vrijwel geen controle over de veiligheid van je website.

Om de beveiliging van websites en de servers waar ze op gehost worden te kunnen testen en verbeteren moeten we deze kennis uitbereiden. In deze tutorial gaan we het dus anders aanpakken en zelf een dedicated webserver inrichten, zonder deze te hoeven delen met andere gebruikers en met volledige controle voor onszelf.

Als basis voor onze server gebruiken we Linux, en wel een Ubuntu-installatie. Hiervan gaan we een complete web- en databaseserver maken en deze vervolgens voorzien van allerlei beveiligingsmaatregelen, om het systeem zo veilig mogelijk te maken. Ten slotte kijken we voor de volledigheid ook nog kort naar enkele tips over het sneller maken van je server en manieren om de server te onderhouden. Een paar complexe onderdelen zullen we overslaan en in latere tutorials behandelen, maar na het doorlopen van de tutorial heb je een veilige en goed uitgeruste webserver die je met een gerust hart aan het Internet kan hangen!

In deze tutorial wordt er van je verwacht dat je al enigszins comfortabel bent met het werken in een Linux terminal, en dat je basistaken zoals tekstbestanden bewerken en pakketten installeren en configureren onder de knie hebt. Denk je dat je hier nog een opfrisbeurt voor kan gebruiken? Bekijk dan eerst even de [Introductie tot Linux](introductie-tot-linux.html) tutorial!

Je ziet in de titel al het woord _LAMP_ staan, en dat is het type server wat we zullen gaan installeren. Maar waar staat die afkorting eigenlijk voor?
- **L**inux : Het besturingssysteem waar we mee gaan werken, in ons voorbeeld Ubuntu Server 14.04 LTS
- **A**pache : Het webserver pakket wat we gaan gebruiken, de Apache Webserver
- **M**ySQL : Het database management system (DBMS) wat we gaan gebruiken
- **P**HP : De scriptingtaal die we gaan gebruiken om dynamische content te serveren

Soms wordt overigens met de 'P' in 'LAMP' ook wel een andere scriptingtaal zoals Perl of Python bedoeld, maar we zullen de server in dit geval met PHP uitrusten.

**Let op:** Voordat we verder gaan is het belangrijk dat je een vers-geïnstalleerd Ubuntu Server 14.04 LTS systeem met internetverbinding en minimaal 512 MB intern geheugen bij de hand hebt.

Als je dit nu nog niet hebt, kun in daarvoor bestemde [tutorial](je-eigen-linux-systeem.html) zien hoe je zo'n systeem kan installeren op een virtuele machine in VirtualBox, bijvoorbeeld op de computer waar je nu eze tutorial op leest.

De installatie kan natuurlijk ook direct op een fysieke server, of in een VPS-omgeving bij een hostingprovider, dat maakt niet uit. Tijdens de installatie van Linux hoef je nog niets bijzonders te doen en kun je overal voor de opties kiezen zoals in de link hierboven te vinden is. Heb je vragen over de installatie van Linux, stel deze dan in het commentaar onderaan de ['Je eigen linux systeem' tutorial](je-eigen-linux-systeem.html).

Heb je al een Ubuntu server die je wil gaan inrichten als veilige LAMP server? Ga dan direct door naar 'Stap 1: Gebruikersaccounts' in het volgende hoofdstuk.

---

# Ubuntu

Zorg ervoor dat er een SSH daemon draait op de server (`apt-get install openssh-server`), dat je VM in NAT-modus staat en een IP heeft gekregen van je router. Na het via SSH inloggen met ons gebruikersaccount op het IP wat onze VM gekregen heeft, zijn we klaar om aan het werk te gaan! Stap voor stap gaan we nu de onderdelen van de webserver dichttimmeren, te beginnen bij het besturingssyteem: Ubuntu.

## Stap 1: Gebruikersaccounts

Wat we zojuist hebben gedaan is meteen iets wat we meteen zullen uitschakelen; namelijk het inloggen via SSH met een gebruikersnaam en wachtwoord. Wachtwoorden zijn namelijk een erg zwakke schakel in een goed beveiligde server en in plaats hiervan zullen we zogenaamde SSH 'sleutels' gaan gebruiken die bestaan uit minimaal 2048 bits aan willekeurige informatie. Dit kun je ook zien als een heel lang wachtwoord maar zo'n sleutel kan natuurlijk niemand uit zijn hoofd leren dus het zie het als een bestand wat iemand bij zich moet hebben om in te kunnen loggen.

Hoe het inloggen met zo'n sleutel werkt is gebaseerd op public key cryptografie, iets waar we in deze tutorial niet verder op in zullen gaan, we zullen het hier alleen vanuit praktisch oogpunt bekijken. We zullen een _publieke sleutel_ genereren die we op de server plaatsen, en een _privésleutel_ genereren die we zorgvuldig voor onszelf bewaren. Samen heten deze twee sleutels een sleutelpaar. Om te voorkomen dat iemand die je privésleutel steelt hier direct mee kan inloggen, zullen we ook deze sleutel nog versleutelen met een eigen wachtwoord.

Als je Windows gebruikt om in te loggen op je server dan zul je van andere tools gebruik moeten maken om SSH keys te genereren, dan wanneer je de ingebouwde terminal van Linux of OS X gebruikt. Kies een van de onderstaande blokken die bij jouw situatie past:

### Windows: Putty, Puttygen, Pageant

> Het genereren van een sleutelpaar kan voor Putty met [puttygen](http://the.earth.li/~sgtatham/putty/latest/x86/puttygen.exe). Klik na het openen van puttygen op 'Generate', beweeg wat met je muis voor [entropie](http://nl.wikipedia.org/wiki/Entropie_(informatietheorie)) en vul een _passphrase_ in om onze sleutel te beschermen met een soort wachtwoord. Zet in het veld 'Key comment' je eigen naam en de maand plus het jaartal, dit is handig voor als je ooit een nieuwe sleutel genereert en ze daarna niet door elkaar haalt.
> Kopieer en plak nu het stuk code bovenin het venster in een notepad-venster (of een andere plaintext tekstverwerker), dit is je publieke sleutel en deze hebben we straks nodig. Let op dat je alle regels meeneemt, je zal wat moeten scrollen! Ook moeten we de privésleutel opslaan, klik hiervoor op 'Save private key' en kies een veilige lokatie. Mijn advies is om hier meteen een backup van te maken op een USB-stick, zodat je nog bij je server kan komen als je het bestandje ineens kwijt bent!
> Vervolgens hebben we bij Putty nog het programma [pageant](http://the.earth.li/~sgtatham/putty/latest/x86/pageant.exe) nodig om deze sleutel op de achtergrond te kunnen laden, zodat Putty er gebruik van kan maken. Na het starten van dit programma gebeurt er niets, maar er zal nu rechtsonderin wel een icoontje in de vorm van een computerscherm met een hoedje zijn verschenen. Klik met de rechtermuisknop op dit icoontje en kies 'Add key'. Navigeer naar je privésleutel en voer je passphrase in. Hierna is je sleutel geladen en kan Putty hier automatisch gebruik van maken. Als je kiest voor 'View keys' kun je zien welke keys geladen zijn en deze eventueel ook weer verwijderen uit het geheugen van pageant. Let op dat je je sleutels alleen moet laden op een persoonlijk account en op een computer die je vertrouwt, dus niet op een gedeelde computer!

### Linux en OS X: Terminal

> (TODO)

De laatste stap voordat we kunnen inloggen met onze privésleutel is het installeren van de publieke sleutel op de server. Hiervoor moeten we een mapje en een bestand aanmaken: (Deze stappen voeren we niet als <code>root</code> uit, maar als normale gebruiker!)

```bash
# Maak de map .ssh aan in onze homedirectory, met de juiste rechten: 
mkdir ~/.ssh
chmod 700 ~/.ssh

# Maak in deze map een bestand authorized_keys aan, met de juiste rechten:
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys

# Bewerk dit bestand:
nano ~/.ssh/authorized_keys
```

Kopieer en plak nu de publieke sleutel die je in een apart venster had gezet in nano, controleer of het bestand nu begint met `ssh-rsa` en eindigt met het commentaar wat je bij in puttygen had ingevuld, en sla het bestand op door op Ctrl+X te drukken en `Y` te kiezen.

Gebruik je geen Putty maar de ingebouwde terminal van Linux of OS X, dan kun je voor het genereren van een sleutel het volgende commando gebruiken: 

```bash
todo
```

Behalve via SSH kun je op een Linux systeem ook via de lokale console inloggen, dat willen we nog wel kunnen doen met wachtwoorden, bijvoorbeeld wanneer er iets met de netwerkverbinding aan de hand is. Hieraan stellen we wel strenge eisen zodat dit risico flink beperkt blijft.

Om deze eisen (policies) in te kunnen stellen hebben we een extra package nodig: `apt-get install libpam-cracklib`

```
Install package `libpam-cracklib` so we can perform weak password checks when users set their passwords. Policies for these checks: allow up to 3 prompts before error, minimum password length is 12 chars, subsequent passwords should differ at least 3 chars from each other, passwords should contain at least 1 uppercase character and a 'other' character. As for the policies, I would prefer umask to be set to 077 to prevent accidental loose permissions, and have a password policy that will make sure our passwords are not older han 3 months. Also set 'DEFAULT_HOME no' so problems with a home-dir will just cause an error instead of logging a user in to '/'. /etc/login.defs UMASK 077 PASS_MAX_DAYS 93 PASS_WARN_AGE 7 DEFAULT_HOME no SHA_CRYPT_MIN_ROUNDS 5000 SHA_CRYPT_MAX_ROUNDS 10000 /etc/bash.bashrc umask 077 /etc/profile umask 077 /etc/pam.d/common-session password required pam_cracklib.so retry=3 minlen=12 difok=3 ucredit=-1 ocredit=-1 password [success=1 default=ignore] pam_unix.so obscure use_authtok try_first_pass sha512 remember=12 password requisite pam_deny.so password required pam_permit.so Modify pam_umask in /etc/pam.d/common-session: session optional pam_umask.so umask=027 Don't use passwords when sudo'ing, users shouldn't use passwords at all /etc/sudoers %sudo ALL=NOPASSWD: ALL
```

## Stap 2: SSH Configuratie

- SSH met keys only, misschien ook two-factor auth?, 
- geen ssh-login als root 
- Allow sshd logins from everywhere, any other type of login can only be done locally. 
- /etc/hosts.allow sshd : ALL : ALLOW ALL: LOCAL, 127.0.0.1 
- /etc/hosts.deny ALL: PARANOID 
- For all accounts that need SSH logins there should be an additional group added (groupadd sshusers). 
- lower LoginGraceTime since 120 is quite long.
- Root login should not be allowed trough SSH. 
- Also X11Forwarding is disabled. 
- MaxStartups settings a bit more strict. 

Aanbevolen "/etc/ssh/sshd_config": 
```Port 22 ListenAddress Protocol 2 AllowGroups sshusers HostKey /etc/ssh/ssh_host_rsa_key HostKey /etc/ssh/ssh_host_dsa_key HostKey /etc/ssh/ssh_host_ecdsa_key HostKey /etc/ssh/ssh_host_ed25519_key UsePrivilegeSeparation yes KeyRegenerationInterval 3600 ServerKeyBits 1024 SyslogFacility AUTH LogLevel INFO LoginGraceTime 20 PermitRootLogin no StrictModes yes RSAAuthentication yes PubkeyAuthentication yes AuthorizedKeysFile %h/.ssh/authorized_keys IgnoreRhosts yes RhostsRSAAuthentication no HostbasedAuthentication no PermitEmptyPasswords no ChallengeResponseAuthentication no PasswordAuthentication no X11Forwarding no X11DisplayOffset 10 PrintMotd no PrintLastLog yes TCPKeepAlive yes ClientAliveInterval 300 ClientAliveCountMax 0 MaxStartups 3:50:10 AcceptEnv LANG LC_* Subsystem sftp /usr/lib/openssh/sftp-server UsePAM yes```


## Stap 3: Bestandssysteem en Encryptie

- Filesystem security, ACL 
- disk encryption 
- /tmp en /var/tmp hardenen (in /etc/fstab "UUID= /tmp ext4 noatime,nodiratime,nodev,nosuid,noexec 0 2", en /var/tmp moet een symlink zijn naar /tmp zodat het geen andere flags kan hebben) 
- per-user temporary directories, apt-get install libpam-tmpdir, in /etc/pam.d/common-session toevoegen "session optional pam_tmpdir.so"

## Stap 4: Logbestanden

- Syslog+Audit logging naar remote host

## Stap 5: Netwerk

- Iptables, zowel voor ipv4 als ipv6, iptables-persistent - Fail2ban - tcpwrappers

## Stap 6: Antivirus

- antivirus (clamav)

## Stap 7: Updates
- Automatische security updates (unattended-upgrades)

## Stap 8: Overige tips &amp; tricks
- Onnodige services uitschakelen 
- By default, executables with the setuid bit could make coredumps which are readable by regular users. If the program is dumped while it had privileged information in memory, and the user can read the dump, they might find out that privileged information. Luckily this can be disabled: /etc/sysctl.conf fs.suid_dumpable = 0

---

# Apache

- http://httpd.apache.org/docs/current/misc/security_tips.html 
- http://wiki.apache.org/httpd/FileSystemPermissions 
- mod_security, mod_evasive 
- modules uitzetten die niet nodig zijn 
- htaccess uitzetten 
- logging naar syslog 
- SSL configuratie, https://www.ssllabs.com/ssltest/ 
`SSLCipherSuite EECDH+ECDSA+AESGCM:EECDH+aRSA+AESGCM:EECDH+ECDSA+SHA384:EECDH+ECDSA+SHA256:EECDH+aRSA+SHA384:EECDH+aRSA+SHA256:EECDH+aRSA+RC4:EECDH:EDH+aRSA:RC4:!aNULL:!eNULL:!LOW:!3DES:!MD5:!EXP:!PSK:!SRP:!DSS:!SRP:!DH:!MD5:aRSA+AES+TLSv1.2:aRSA+RC4:+RC4:RC4`
- SHA256 cert, ook in chain 
- ServerSignature Off 
- ServerTokens Prod 
- Options -Indexes -FollowSymLinks -Includes -ExecCGI
- LimitRequestBody 512000
- LimitRequestFields 100 
- LimitRequestFieldSize 8190 (default) 
- TimeOut 30 
- KeepAliveTimeout 5 
- RequestReadTimeout (mod_reqtimeout)

---

# MySQL

- http://www.greensql.com/content/mysql-security-best-practices-hardening-mysql-tips 
- http://etechnologytips.com/hardening-mysql-security-server/ 
- https://www.youtube.com/watch?v=uEBQ9l5MXtI

---

# PHP

- http://www.reecefowell.com/2012/10/01/hardening-php-through-php-ini-configuration-file/ 
- http://www.madirish.net/?article=229 
- http://phpsec.org/projects/phpsecinfo/index.html

---

# Performance

php5-fpm + mod_proxy_fcgi + apache event mpm (+tuning) mysqltuner

---

# Monitoring

todo

---

# Vervolgonderwerpen

De volgende onderwerpen hebben ook veel te maken met de beveiliging van een server zoals we deze hebben beschreven in deze tutorial, maar zijn iets te uitgebreid om in deze eerste tutorial in detail uit te leggen. Misschien dat er later aparte tutorials over volgen!

- Rootkitdetectie met bijvoorbeeld `chkrootkit` of `rkhunter`
- Intrusion Detection en Prevention, bijvoorbeeld met `tripwire`
- Geavanceerde security controls met SELinux of Apparmor
- Bastille Linux, hardening profielen
- Mailserverbeveiliging
- Fysieke Security van je server
- De gegevens op je server backuppen

Wil je dus na het lezen van deze tutorial nog meer weten over de beveiliging van je server, zoek dan op het Internet eens naar de bovenstaande termen!