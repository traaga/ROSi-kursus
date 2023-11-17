



 Kodutöö. Robotont ja porgandid
================================











> 
> 
> **Selles harjutuses paneme robotondi iseseisvalt sõitma ühe oranži porgandi juurest teise juurde, siis kolmanda juurde ja nõnda edasi.**
> 
> 
> 
> 
>  Selleks uurime kolme erinevat ROSi kimpu ja paneme nad kõik koos töötama.
>  
> 
> 
> 
> **Selle harjutuse sooritamiseks on vaja:**
> 
> 
> 
> * **Töötavat robotondi robotit**
> * **Oranžide porganditega keskkonda, kus ei ole muid oranže objekte**
> 
> 
> 
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 





### [**1. Mida me teha tahame?**](#)

Harjutuse lõpuks tahame saavutada järgmist: tahame, et robotont otsiks enda ümbruskonnast üles oranži porgandi ja sõidaks selle juurde. Kui ta on porgandi juurde jõudnud, siis tahame, et ta otsiks mõne teise porgandi ning sõidaks selle juurde. Niimoodi jätkab ta seni, kuni programm peatatakse.




 Vaata lõpptulemust sellest videost:









 Selle tulemuse saavutamiseks paneme omavahel koos töötama **kolm sõlme**:



1. Sõlm, mis võtab kaamerast pildi ja kuulutab saadud pilti mõnes rubriigis.
2. Sõlm, mis kuulab rubriiki, kus on kaamera pildid, ja leiab neilt oranžid porgandid.
3. Sõlm, mis võtab tuvastatud porgandite asukohad ja paneb roboti nende järgi sõitma.



 Vaatame neid ükshaaval.









### [**2. Kaamera pilt**](#)

Robotondi robotil töötab sõlm, mis kuulutab kindlasse rubriiki kaamerast tulnud värvilist pilti.




 Kasutame ROSi tööriistu, et leida sobiv rubriik:




```
rostopic list
```


 Näeme rubriikide hulgas rubriiki nimega /camera/color/image\_raw\_throttled. Kasutame seda, et saada kätte soovitud pilt.




> 
> #### 
>  Ettevaatust!
> 
> 
> 
>  Ära kasuta rubriiki /camera/color/image\_raw. See jooksutab suure andmemahu tõttu süsteemi kokku.
>  
> 
> 
> 








### [**3. Laigutuvastaja paigaldamine**](#)

Porgandeid on kõige lihtsam tuvastada värvi järgi: kui porgandid on oranžid ja ümbruskonnas teisi sama värvi objekte ei ole, siis võib robot lihtsalt leida kõik oranži värvi objektid ja need ongi otsitavad porgandid.




 Selleks kasutame **laigutuvastajat (*blob detector*)**.




 Laigutuvastaja kasutamiseks kasutame ROSi kimpu nimega **opencv\_apps**. Täpsemini soovime kasutada versiooni, milles sisaldub laigutuvastaja: seetõttu ei saa me seda installida käsureatööriistaga apt, vaid **kompileerime selle lähtekoodist**.




**Navigeeri terminaliga catkini tööruumis kausta** src**, kuhu paigutatakse ROSi kimpude lähtekood.** Vajadusel kontrolli käsuga pwd, et oled õiges asukohas.




**Klooni endale laigutuvastajat sisaldava kimbu lähtekood** **järgmiste käskudega:**




```
git clone https://github.com/ut-ims-robotics/opencv_apps.git
cd opencv_apps
git checkout blob_detection_nodelet
```


**Kompileeri catkini tööruum ja laadi see.**









### [**4. Laigutuvastaja kasutamine**](#)

Kimp opencv\_apps ei ole mõeldud vaid porgandite tuvastamiseks. Selleks, et laigutuvastaja leiaks üles just porgandid, on meil vaja programmile öelda, et ta otsiks justnimelt oranži värvi. Selleks ava tekstiredaktoriga kimbu opencv\_apps alamkaustas config tekstifail nimega blob\_detection\_config.yaml.




 Failis näed mitmeid parameetreid. Porgandite tuvastamiseks leia neist järgmised viis ja anna neile järgmised väärtused:




```
hue_lower_limit: 5
hue_upper_limit: 20
...
min_area: 20
...
sat_lower_limit: 160
...
val_lower_limit: 100

```


 Need väärtused tähendavad, et tuvastatakse objekte, mis **HSV värviruumis** jäävad vahemikku, mis vastab oranžile toonile, ning otsime oranži ala, mis ei ole väga väike.




 Ära unusta faili pärast muudatuste tegemist salvestada.




**Katseta tulemust**, käivitades opencv\_apps-nimelise kimbu käivitusfaili nimega blob\_detection.launch nõnda, et argumendi debug\_mode väärtuseks on antud deploy ning argumendi image väärtuseks antud **varasemalt leitud kaamera pildi rubriik** (asenda kirjuta\_siia\_kaamera\_pildi\_rubriik sellega):




```
roslaunch opencv_apps blob_detection.launch debug_mode:=deploy image:=kirjuta_siia_kaamera_pildi_rubriik
```


 Argumendi debug\_mode väärtus deploy paneb selle käivitusfaili kasutama yaml-faili, millesse lisasime eelnevalt oranži värvi tuvastamiseks vajaliku info. Argumendi image väärtus aga määrab, missugust rubriiki kasutatakse pildi allikana.




> 
> #### 
>  Aga kui mul ei tööta?
> 
> 
> 
>  Kas **kompileerisid** ja seejärel ka **laadisid** catkini tööruumi?
>  
> 
> 
> 



 Kui kõik on läinud hästi, siis saad nüüd ROSi tööriistu kasutades leida, et on tekkinud rubriik nimega /blob\_detection/blobs, kuhu kuulutab sõlm nimega blob\_detection. **Kasuta ROSi tööriistu, et pealt kuulata selles rubriigis kuulutatud sõnumeid.** Kui roboti vaateväljas on oranž porgand, siis peaks käivitatud sõlm tuvastama selle asukoha.









### [**5. Liikumise kontroll**](#)

Viimase asjana on meil vaja midagi, mis paneks roboti liikuma tuvastatud porgandite juurde.




 Selleks kasutame [väga väikest ROSi kimpu](https://github.com/unitartu-edu/carrot_follower "https://github.com/unitartu-edu/carrot_follower"), mis sisaldab sisuliselt vaid üht Pythoni faili. Selle käivitamisel tellib sõlm üht rubriiki, võtab sealt oranži laigu asukoha ja liigub selle juurde. Siis keerab robot end vastupäeva, leiab järgmise laigu ning sõidab selle juurde.




**Navigeeri terminaliga jälle catkini tööruumis kausta** src**, kuhu paigutatakse ROSi kimpude lähtekood.** Vajadusel kontrolli käsuga pwd, et oled õiges asukohas. Sisesta järgmine käsk kimbu lähtekoodi allalaadimiseks:




```
git clone https://github.com/unitartu-edu/carrot_follower.git
```


**Kompileeri catkini tööruum ja laadi see.**




**Leia, mis on uues kimbus asuva käivitatava Pythoni-faili nimi** (see lõppeb faililaiendiga .py)**. Käivita see sõlm õige ROSi käsuga (lisaks peab kusagil jooksma laigutuvastaja sõlm).**




**Kasuta ROSi vahendeid, et leida, mis rubriiki tellib äsja käivitatud sõlm.** Näed, et see ei ole täpselt sama, mis rubriik, kuhu kuulutatakse tuvastatud laikude asukohti.




 Peata sõlm ja **käivita see uuesti**, aga seekord nii, et **sõlm telliks rubriiki, kus on päriselt oranžide laikude asukohad**.




 Kui kõik läks õigesti, siis sõidab robot nüüd porgandite vahet.




> 
> #### 
>  Midagi on valesti! Mis teha?
> 
> 
> 
>  Kui midagi on valesti, siis võid **kasutada ROSi käsureatööriistu**, et leida:
>  
> 
> 
> * Kas kõik vajalikud sõlmed on käivitatud?
> * Kas iga sõlm kuulutab sellesse rubriiki, kuhu peaks, ja tellib seda rubriiki, mida peaks?
> * Kas olulistesse rubriikidesse jõuavad sõnumid?
> * Kas nendes sõnumites sisaldub soovitud info?
> 
> 
> 



 Kui soovid näha, mida robotont näeb, siis käivitajärgmine käsk:




```
rviz -d ~/catkin_ws/src/carrot_follower/config/watch_carrots.rviz
```






