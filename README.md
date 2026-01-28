# KOL Studio – Dokumentaatio

Tämä dokumentaatio kuvaa **KOL Studio** -editorin ja viewerin käytön, ominaisuudet ja tiedostomuodot. Dokumentti on tarkoitettu luettavaksi erillään HTML-tiedostosta, esimerkiksi README.md- tai docs.html-tiedostona.

Linkki Kol Studioon: [https://cmdman-urlman.github.io/Kol-studio/](https://cmdman-urlman.github.io/Kol-studio/)

---

## 1. Yleiskuva

KOL Studio on **yhden HTML-tiedoston** editori ja viewer, jolla voit:

* rakentaa visuaalisia lavoja (stage)
* lisätä kuvia ja videoita layereina
* siirtää ja muuttaa niiden kokoa
* nimetä layerit
* tallentaa projektin `.kol`-tiedostoksi
* avata saman projektin eri laitteilla
* synkata editorin ja viewerin reaaliaikaisesti

Ei vaadi:

* kirjautumista
* Firebasea
* backend-palvelinta

*Kommentti: tiivistetty yleiskuva ja lisätty linkki pääsivulle.*

---

## 2. Peruskäyttö

### 2.1 Editorin avaaminen

Avaa Kol Studio selaimessa osoitteessa:

```
https://cmdman-urlman.github.io/Kol-studio/
```

Editorissa voit:

* lisätä kuvia ja videoita
* nimetä layerit
* siirtää ja skaalata layereita
* vaihtaa taustavärin
* tallentaa `.kol`-projektin

*Kommentti: päivitetty URL vastaamaan GitHub Pages -osoitetta.*

---

## 3. Viewer-tila (esitystila)

Viewer-tila piilottaa editorin käyttöliittymän ja näyttää vain lopullisen sisällön.

### 3.1 Viewer päälle

```
https://cmdman-urlman.github.io/Kol-studio/?view
```

### 3.2 Automaattinen fullscreen

```
https://cmdman-urlman.github.io/Kol-studio/?view&fullscreen
```

Viewer menee automaattisesti fullscreen-tilaan TV- ja kioskikäytössä.

---

## 4. Live-sync (reaaliaikainen synkronointi)

Editor ja viewer voidaan yhdistää reaaliaikaisesti.

### 4.1 Editor

```
https://cmdman-urlman.github.io/Kol-studio/?live=demo
```

### 4.2 Viewer

```
https://cmdman-urlman.github.io/Kol-studio/?view&fullscreen&live=demo
```

Kaikki muutokset päivittyvät heti:

* layerien sijainti
* koko
* nimet
* tausta

Tekniikka:

* `BroadcastChannel`
* toimii samalla laitteella tai saman verkon selaimissa

---

## 5. Autoplay-lock

Estää käyttäjän klikkaukset viewer-tilassa.

```
https://cmdman-urlman.github.io/Kol-studio/?view&autoplay
```

Soveltuu:

* infonäytöt
* messut
* taustavideot

---

## 6. Skaalaus eri näytöille

### 6.1 Fit (oletus)

```
?view&scale=fit
```

Sisältö näkyy kokonaan (suhteet säilyvät).

### 6.2 Fill

```
?view&scale=fill
```

Sisältö täyttää koko ruudun (reunoja voidaan rajata).

---

## 7. .kol-tiedostomuoto

`.kol` on **itsenäinen projektitiedosto**, joka sisältää kaiken tarvittavan datan.

### 7.1 Sisältö

* taustaväri
* lavan koko
* layerien nimet
* kuvat (base64)
* videot (base64)
* sijainnit ja koot

### 7.2 Esimerkki

```json
{
  "bg": "#333333",
  "stage": {"w": "640px", "h": "360px"},
  "layers": [
    {
      "name": "Taustavideo",
      "tag": "VIDEO",
      "src": "data:video/mp4;base64,...",
      "x": "0px",
      "y": "0px",
      "w": "640px",
      "h": "360px"
    }
  ]
}
```

*Kommentti: Selkeytetty sisältö ja kuvattu URL-tiedostojen käyttö live-projekteissa.*

---

## 8. Suositeltu käyttötapa

* 📱 Puhelin: editori
* 📺 TV / näyttö: viewer
* 🔄 Live-sync URL-parametrilla

Esimerkki:

```
Editor: https://cmdman-urlman.github.io/Kol-studio/?live=show1
Viewer: https://cmdman-urlman.github.io/Kol-studio/?view&fullscreen&live=show1&autoplay&scale=fill
```

---

## 9. Selainyhteensopivuus

Suositellaan:

* Chrome
* Edge

Toimii myös:

* Android Chrome
* Smart TV (Chromium-pohjainen)



**KOL Studio** on suunniteltu kevyeksi, offline-yhteensopivaksi ja helposti julkaistavaksi työkaluksi.
