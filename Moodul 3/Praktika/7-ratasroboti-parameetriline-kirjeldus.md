



 7. Ratasroboti parameetriline kirjeldus
=========================================











> 
> 
> **Selles õppetükis vaatame, kuidas saab URDF mudelist luua paindliku ja kergesti muudetava XACRO mudeli. Loome XACRO formaadis kirjelduse eelnevas peatükis loodud robotimudelist.**
> 
> 
> 
> 
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



### [**1. Mis on XACRO?**](#)

XACRO on **XML-põhine makrokeel**, millega saab ROSi robotitele luua **parametriseeritud mudeleid**. Hästi organiseeritud XACRO olemasolu korral on roboti mudeli muutmine väga lihtne. URDF mudeli muutmine on tülikam, sest muudatusi peab tegema palju rohkemates kohtades.




Kuna XACRO fail on kõrgema tasemega kui URDF, on roboti mudeli ROS-is kasutamiseks vaja XACRO teisendada klassikalisse URDF formaati. Selle jaoks saab kasutada xacro käsku, mis on ROSis algusest peale olemas.









### [**2. Ettevalmistused**](#)

Võtame aluseks eelnevas peatükis loodud fourwheeler.urdf faili. Liigume urdf kausta ja teeme URDF failist koopia nimega fourwheeler.urdf.xacro.














### [**3. XACRO faili käivitamine**](#)

XACRO formaadis kirjeldatud mudelit saame visualiseerida sama display.launch faili abil, mille lõime eelmisel sammul.




 Leia üles eelnevalt loodud display.launch fail ja muuda seda nõnda, et mudeli fourwheeler.urdf asemel kasutataks mudelit fourwheeler.urdf.xacro.




Käivita nüüd käivitusfail. Avaneb RVizi aken, kus näeme eelnevalt loodud robotimudelit.









### [**4. XACRO kirjutamine: eeltöö**](#)

Avame fourwheeler.urdf.xacro faili endale meelepärases tekstiredaktoris.




Selleks, et saaksime XACRO keelt oma failis kasutada, peame märgendile robot lisama XACRO XML nimeruumi (xmlns).




 Nimeruumi lisamise koodijupp, mis tuleb paigutada õigesse kohta (vt allolevalt animatsioonilt):




```
xmlns:xacro="http://www.ros.org/wiki/xacro"
```












### [**5. XACRO kirjutamine: miks?**](#)

Roboti kirjeldus algab base\_link definitsiooniga. Näeme, et lüli geomeetria määravad kolm arvu, mis on konstantsed (märgendiga box size). Oletame, et oleme oma füüsilise roboti kere suurust muutnud, ja robot on nüüd 20 cm laiem. Mudeli muutmiseks peame muutma roboti kere suuruse teist väärtust (suurus y-teljes). **Anname sellele väärtuse 0.320 asemel uue väärtuse 0.520.**




Kui aga vaatame nüüd uuendatud mudelit, näeme, et rattad asuvad nüüd roboti kere sees. Oleks mugav, kui saaksime muuta roboti suurust selliselt, et rattad püsiksid alati kere kõrval.  










### [**6. XACRO muutujate loomine**](#)

![.](https://sisu.ut.ee/sites/default/files/rosak/files/4wheeler_drawings.png)




Selleks, et saavutada mudel, kus kere suuruse muutumisel paigutuvad ka rattad ümber, saame kasutada **XACRO** **muutujaid** (ingl k. *property*).




Kui oleme korra muutuja väärtuse määranud, saame edaspidi lasta XACRO-l kasutada mitmes kohas sama muutujat. Kui hiljem on vaja muutuja väärtust korrigeerida, peame seda tegema ainult seal, kus muutuja on defineeritud.




Teeme muutuja kere laiuse (base\_width) jaoks. Saame seda teha märgendiga xacro:property, millele järgnevad nimi (name) ja väärtus (value).




Lisame muutujad ka rataste raadiuse ja laiuse jaoks.











