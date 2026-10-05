# Harjoitus 4 – Ominaisuushaarat

## 1. HTML-sivun perusrakenteen lisääminen

Muokkasin `hello.html`-tiedoston HTML-sivun perusrakenteeseen.

### `hello.html`

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hello</title>
</head>

<body>
  <main>
    <h1>Hei maailma!</h1>
  </main>

</body>

</html>
```

---

## 2. Muutosten tallettaminen `master`-haaraan

### Komennot

```bash
git add index.html
git commit -m "Lisää HTML-sivun perusrakenne"
```

---

## 3. Tyylien lisääminen

### Luo `styles.css`

```css
html {
  height: 100%;
}

body {
  background-color:linen;
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;
}

main {
  text-align: center;
}
```

### Liitin tyylit `index.html`-tiedostoon

Lisäsin `<head>`-osioon:

```html
<link rel="stylesheet" href="styles.css">
```


### Testasin sivun selaimessa

**Havainto:**
Hei maailma! on asettunut sivun keskelle sekä horisontaalisesti että vertikaalisesti ja sivun taustaväri on vaihtunut.

---

## 4. Ominaisuushaaran luominen

Loin tyylimuutoksia varten uuden haaran nimeltä `tyylit`.

### Komento

```bash
git switch -c tyylit
```

### Talletin tyylimuutokset `tyylit`-haaraan

```bash
git add .
git commit -m "Lisää sivulle tyylit"
```

---

## 5. Aktiivisen haaran vaihtaminen

### Vaihdoin `master`-haaraan

```bash
git switch master
```

Latasin sivun selaimessa uudelleen.

**Miten sivu muuttui?**
Master-haarassa olevalla sivulla ei ole uutta tyyliä ja "Hei maailma!" teksti sijaitsee sivuston vasemmassa yläkulmassa.

---

### Vaihdoin `tyylit`-haaraan

```bash
git switch tyylit
```

Latasin sivun selaimessa uudelleen.

**Miten sivu muuttui?**

Tyylit-haarassa sivulla on uudet tyylit ja "Hei maailma!" teksti on sivun keskipisteessä.

---

## 6. `tyylit`-haaran yhdistäminen `master`-haaraan

Vaihdoin ensin `master`-haaraan:

```bash
git switch master
```

Yhdistin `tyylit`-haaran:

```bash
git merge --no-ff tyylit

```

`--no-ff` laajenninta kättämällä yhdistäminen jää versiohistoriaan näkyville.

### Tarkistin historian

```bash
git log --oneline --decorate --graph --all
```

**Tuloste**
```text
*   e973da0 (HEAD -> master) Yhdistä 'tyylit' haara 'Master' haaraan.
|\  
| * abe0742 (tyylit) Lisää sivulle tyylit
|/  
* 0f0d212 Lisää HTML-sivun perusrakenne
* 8ca16dc (tag: harjoitus3) Revert "Muokkasin index.html ja about.txt tiedostoja."
* face3ab Muokkasin index.html ja about.txt tiedostoja. Lisäsin uusi1.txt ja uusi2.txt tiedostot.
* d2dc0a6 (tag: harjoitus2) README.md, about.txt ja info.html tiedostojen lisääminen versionhallintaan
* 1a1bc87 text.txt tiedoston poistaminen
* f3d1afb hello.html tiedoston muuttaminen index.html tiedostoksi
* b426870 hello.html-tiedoston muuttaminen html-muotoon
* 1c2779e hello.html-tiedoston luominen
* 468dd4e text.txt tiedoston luominen ja tallettaminen
```

---

## 7. Haarojen vaihtaminen yhdistämisen jälkeen

Vaihdoin aktiivista haaraa master- ja tyylit-haarojen välillä ja latasin sivun selaimessa uudelleen.

### Komennot

```bash
git switch master
git switch tyylit
```

### Miten sivu eroaa haarojen välillä yhdistämisen jälkeen?

`master` ja `tyylit` haarojen välillä ei ollut eroa ja sivu näytti samalta molemmissa haaroissa. Molemmissa "Hei maailma!" lause on sivun keskipisteessä ja taustaväri on muuttunut.

---

## 8. Tunnisteen lisääminen

Vaihdoin päähaaraan:

```bash
git switch master
```


Lisäsin viimeisimpään talletukseen tunnisteen:

```bash
git tag harjoitus4
```

### Tarkistin tunnisteen

```bash
git tag


```

**Tuloste**

```text
harjoitus2
harjoitus3
harjoitus4


```

### Tarkistin lopullisen historian

```bash
git log --oneline --decorate --graph --all
```

**Tuloste**:

```text
*   e973da0 (HEAD -> master, tag: harjoitus4) Yhdistä 'tyylit' haara 'Master' haaraan.
|\  
| * abe0742 (tyylit) Lisää sivulle tyylit
|/  
* 0f0d212 Lisää HTML-sivun perusrakenne
* 8ca16dc (tag: harjoitus3) Revert "Muokkasin index.html ja about.txt tiedostoja."
* face3ab Muokkasin index.html ja about.txt tiedostoja. Lisäsin uusi1.txt ja uusi2.txt tiedostot.
* d2dc0a6 (tag: harjoitus2) README.md, about.txt ja info.html tiedostojen lisääminen versionhallintaan
* 1a1bc87 text.txt tiedoston poistaminen
* f3d1afb hello.html tiedoston muuttaminen index.html tiedostoksi
* b426870 hello.html-tiedoston muuttaminen html-muotoon
* 1c2779e hello.html-tiedoston luominen
* 468dd4e text.txt tiedoston luominen ja tallettaminen
```

---

# Yhteenveto

## Harjoituksessa käytetyt Git-komennot

```bash
git add
git commit
git switch
git merge --no-ff
git log
git tag
```

