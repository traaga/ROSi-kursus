



 5. Rajaplaanimine ja navigeerimine
====================================











> 
> 
> **Räägime rajaplaneerimisest.**
> 
> 
> 
> 



![.](https://sisu.ut.ee/sites/default/files/rosak/files/navigation.gif)




Üks robotite peamisi ülesandeid on liikuda. Rajaplaanimise eesmärk on defineerida, kuidas liikuda lähtepunktist sihtkohta, võttes arvesse kõiki seonduvaid kitsendusi (nt roboti kinemaatika ja keskkonnas esinevad takistused). Tihtilugu on kaval jagada rajaplaanimine kaheks: globaalne ja lokaalne plaanimine.




**Globaalse plaanimise** eesmärk on kõige alguses, kui robot veel liikuma pole hakanud, arvutada välja parim võimalik teekond (koordinaatide järjestus) sihtpunkti. Ent kuna roboti rataste libisemine või vahepeal lisandunud takistused võivad robotit algsest teekonnast kõrvale juhtida, siis kogu liikumise vältel arvutatakse lühiajalisemat **lokaalset plaani**. Lokaalse plaanimise eesmärk on korrigeerida triivi ja juhtida robot uuest takistustest mööda. ROSis on lokaalse plaanimise väljundiks roboti liikumist suunavad kiiruskäsud.




Kaardid, rajaplaanimine ja lokaliseerimine kokku moodustab roboti navigeerimisvõimekuse. Räägime robotite navigeerimisvõimekusest, kui saame robotile anda ette sihtkoha ning seejärel suudab roboti tarkvara genereerida roboti juhtkäsud, mis tagavad roboti kokkupõrkevaba saabumise sihtpunkti.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/kuvatommis_2022-10-30_21-13-54.png)



 







