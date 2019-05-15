# Konsolen Zeug

## Beispiel um auf installierte mysql zuzugreifen



auf der Konsole ausführen.

    vi ~/.ssh/config

## Anpassungen in der ssh config

Wir forwaren hier den Port 3306 um in unserem Fall um auf eine MYSQL Datenbank zugreifen zu können.

    Host projektName
    User userName
    HostName meineUrl.com oder IP-Adresse
    LocalForward 3306 meineUrl.com:3306
    #IdentityFile ~/.ssh/userName.pub
    #PreferredAuthentications publickey

Nun können wir auf der Konsole per ssh unser Projekt aufrufen.

    ssh projektName

Danach Passwort eingeben und wir sind auf der Machine mit gelinkter MYSQL Datenbank.

## Zugriff auf MYSQL Datenbank

Mit einem Client z.B. SQuirreL oder SequelPro einloggen

_Dran denken lokalhost wäre in dem Fall dann **127.0.0.1**!!!_