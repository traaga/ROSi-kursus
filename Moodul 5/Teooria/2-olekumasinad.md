



 2. Olekumasinad
=================











> 
> 
> **Robotite kood peab tegema paljusid eri asju: saama infot sensoritelt, selle põhjal otsuseid vastu võtma ja mõnikord ka mäletama, mis on varem tehtud. Selleks, et kõiki neid funktsioone hästi sooritada, on kasulik mõelda roboti koodist kui olekumasinast.**
> 
> 
> 
> 



**Lõplik olekumasin** on matemaatiline mudel, kus süsteem (näiteks meie robot) saab olla erinevates **olekutes**.




Võime näitena mõelda koodi peale, mis teises moodulis otsis porgandeid. See kood pidi keerama end porgandi suunas, selle juurde sõitma, siis aru saama, et ta on porgandile piisavalt lähedal, ja uue porgandi poole keerama. Aga kuidas kood pärast porgandi juurde sõitmist aru saab, et ta võib nüüd seda porgandit ignoreerida, seni, kuni uut otsib?




Meie porgandiotsija kood lahendab selle probleemi kahe olekuga. See, kummas olekus robot parasjagu on, on salvestatud ühte muutujasse.



* Programm alustab “porgandi otsimise” olekus, kus robot keerleb vastupäeva, kuni tema pildi vasakusse serva tekib porgand.
* Seejärel läheb robot “porgandile lähenemise” olekusse, kus ta keerab leitud porgandi oma ekraani keskele ja sõidab porgandi poole.
* Kui robot saab aga oranži laigu suuruse järgi aru, et on porgandile piisavalt lähedal, siis läheb robot uuesti “porgandi otsimise” olekusse. See tähendab, et nüüd hakkab ta porgandit ekraani keskel ignoreerima ja otsib jälle uut porgandit ekraani vasakus servas. Kuna robot pöörab vastupäeva, siis lubab see tal leida justnimelt uue porgandi, mitte selle, mis tal juba ekraani keskel näha on.



Niimoodi pendeldab roboti kood kahe oleku vahet.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/kuvatommis_2022-10-26_19-28-48.png)



 







