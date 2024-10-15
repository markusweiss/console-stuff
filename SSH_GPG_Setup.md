# SSH

## Key anlegen

     ssh-keygen -t rsa -b 4096 -C "<my.name@domain.com>"

Evtl. direkt im .ssh Ordner.

Alternativ, schneller, sicherer, aber derzeit nicht von allen Standards unterstützt.

     ssh-keygen -t ed25519

## Alle öffentlichen ssh Keys auflisten

     ls -la ~/.ssh/*.pub

## vorhandenen ssh key import    

Ordner im User Verzeichnis anlegen

     mkdir .ssh

     ~/.ssh/

Schlüssel reinkopieren

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

## Private Schlüssel in den SSH-Agenten laden

     ssh-add

## SSH-Agent Forwarding

     ssh -A <servename> bzw. ssh -A user@remote-server

## Auflistung der öffentlichen Schlüssel, die im SSH-Agent geladen sind. 

     ssh-add -L

##  Überprüfen, ob deine SSH-Konfiguration für GitHub richtig ist.

     ssh -T git@github.com


## Zugriff auf MySQL Datenbank

Mit einem Client z.B. SQuirreL oder SequelPro einloggen

_Dran denken lokalhost wäre in dem Fall dann **127.0.0.1**!!!_

# GPG
## Key installieren

todo

## GPG export/import

todo

## Key zu .zshrc config hinzufügen

     ~ ▓▒░ vi .zshrc

    export GPG_TTY=$(tty)
