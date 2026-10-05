# Harjoitus 1 --- Johdanto

## 1. Gitin asentaminen

### Asennus

Asensin Gitin koneelle käyttämällä CachyOS Linux käyttöjärjestelmän paketinhallintaa:

```bash
sudo pacman -S git
```

### Tarkistin Git-version

```bash
git --version
```

**Tuloste:**

```text
git version 2.55.0
```

---

## 2. Visual Studio Coden asentaminen

### Asennus

Asensin Visual Studio Coden käyttämällä yay -paketinhallintatyökalua AUR-käyttäjärepositiorista.

```bash
yay -S visual-studio-code-bin
```

### Asennuksen tarkistus

Tarkistin VS Coden asennuksen komennolla:

```bash
code --version
```

**Tuloste:**

```text
1.135.0
08d4889f9ec4a1685d257b9b95de036c8e1ce1e5
x64
```

Tarkistin myös Visual Studio Coden:n työpöytäsovelluksen käynnistämällä sovelluksen.

---

## 3. Gitin konfigurointi

### Käyttäjänimen määrittäminen

```bash
git config set --global user.name "Teemu Tanninen"
```

### Sähköpostiosoitteen määrittäminen

```bash
git config set --global user.email teemu.tanninen@myy.haaga-helia.fi
```

### Editorin määrittäminen

Suosin NeoVim(nvim) editoria, joka on vim editorista jatkokehitetty kattavampi versio.

Saatavilla: [Neovim](https://neovim.io/)

```bash
git config set --global core.editor "nvim"
```

### Konfiguraation tarkistaminen

```bash
git config list --global
```

**Tuloste:**

```text
user.name=Teemu Tanninen
user.email=teemu.tanninen@myy.haaga-helia.fi
core.editor=nvim
```

---

## 4. GitHub-tilin luominen

### GitHub-tili

Olen jo aikaisemmin luonut käyttäjätilin Githubiin käyttäjänimellä `NikodemiusTKT`

Saatavilla: [Github.com/NikodemiusTKT](https://github.com/NikodemiusTKT)

---

## 5. Yhteenveto

### Käytetyt Git-komennot

| Git-komento | Kuvaus |
| --- | ---|
| git --version | git versionumeron tulostus |
| git config --global set user.name| Git:n käyttäjänimen asetus globaalisti |
| git config --global set user.email | Git:n Sähköpostiosoitteen asetus globaalisti |
| git config --global set core.editor | Git:ssä käytetyn tekstieditorin asetus. |
| git config list --global | Git:n globaalien asetusten tulostus |


