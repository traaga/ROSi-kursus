



 4. SLAM
=========











> 
> 
> **Robootikas võib sageli kuulda terminit SLAM. Mis on SLAM ja kuidas see töötab?**
> 
> 
> 
> 



SLAM on samaaegselt lokaliseerimine ja kaardistamine (ingl *Simultaneous Localisation and Mapping*).




Seni oleme vaadelnud juba olemasoleva kaardi abil lokaliseerimist. Kaardi loomiseks peaksime aga selle ja kõik huvipakkuvad punktid sellel käsitsi joonistama, mis on väga ajamahukas töö.




Lihtsam meetod on kasutada roboti sensoreid (näiteks kaamerat), et luua kaart, kui robot liigub toas ringi. Robot skännib kaaderhaaval keskkonda. Hiljem saab neist kaadritest tükkhaaval kaardi kokku panna. Selleks aga on vaja teada, kus robot iga kaadri salvestamise hetkel oli ehk mis oli roboti vaatepunkt. Seda probleemi illustreerib allolev joonis.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/slamproblem-est.png)





---



 Selles harjutuses on kasutatud ja mugandatud David Kostolani (TU Wien) loodud õppematerjale.



 







