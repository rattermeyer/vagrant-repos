Vagrant-Repos
=============

Installiert eine VM mit

* Sonatype Nexus
* User git/password
* bare repository /home/git/demo.git
* default keys

IP: 192.168.33.10 (siehe Vagrantfile)

Setup
-----
vagrant up

Nexus
-----

Zugriff http://192.168.33.10:8081/nexus

Git
-----
Clonen mit Passwort
git clone ssh://192.168.33.10/home/git/demo.git

Clonen ohne Passwort (von Linux aus)
Erstellen der Datei ~/.ssh/config

Host repos 192.168.33.10
Hostname 192.168.33.10
IdentityFile ~/.ssh/repos_rsa

Kopieren des Private keys

cp keys/id_rsa ~/.ssh/repos_rsa

Dann ohne Passwort
git clone ...
