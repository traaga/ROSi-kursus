



 2. Roboti liikumine
=====================











> 
> 
> **Oleme juba päris palju ROSis robotit liigutanud. Kuidas see tegelikult toimib?**
> 
> 
> 
> 



Igal ROSi toega robotil on miski, mille nimi on ROSi draiver. Mobiilsel robotil, näiteks robotondil, on draiveriks sõlm, mis tellib üht olulist rubriiki: cmd\_vel. Selles rubriigis kuulutatud sõnumid sisaldavad infot selle kohta, **kuidas** me soovime **robotit liigutada**. Draiverisõlm võtab need sõnumid ja teisendab need sobivateks kiirusteks kõigi mootorite jaoks, pannes roboti liikuma just selle kiirusega ja selles suunas, nagu oli kirjeldatud cmd\_vel rubriigist saadud sõnumis.




Seega kui soovime programmeerida roboti kindlat moodi liikuma, siis tuleb meil luua sõlm, mis kuulutab sõnumeid rubriigis cmd\_vel. Selleks on vaja teada, kuidas cmd\_vel rubriigi sõnumid välja näevad.




Rubriigi cmd\_vel sõnumitel on kindel struktuur ehk tüüp nimega **Twist**. Twist kuulub kategooriasse nimega geometry\_msgs ja sisaldab **kaht vektorit**, millest **kummaski** on **kolm reaalarvu**. Esimesed kolm moodustavad vektori nimega *linear* ja kirjeldavad **lineaarset liikumist** kolmemõõtmelise ruumi kolmes suunas. Teised kolm moodustavad vektori nimega *angular* ja kirjeldavad roboti **pöördliikumist** ümber nendesamade kolme telje.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/twist2.png)




Täpsemini: vaatame meie robotit. Robotont suudab liikuda edasi ja tagasi ning end kohapeal pöörata. Oma rataste tõttu suudab ta aga ka liikuda külgsuunas. ROSis on roboti liikumise koordinaatsüsteemi **x-telg** suunatud **ettepoole**, **y-telg vasakule** ja **z-telg üles**. Twist-tüüpi sõnumis tähistab esimene kolmest arvust koosnev vektor **kiiruseid** (ühikuks m/s) nendes kolmes teljes. Selle vektori nimi on linear.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/linear.gif)




Twist-sõnumid on mõeldud olema universaalsed, et neid saaks kasutada iga roboti jaoks: ka nende jaoks, mis saavad liikuda üles ja alla, s.t. mööda z-telge. Meie robot seda teha ei suuda.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/ibelieveicanfly.gif)




See-eest suudab ta end selle ümber pöörata. Siin tuleb mängu teine vektor, nimega angular. Sarnaselt sisaldab see kolme arvu, mis vastavad nüüd **nurkkiirustele** vastavate telgede ümber: x-telg, y-telg ja z-telg (ühikuks radiaan sekundis ehk rad/s). Meie robot suudab pöörelda ainult ümber z-telje.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/angular.gif)




Ühesõnaga, et robotit kindlal viisil liikuma saada, on meil vaja luua sobiv Twist-tüüpi sõnum ja see cmd\_vel rubriiki kuulutada. Robotondi jaoks on Twist-sõnumis olulised linear.x, linear.y ja angular.z komponendid.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/twist1.png)




> 
> #### 
> Kuidas me enne robotit liigutasime?
> 
> 
> 
> Varasemalt robotondi juhtimiseks kasutatud teleop\_twist\_keyboard.py sõlm pani roboti või selle simulatsiooni liikuma täpselt samal põhimõttel. Antud sõlm kuulutas rubriigis cmd\_vel Twist-tüüpi sõnumeid, nii et iga sõnumi linear.x, linear.y ja angular.z komponentite arvväärtused muutusid vastavalt arvuti klaviatuuril vajutatud klahvidele.
> 
> 
> 
> 


 







