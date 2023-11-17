



 3. ROS hajussüsteemides
=========================











> 
> 
> **ROS töötab ka hajussüsteemides - see tähendab süsteemides, kus võrku on ühendatud ja ülesandeid täidavad mitu arvutit.**
> 
> 
> 
> 



 Sageli on robotit programmeerides olukord, kus mängus on rohkem kui üks arvuti. Näiteks võib üks arvuti asuda roboti pardal ja teine olla robootiku sülearvuti. Mõnikord on vaja korraga kontrollida mitut robotit või ühele robotile vaja ligipääsu mitmel arvutil. Võib-olla tahame robotile käsklusi anda oma nutiseadmest. Kõike seda lubab ROS lihtsasti teha.




 Mitme masinaga ROS-süsteemis on üks seade, kus jookseb **ROSi tuum** ehk roscore. Kõik teised kasutatavad masinad peavad olema selle seadmega samas võrgus (näiteks samas WiFi-võrgus), nad peavad saama omavahel selles võrgus vabalt suhelda ning neile tuleb teada anda, kus asub tuum.




 Pärast seda aga ei ole enam vahet, missugusel masinal käivitatakse ROSi sõlmesid - nad saavad kõik omavahel suhelda, samadele rubriikidele kuulutada ning neilt tellida.








 







