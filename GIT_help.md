## GIT

### Branches

Nach Änderungen im aktuellen branch schauen

     git status

Alle Branches holen

     git fetch -a

Alle Branches anzeigen

     git branch -a

Branch (feature) löschen

     git branch -d feature/meinfeatureordner

Branches bereinigen (prunen), z.B. unereichbare Branches oder gelöschte Ordner werden nicht mehr angezeigt.

     git fetch -p

Gewünschten Branch anlegen z.B. feature/meinfeatureordner

     git checkout -b feature/meinfeatureordner

Zum master wechseln

     git checkout master

oder zurück

     git checkout feature/meinfeatureordner

### Letzte git commit Nachricht umbenennen

`git commit --amend -m "Meine neue commit Nachricht"`

Danach brauchen wir den aktuellen Respository und Branch Namen.

Falls der Repository Name aus irgendeinem Grund nicht bekannt sein sollte:

`git remote show origin`

Ganz oben steht der Pfad/URL, jetzt können wir pushen.

`git push --force <mein-repository-name> <mein-branch-name>`

**ACHTUNG `--force` nur nutzen wenn Ihr Euch sicher seid das kein anderer dran arbeitet oder ein clone gemacht hat!!!**

### Branch umbenennen

lokaler Branch der noch nicht gepusht wurde

     git checkout <alter-name>

     git branch -m <neuer-name>

wenn der Branch schon gepush wurde dann zusätzlich

     git push origin -u <neuer-name>

     git push origin --delete <alter-name>

### Ordner umbenennen z.B. Groß/Kleinschreibung

Wird mit normalen Einstellungen nicht erkannt wenn der Ordern von Name in name geändert wurde

     git mv <Meinname> tmp
     git mv tmp <meinname>

     git commit -m "rename folder"
     git push

## Git master in feature mergen

den master Branch aktualisieren

     git pull

wechsel auf den feature Branch

     git checkout feature/meinfeatureordner

sicherheitshalber aktualisieren und danach master in feature mergen und pushen

     git pull

     git merge master

     git push

## Tags setzen

Wir wollen ein Tag setzen um zu deployen oder einen Stand markieren, damit wir zu dieser Version zurückkommen, ohne Branch

    git tag -a <basic-version> -m "Alle Einstellungen für Basisprojekt"

    git push origin --tags

## Commit ohne vorherigen Push rückgängig machen

     git reset HEAD^ --hard

## Git mit verschiedenden ssh Keys nutzen

Hier wurde der ssh config der Key **projektName** hinterlegt siehe Beispiel ssh weiter unten.

clone URL in Git:

git@gitlab.meinserver.com:**gitordner**/workshop/meinverzeichnis.git

     git clone projektName:gitordner/workshop/meinverzeichnis.git

Die Gitlab URL wird hier dann durch den angelegte ssh key in der config ersetzt. (**projektName** mit hinterlegtem ssh Key)

## vorhandenen Ordner zu git hinzufügen

in den Ordner gehen und Dateien hinzufügen

     cd mein-projekt-ordner
     git init
     git add .

Kommentar nicht vergessen

     git commit

dann bei github ein neues Repository anlegen, da stehen dann schon die richtigen Befehle, wie z.B.:

     git remote add origin git@github.com:meinusername/mein-projekt-ordner.git

     git push -u origin master

## Alias für übersichtliche View anlegen

Ein Alias kann genutzt werden um Kommados zusammenzufassen z.B mit einem Wort das Ihr Euch besser merken könnt.

     git config --global alias.graph "log --graph --branches --remotes --decorate --oneline"

Nach _alias._ könnt Ihr Euren sprechenden Namen nehmen

     alias.graph oder alias.eigenername

Schöne Übersicht aufrufen mit:

     git graph oder git eigenername

## git remote

Remotes auflisten

     git remote

Remotes mit URLs auflisten

     git remote -v

Einen neuen Remote hinzufügen

     git remote add <bezeichnung> <url>

z.B.

     git remote add testserver https://gitlab.meintestserver/testprojekt/testapp.git

## Verschiedene git Accounts nutzen

Grundsätzlich mit einem Account kann dieser immer global angelegt werden.

     git config --global user.name "<Vorname Nachname>"
     git config --global user.email "<email_für_git>"

Wollen wir z.B. für eine Kundenprojekt oder ein zweites privates Projekt einen anderen
ssh key und eine andere e-mail verwenden müssen wir dies im Projekt anlegen.

D.h. nach dem der neue Key (siehe unten) mit der email Adresse angelegt wurde gehen wir in:

     cd <mein-neuer-projektordner>

     git config user.name "Name im Projekt"
     git config user.email "projekt_email@example.com"

     ssh-add ~/.ssh/privater_Projekt_Schlüssel 

     git remote set-url origin git@github.com:Benutzername/Projektname.git

Um zu sehen was im Projekt-Order konfiguriert ist kann amn dies sich z.B. so anschauen:

     cat .git/config

## Verified commits

Hierzu braucht man z.B. einen GPG Key.
Installation siehe SSH_GPG_Setup.md

Folgende Einstellung kann auch nur in einem entsprechenden Projekt gesetzt werden.

     git config commit.gpgsign true
     cat .git/config -> prüfen

bei Bedarf kann es auch ausgeschaltet werden

      git config commit.gpgsign false
