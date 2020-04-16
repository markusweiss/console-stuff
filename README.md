# Konsolen Zeug

## NodeJS

Einfachen lokalen Http Server starten: im entsprechenden Order folgendes aufrufen:

     npx http-server .

Link zum Server: [http-server: a command-line http server](https://www.npmjs.com/package/http-server)

## wget

Komplette Seite mit wget ziehen und im Ordner abspeichern.

wget für OSX kann mit [brew](https://brew.sh/) installiert werden.

Die umfangreiche **wget** [Dokumentation](https://www.gnu.org/software/wget/manual/wget.html) :scream: 

     wget --page-requisites --adjust-extension --convert-links <https://www.url-to-grab.de>

## GIT

### Branches

Nach Änderungen im aktuellen branch schauen

     git status

Alle Branches holen

     git fetch -a

Alle Branches anzeigen

     git branch -a

Gewünschten Branch anlegen z.B. feature/meinfeatureordner

     git checkout -b feature/meinfeatureordner

Zum master wechseln

     git checkout master

oder zurück

     git checkout feature/meinfeatureordner

### Branch umbenennen

lokaler Branch der noch nicht gepusht wurde

     git checkout <alter-name>

     git branch -m <neuer-name>

wenn der Branch schon gepush wurde dann zusätzlich

     git push origin -u <neuer-name>

     git push origin --delete <alter-name>


## Git master in feature mergen

den master Branch aktualisieren

     git pull

wechsel auf den feature Branch

     git checkout feature/meinfeatureordner

sicherheitshalber aktualisieren und danach master in feature mergen und pushen

     git pull
    
     git merge master
    
     git push

## Commit ohne vorherigen Push rückgängig machen

     git reset HEAD^ --hard

## Git mit verschiedenden ssh Keys nutzen

Hier wurde der ssh config der Key **projektName** hinterlegt siehe Beispiel ssh weiter unten.

clone URL in Git:

git@gitlab.meinserver.com:**gitordner**/workshop/meinverzeichnis.git

     git clone projektName:gitordner/workshop/meinverzeichnis.git

Die Gitlab URL wird hier dann durch den angelegte ssh key in der config ersetzt. (**projektName** mit hinterlegtem ssh Key)

## vorhandenen Ordner zu git hinzufügen

in den Ordner gehen und Dateien huínzufügen

     cd mein-projekt-ordner
     git init
     git add .

Kommentar nicht vergessen

     git commit

dann bei github ein neues Repository anlegen, da stehen dann schon die richtigen Befehle, wie z.B.:

     git remote add origin git@github.com:meinusername/mein-projekt-ordner.git

     git push -u origin master


## SSH

## Alle öffentlichen ssh Keys auflisten

     ls -la ~/.ssh/*.pub

## Beispiel um auf installierte MySQL zuzugreifen



auf der Konsole ausführen.

    vi ~/.ssh/config

## Anpassungen in der ssh config

Wir forwaren hier den Port 3306 um in unserem Fall um auf eine MySQL Datenbank zugreifen zu können.
<pre>
Host <b>projektName</b>
User <b>userName</b>
HostName <b>meineUrl.com oder IP-Adresse</b>
LocalForward <b>3306 meineUrl.com:3306</b>
IdentityFile /Users/<b>userName</b>/.ssh/<b>keyName</b>
</pre>
Nun können wir auf der Konsole per ssh unser Projekt aufrufen.

    ssh projektName

Danach Passwort eingeben und wir sind auf der Maschine mit gelinkter MySQL Datenbank.

## Zugriff auf MySQL Datenbank

Mit einem Client z.B. SQuirreL oder SequelPro einloggen

_Dran denken lokalhost wäre in dem Fall dann **127.0.0.1**!!!_