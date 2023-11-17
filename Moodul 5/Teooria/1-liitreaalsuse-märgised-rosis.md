



 1. Liitreaalsuse märgised ROSis
=================================











> 
> 
> **Inimestena on meil üpris lihtne vaadata objekte enda ümber ja teada, mis need on. Arvutitele võib see valmistada probleeme. Sellepärast on robotitega töötamisel mõnikord võimalik ja kasulik nende elu lihtsustada ja kasutada liitreaalsuse märgiseid.**
> 
> 
> 
> 



### [**Mis on liitreaalsuse märgised?**](#)

Liitreaalsuse (ing k. Augmented Reality) märgised ehk AR märgised on must-valged pildikesed, mis meenutavad QR koode. Alloleval pildil on näha mõnda näidet AR märgistest. Pane tähele, kuidas igal märgisel on erinev ruudustik ja et kõik nurgad on 90-kraadised. See ruudustik on igal märgisel unikaalne ja ei kordu ka märgiseid pöörates.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/marker1.png)![.](https://sisu.ut.ee/sites/default/files/rosak/files/marker2.png)![.](https://sisu.ut.ee/sites/default/files/rosak/files/marker3.png)




Kaamera abil on võimalik AR märgiste abil saada palju kasulikku informatsiooni. Võimalik on leida, millise AR märgisega on tegemist, samuti saab kindlaks määrata märgise positsiooni ja orientatsiooni.




Seetõttu on AR märgistel robootikas palju rakendusvõimalusi. Robot võib määrata enda asukohta ruumis, kui ta näeb fikseeritud AR märgist, mida ta on ka varem samas kohas näinud. Kinnitades AR märgise roboti enda külge saame kaamerapildist teada roboti asukoha. Võimalik on ette kujutada veel paljusid olukordi, kus AR märgised robootikas kasulikud on.




Kasutades ROS-i kimpu ar\_track\_alvar saame me AR märgisest järgneva info:




 Neist toorandmetest saame eristada kolm kõige huvipakkuvamat sektsiooni:



1. ID
2. Positsioon (ingl *position*)
3. Orientatsioon (ingl *orientation*)



 Järgnevalt tutvume neist igaühega veidi lähemalt.









### [**ID**](#)

Igale märgisele vastab kindel ID. Alloleval pildil on näha AR märgiseid ID-ga 3, 4 ja 5. Sama ID-ga märgised näevad alati välja samasugused, ja kahel erineval märgisel ei ole kunagi sama ID. See tähendab, et märgise must-valge ruudustiku mustri järgi on võimalik teada saada märgise ID.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/ar_markers_w_id.png)




> 
> #### 
> Infoks!
> 
> 
> 
> Küll aga peab tähele panema, millise süsteemiga on tegu. Nagu on maailmas palju keeli, nii on ka palju erinevaid süsteeme AR märgiste jaoks. Seni, kuni on teada, millist süsteemi kasutame, on aga lihtne märgise mustri järgi saada kätte selle ID.
> 
> 
> 
> 



Üks võimalik olukord, kus märgiste ID on kasulik, on asjade tuvastamine. Näiteks hulga sarnaste karpide hulgast kindla karbi ülesleidmine võib olla keeruline, sest ei piisa sellest, kui tuvastada, et tegemist on karbiga. Kui aga igal karbil on peal AR märgis, ja me otsime näiteks karpi märgisega nr 5, läheb õige karbi leidmine väga palju kergemaks.




Võib ka juhtuda, et robot otsib kindlat eset teiste hulgast, aga ta ei tea, mis tüüpi eset ta otsib, ega oska ka ühtegi eset ära tunda. Sellist olukorda illustreerivad allolevad pildid. Selle asemel, et õpetada robot ära tundma suurt hulka erinevaid esemeid, on programmeerija jaoks väga palju lihtsam teha robotile selgeks, et vaja on leida kindla ID-ga AR märgis.




*Liiguta pildi keskel olevat slaiderit!*














### [**Positsioon**](#)

AR märgise positsioon on selle suhteline asukoht kaamerapildi keskpunkti suhtes.









Jälgi ülaltoodud videot. Kaamerapildis on AR märgis, mida liigutatakse kaamera suhtes üles ja alla, vasakule ja paremale, kaugemale ja lähemale. Üles-alla liikumisel on näha, kuidas muutuvad numbrid **y-teljes**. Vasakule ja paremale liikudes on näha kõige rohkem muutust **x-teljes**. Kaugemale ja lähemale liikudes muutuvad enim aga numbrid **z-teljes**. Sellest on näha, et need kolm komponenti (x, y, z) annavad meile infot AR märgise **positsiooni** kohta.




Alloleval pildil on toodud veel üks näide. Pildil on näha simuleeritud robotit, mille ees seinal on AR märgis. Märgis on 1.2 m kaugusel roboti ees ehk märgise kaugus robotist x-teljes on 1.2 m (roheline joon näitab 1 m kaugust seinast). Leia see kaugus pildi kõrval olevatest toorandmetest. Punane nool pildil näitab roboti koordinaatsüsteemi x-telje suunda.




Rohelise noolega on pildil märgitud y-komponent. Y-teljes on AR märgise kaugus -0.26 m, mis tähendab, et märgise keskpunkt on roboti kaamerapildi keskpunktist 0.26 m paremal.




Märgise positsioon z-teljes on nullilähedane, mis tähendab, et märgise keskpunkt on üsna samal kõrgusel roboti kaamerapildi keskpunktiga. Pildil on z-telg märgitud sinise noolega.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/position.png)









### [**Orientatsioon**](#)

Orientatsioon kirjeldab, mis suunas ja kui palju on AR märgist pööratud. Kuna märgise muster ei muutu ja sel puudub vertikaalne sümmeetria, on mustri järgi võimalik öelda, kui palju on märgist keeratud (ing k. roll). AR märgiste kõik nurgad on 90-kraadised, seega kui märgist kallutada (ing k. pitch) või pöörata (ing k. yaw), muutub osa nurkadest suuremaks kui 90 kraadi ja osa väiksemaks. Selle näide on toodud parempoolsel pildil. Nende nurkade järgi on võimalik leida märgise täpne nurk ja suund kaamera suhtes. Teine viis märgise orientatsiooni mõistmiseks on mõelda märgise sirgete joonte suunalistest suunavektoritest – vektorite koondumine ja lahknemine annavad infot märgise orientatsiooni kohta.




Orientatsiooni toorandmed, mille saame ar\_track\_alvar kimpu kasutades, näevad esmapilgul välja, nagu need võiksid olla nurgad x-, y- ja z-teljes, lisaks veel üks w. See ei ole nii.




Need x, y, z ja w moodustavad **kvaternioni**. Kvaternionid on matemaatilised konstruktsioonid, mida kasutatakse 3D pöörete kirjeldamiseks. Selleks, et need oleksid kergemini mõistetavad, tuleb need **teisendada** mõnele muule kujule, näiteks **Euleri nurkadeks**. Euleri nurgad kirjeldavad objekti orientatsiooni x- (roll), y- (pitch) ja z-teljes (yaw) fikseeritud võrdlusorientatsiooni suhtes. Need kolm telge on toodud alloleval vasakpoolsel pildil. Antud juhul on võrdlusorientatsiooniks pööramata AR märgise orientatsioon.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/roll_pitch_yaw_1.png)![.](https://sisu.ut.ee/sites/default/files/rosak/files/roll_pitch_yaw_2.png)








