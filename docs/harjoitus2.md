# Harjoitus 2 – Gitin perustoiminnot

## 1. Git-repositorion perustaminen

### Harjoitushakemiston luominen

```bash
mkdir git-harjoittelua
```

### Siirtyminen hakemistoon

```bash
cd git-harjoittelua
```

### Git-repositorion alustaminen

```bash
git init
```

### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)

```

---

## 2. `test.txt`-tiedoston luominen ja tallettaminen

### Tiedoston luominen

```bash
touch test.txt
```

### Sisällön lisääminen tiedostoon

```bash
vim test.txt
```

Tiedoston sisältö:

```text
Git-harjoitus 2

Tämä on ensimmäinen Git-repositorioon lisätty tiedosto.
Harjoittelen Gitin perustoimintoja.

```

### Repositorion tilan tarkastaminen

```bash
git status
```

Tuloste:

```text
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	test.txt

nothing added to commit but untracked files present (use "git add" to track)

```

### Tiedoston lisääminen versionhallintaan

```bash
git add test.txt
```

### Talletuksen tekeminen

```bash
git commit -m "test.txt tiedoston luominen ja tallettaminen"
```

### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master
nothing to commit, working tree clean
```

---

## 3. `hello.html`-tiedoston luominen

### Tiedoston luominen ja muokkaus

```bash
vim hello.html
```

### `hello.html` tiedoston sisältö

```html
Hei maailma!
```

### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	hello.html

nothing added to commit but untracked files present (use "git add" to track)

```

### Muutosten vieminen Git-hallintaan

```bash
git add hello.html

```
```bash
git status
```

Tuloste:

```text
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   hello.html

```

### Talletuksen tekeminen

```bash
git commit -m "hello.html-tiedoston luominen"
```

### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master
nothing to commit, working tree clean
```

---

## 4. `hello.html`-tiedoston muuttaminen HTML-muotoon

### Alkuperäinen sisältö

```html
Hei maailma!
```

### Muutettu sisältö

```bash
vim hello.html
```

```html
<h1>Hei maailma!</h1>
```

### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   hello.html

no changes added to commit (use "git add" and/or "git commit -a")
```

### Muutoksen lisääminen versionhallintaan

```bash
git add hello.html
```

### Talletuksen tekeminen

```bash
git commit -m "hello.html-tiedoston muuttaminen html-muotoon"
```

### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master
nothing to commit, working tree clean
```

---

## 5. `hello.html` → `index.html`

### Tiedoston nimen muuttaminen

```bash
git mv hello.html index.html
```

### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	renamed:    hello.html -> index.html


```

### Muutoksen tallettaminen

```bash
git commit -m "hello.html tiedoston muuttaminen index.html tiedostoksi"
```


### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master
nothing to commit, working tree clean

```

---

## 6. `test.txt`-tiedoston poistaminen

### Tiedoston poistaminen versionhallinnasta

```bash
git rm test.txt
```

### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	deleted:    test.txt

```

### Muutoksen tallentaminen versionhallintaan

```bash
git commit -m "test.txt tiedoston poistaminen"
```

### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master
nothing to commit, working tree clean
```

---

## 7. Uusien tiedostojen lisääminen

### Lisätyt tiedostot

* `README.md`
* `about.txt`
* `info.html`

### Tiedostojen luominen

```bash
vim README.md
vim about.txt
vim info.html
```

### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README.md
	about.txt
	info.html

nothing added to commit but untracked files present (use "git add" to track)
```

### Tiedostojen lisääminen versionhallintaan

```bash
git add .
```

Tuloste:
```text
[master d2dc0a6] README.md, about.txt ja info.html tiedostojen lisääminen versionhallintaan
 3 files changed, 27 insertions(+)
 create mode 100644 README.md
 create mode 100644 about.txt
 create mode 100644 info.html

```

### Talletuksen tekeminen

```bash
git commit -m "README.md, about.txt ja info.html tiedostojen lisääminen versionhallintaan"
```

### Repositorion tilan tarkistaminen

```bash
git status
```

Tuloste:

```text
On branch master
nothing to commit, working tree clean

```

---

## 8. Talletusten tarkasteleminen

### `git log`

```bash
git log
```

Tuloste:

```text
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

### `git log --stat`

```bash
git log --stat
```

Tuloste:

```text
commit d2dc0a6019aa8e3b997bc3ec3e3294f167b62080
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 17:14:51 2026 +0300

    README.md, about.txt ja info.html tiedostojen lisääminen versionhallintaan

 README.md | 10 ++++++++++
 about.txt |  6 ++++++
 info.html | 11 +++++++++++
 3 files changed, 27 insertions(+)

commit 1a1bc87846a30d923c22060e7d81eb478a1467ff
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 17:06:51 2026 +0300

    text.txt tiedoston poistaminen

 test.txt | 4 ----
 1 file changed, 4 deletions(-)

commit f3d1afb92490cd4600d22de6e8edba6d5c46985d
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 17:01:01 2026 +0300

    hello.html tiedoston muuttaminen index.html tiedostoksi

 hello.html => index.html | 0
 1 file changed, 0 insertions(+), 0 deletions(-)

commit b426870e9a5913a6dbeb1210e742d2287aed4d7d
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 16:52:15 2026 +0300

    hello.html-tiedoston muuttaminen html-muotoon

 hello.html | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

commit 1c2779ed64860ac616d39b164ca56b60663dd896
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 16:14:41 2026 +0300

    hello.html-tiedoston luominen

 hello.html | 1 +
 1 file changed, 1 insertion(+)

commit 468dd4ef8e17bbb034cf140e1e1d7730fef4f07e
Author: Teemu Tanninen <teemu.tanninen@myy.haaga-helia.fi>
Date:   Wed Sep 9 16:05:41 2026 +0300

    text.txt tiedoston luominen ja tallettaminen

 test.txt | 4 ++++
 1 file changed, 4 insertions(+)

```

### Mitä lisätietoa `--stat` antaa?

Lisäämällä `--stat` asetus `git log` komentoon saadaan tarkemmat muokkaustiedot versionhallinnasta, kuten kuinka montaa tiedostoa on muutettua ja kuinka monta riviä on lisätty tai poistettu.

---

## 9. Tunnisteen lisääminen

Lisäsin viimeisimpään talletukseen tunnisteen:

```bash
git tag harjoitus2
```

### Tunnisteiden tarkistaminen

```bash
git tag
```

Tuloste:

```text
harjoitus2
```

---

## Yhteenveto käytetyistä git-komennoista


| Git-komento | Selite |
| --- | --- |
| git init | Uuden git-repositorion alustaminen hakemistoon |
| git status | Repositorion nykyisen tilan tarkastaminen |
| git add hello.html | Yksittäisen tiedoston lisääminen versionhallintaan |
| git add . | Kaikkien tiedostojen lisääminen versionhallintaan |
| git commit -m "viesti" | Staging-muutosten tallentaminen versionhallintaan annetulla viestillä. |
| git rm test.txt | Tiedoston poistaminen versionhallinnasta ja hakemistosta. |
| git mv hello.html index.html | Tiedoston nimeäminen tai siirtäminen versionhallinnassa |
| git log | Näyttää commit-talletusten historian |
| git log --stat | Näyttää commit-historian lyhyillä yhteenvedoilla talletusten muutoksista |
| git tag harjoitus2 | Lisää tunnisteen viimeisempään committiin |


### Harjoituksen lopputilanne

```bash
git status
```

Tuloste:

```text
```

