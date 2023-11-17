



 11. Linuxi terminal: programmid
=================================











> 
> 
> **Selles harjutuses õpid käivitama käsurealt programme, neid peatama, programme käivitama taustal, viima taustale ja sealt tagasi tooma. Valikulises osas õpid programme peatama ka siis, kui nad tööd lõpetada ei taha, leidma protsessi ID-d, kuvama protsessori- ja mälukasutust ja saad teada, mida teeb käsk sudo. Harjutus eeldab, et oled läbinud Linuxi terminali navigatsiooniharjutuse ja failide muutmise harjutuse.**  
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



### [**1. Programmid: käivitamine ja peatamine**](#)






 Alustamiseks peaksid terminaliga olema kaustas linux\_intro, mis sai loodud terminali navigatsiooniharjutuses.




**a. Sisesta käsk ./sample\_job.** See käivitab kataloogis oleva programmi sample\_job.**b. Vajuta Ctrl+C.** See klahvikombinatsioon peatab terminalis suurema osa programme - jäta see meelde ja kasuta vajadusel.









### [**2. Programmid: teksti redigeerimine**](#)






**a. Sisesta terminali käsk gedit test.txt.**  
Näed, et avatakse tekstiredaktori aken, kus saad muuta faili test.txt sisu. See on enne õpitutele lisaks veel üks moodus tekstiredaktori avamiseks.  
Sellesse terminaliaknasse aga enne tekstiredaktori sulgemist uusi käske sisestada ei saa. Sulge tekstiredaktori aken.




**b.** Proovime programmi gedit terminalist avada teisiti. **Sisesta käsk gedit test.txt &.**  
See viimane &-märk ütleb terminalile, et käsku tuleb jooksutada “taustal”, st näeme kohe ka uuesti käsuviipa ja saame sisestada uusi käske.




**c. Sulge tekstiredaktori aken ja sisesta siis terminali käsk ls.**  
Lisaks failinimekirja näitamisele ütleb terminal Sulle ka, et programm gedit on vahepeal töö lõpetanud.




**d. Ava nüüd tekstiredaktor uuesti käsuga gedit test.txt.**  
Tekstiredaktor avaneb uuesti ja terminali kontrollides näeme, et uut käsuviipa ei kuvatud.




**e. Tee see terminaliaken uuesti aktiivseks ja vajuta klahvikombinatsiooni Ctrl+Z.**  
Terminal annab Sulle teada, et gedit on peatatud. Näed uut käsuviipa.




**f. Proovi lahtiolevat tekstiredaktori akent kasutada – näed, et ei saa seda teha.**




**g. Trüki terminali käsk bg. See teeb tekstiredaktori jälle aktiivseks.**




**h. Sulge tekstiredaktori aken.**





---



### [**Valikuline sisu. Programmid: kontrollimatute programmide peatamine**](#)

  
Siintoodud materjalide läbimine ei ole kohustuslik, kuid kui teema huvitab, siis võid ka neid proovida.




 Käivitame programmi, mida lihtsalt Ctrl+C kasutamisega peatada ei saa, ja siis peatame selle teiste meetoditega.




**a. Liigu kausta linux\_intro.**




**b. Sisesta käsk ./sample\_job sigterm.** See käivitab näidisprogrammi uuesti, kuid veidi teistmoodi.




**c. Vajuta uuesti Ctrl+C.** Näed, et seekord programmi töö ei peatu.




**d. Ava uus terminaliaken.**




**e. Sisesta käsk ps ax.**




**f. Liigu aknas ülespoole, kuni leiad käsu python ./sample\_job sigterm.** See on esimeses aknas jooksev programm, mis peatuda ei taha. Antud tabelirea esimene väli on protsessi ID – seda on meil vaja.




**g. Nüüd kasuta hoopis käsku ps ax | grep sample.**  
Näed, et nüüd loetletakse sulle ainult mõned read (kõik, mis sisaldavad sõna “sample”). See on kasulik juhul, kui otsid mõnd kindlat programmi, nagu meie praegu.




**h. Sisesta käsk kill <id>,** kus <id> asemele (ilma nurksulgudeta) kirjutad eelnevalt leitud protsessi ID.




**i. Vaata terminaliaknasse, kus jooksis jonnakas programm, mis peatuda ei soovinud.** Selle töö on nüüd lõpetatud.




**j.** Teeme olukorra veel keerulisemaks. **Käivita jonnakas programm uuesti, seekord käsuga ./sample\_job sigterm sigkill.**




**k. Proovi teisest aknast programmi uuesti peatada, leides protsessi ID käsuga ps ax | grep sample ja proovides seejärel käsuga kill seda peatada, nagu enne.** Näed, et see ei tööta enam.




**l.** Täiendame peatamiskäsku veidi: **sisesta kill -SIGKILL <id>, kus <id> on, nagu ennegi, asendatud protsessi ID-ga.** Selle peale peaks programm ikkagi peatuma.









### [**Valikuline sisu. Programmid: protsessori- ja mälukasutus**](#)






**a. Sisesta terminali käsk top.**  
Näed tabelit, mida uuendatakse kord sekundis ja mis näitab kõiki aktiivseid protsesse. Lisaks näidatakse ka üldist CPU ja mälukasutust.




**b. Vajuta klahvikombinatsiooni Shift+P.**  
See sorteerib protsessid CPU kasutuse järgi ja näitab, missugused kasutavad seda enim.




**c. Vajuta klahvikombinatsiooni Shift+M.**  
See sorteerib protsessid mälukasutuse järgi ja näitab, missugused kasutavad seda enim.




**d. Väljumiseks vajuta klahvi q või klahvikombinatsiooni Ctrl+C.**









### [**Valikuline sisu. Programmid: käskude käivitamine juurkasutajana**](#)






**a. Trüki terminali käsk ls -a /root.**  
Terminal annab Sulle teada, et ta ei suuda selle sisu kuvada.  
Selleks on meil vaja rohkem õiguseid: täpsemini juurkasutaja õiguseid.




**b. Selleks, et eelmist käsku jooksutada juurkasutajana, pead käsu algusesse lisama sõna sudo.** Käsk oleks seega sudo ls -a /root. Selle peale küsib terminal parooli.  
Kui Sinu kasutajal on juurkasutaja õigused, siis saad kataloogi /root sisu näha pärast parooli sisestamist.  
Kui Sinu kasutajal juurkasutaja õiguseid ei ole, siis sa käske sõnaga sudo alustada ei saa ja proovimisel kuvatakse veateade.




> 
> #### 
>  Ettevaatust!
> 
> 
> 
> sudo on väga võimas tööriist ja ei kontrolli, kas teed midagi mõistlikku, seega peaksid selle kasutamisel olema väga ettevaatlik. Enamasti ei ole seda vaja.
> 
> 




