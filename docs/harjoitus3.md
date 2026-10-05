
# Harjoitus 3 – Git-muutosten peruuttaminen

## 1. Muutosten tekeminen

Tein repositorioon useita muutoksia:

* Muutin tiedostoa `index.html`
* Muutin tiedostoa `about.txt`
* Lisäsin uuden tiedoston `uusi1.txt`
* Lisäsin uuden tiedoston `uusi2.txt`

### Komennot

```bash
vim index.html
vim about.txt
touch uusi1.txt
touch uusi2.txt
```

### `git status`

```text
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   about.txt
	modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	uusi1.txt
	uusi2.txt

no changes added to commit (use "git add" and/or "git commit -a")

```

---

## 2. `add`-toiminnon peruuttaminen

### Lisäsin muutokset seuraavaan talletukseen

```bash
git add .
```

### `git status`

```text
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   about.txt
	modified:   index.html
	new file:   uusi1.txt
	new file:   uusi2.txt

```

### Poistin yhden muutoksen seuraavasta talletuksesta

```bash
git reset index.html

```

`index.html` poistuu staging-tilasta.

### `git status`

```text
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   about.txt
	new file:   uusi1.txt
	new file:   uusi2.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   index.html


```

### Poistin kaikki loput muutokset seuraavasta talletuksesta

```bash
git reset
```

Kaikki muutokset poistuvat staging-tilasta.

### `git status`

```text
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   about.txt
	modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	uusi1.txt
	uusi2.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Työtilassa on useita tallentumattomia muutoksia, mitkä ei ole menossa seuraavaan commit-tallennukseen.

---

## 3. Työtilaan tehtyjen muutosten peruuttaminen

### Peruuttaminen yhdestä talletetusta tiedostosta

```bash
git restore index.html
```

`index.html` palautuu muutosta edeltävään tilaan. Lisäksi se ei enää näy tallentumattomissa muutoksissa.

### `git status`

```text
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   about.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	uusi1.txt
	uusi2.txt

no changes added to commit (use "git add" and/or "git commit -a")

```

### Poistin kaikki loput muutokset työtilasta

```bash
git restore .
```

### `git status`

```text
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	uusi1.txt
	uusi2.txt

nothing added to commit but untracked files present (use "git add" to track)

```

### Mitä tapahtui uusille `untracked`-tilassa oleville tiedostoille?

Kun käytti `git restore .` komentoa niin loput tracked-tilassa olevat tiedostot palasivat edellistä committia edeltävään tilaan, mutta `untracked` tiedostot `uusi1.txt` ja `uusi2.txt` eivät muuttuneet.

---

## 4. Talletuksen peruuttaminen

### Tein useita muutoksia

```bash
vim index.html
vim about.txt
```

### `git status`

```text
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   about.txt
	modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	uusi1.txt
	uusi2.txt

no changes added to commit (use "git add" and/or "git commit -a")

```

### Lisäsin muutokset seuraavaan talletukseen

```bash
git add .
```

### Talletin muutokset

```bash
git commit
```

### `git status`

```text
On branch master
nothing to commit, working tree clean

```

---

## 5. Talletuksen peruuttaminen `revert`-komennolla

### Tarkistin historian ennen peruuttamista

```bash
git log
```

```text
commit face3ab2a065817c91a5ce6586a9fff35d4f7be8
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 19:40:01 2026 +0300

    Muokkasin index.html ja about.txt tiedostoja.
    Lisäsin uusi1.txt ja uusi2.txt tiedostot.

commit d2dc0a6019aa8e3b997bc3ec3e3294f167b62080
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 17:14:51 2026 +0300

    README.md, about.txt ja info.html tiedostojen lisääminen versionhallintaan

commit 1a1bc87846a30d923c22060e7d81eb478a1467ff
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 17:06:51 2026 +0300

    text.txt tiedoston poistaminen

commit f3d1afb92490cd4600d22de6e8edba6d5c46985d
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 17:01:01 2026 +0300

    hello.html tiedoston muuttaminen index.html tiedostoksi

commit b426870e9a5913a6dbeb1210e742d2287aed4d7d
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 16:52:15 2026 +0300

    hello.html-tiedoston muuttaminen html-muotoon

commit 1c2779ed64860ac616d39b164ca56b60663dd896
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 16:14:41 2026 +0300

    hello.html-tiedoston luominen

commit 468dd4ef8e17bbb034cf140e1e1d7730fef4f07e
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 16:05:41 2026 +0300

    text.txt tiedoston luominen ja tallettaminen

```

### Peruutin viimeisimmän talletuksen

```bash
git revert face3ab2
```

Tuloste:

```text
[master 8ca16dc] Revert "Muokkasin index.html ja about.txt tiedostoja."
 4 files changed, 2 insertions(+), 6 deletions(-)
 delete mode 100644 uusi1.txt
 delete mode 100644 uusi2.txt

```

### `git status`

```text
On branch master
nothing to commit, working tree clean

```

### Tarkistin historian peruuttamisen jälkeen

```bash
git log --oneline
```

```text
8ca16dc Revert "Muokkasin index.html ja about.txt tiedostoja."
face3ab Muokkasin index.html ja about.txt tiedostoja. Lisäsin uusi1.txt ja uusi2.txt tiedostot.
d2dc0a6 README.md, about.txt ja info.html tiedostojen lisääminen versionhallintaan
1a1bc87 text.txt tiedoston poistaminen
f3d1afb hello.html tiedoston muuttaminen index.html tiedostoksi
b426870 hello.html-tiedoston muuttaminen html-muotoon
1c2779e hello.html-tiedoston luominen
468dd4e text.txt tiedoston luominen ja tallettaminen

```

### Mitä `git log` näyttää?

`git log` näyttää, että alkuperäinen commit ja siinä tehdyt muutokset ovat edelleen mukana commit-historiassa. `git revert` ei poista aikaisempaa committia, vaan luo uuden revert-commitin, joka kumoaa kyseisessä commitissa tehdyt muutokset. Näin alkuperäinen commit säilyy historiassa, mutta sen vaikutukset on peruttu.

---

## 6. Tunnisteen lisääminen

Lisäsin viimeisimpään talletukseen tunnisteen:

```bash
git tag harjoitus3
```

---

## 7. Yhteenveto käytetyistä Git-komennoista


| Git-komento | Selite |
| --- | --- |
| git status | Näytä versionhallinnan työtilan muutokset |
| git add | Lisää tiedosto versionhallintaan |
| git reset | Peruuta lisäys versionhallinnan tallennuksesta |
| git restore | Palauta tiedosto aikaisempaan versionhallinnassa olevaan versioon |
| git commit | Tallenna muutokset versionhallintaan |
| git log | Näytä versionhallinnan commit-historia |
| git revert | Peruuta parametrina annetun versionhallinnan talletus kokonaan, tekemällä ns. "anti-talletus committin" |
| git tag | Lisää versionhallinnan commit-historiaan tunniste |

