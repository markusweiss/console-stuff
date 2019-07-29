# Konsolen Zeug

## GIT

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


## Git mit verschiedenden ssh Keys nutzen

Hier wurde der ssh config der Key **projektName** hinterlegt siehe Beispiel ssh weiter unten.

clone URL in Git:

git@gitlab.meinserver.com:**gitordner**/workshop/meinverzeichnis.git

     git clone projektName:gitordner/workshop/meinverzeichnis.git

Die Gitlab URL wird hier dann durch den angelegte ssh key in der config ersetzt. (**projektName** mit hinterlegtem ssh Key)

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