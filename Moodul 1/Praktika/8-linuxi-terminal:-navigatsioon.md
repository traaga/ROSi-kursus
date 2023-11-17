



 8. Linuxi terminal: navigatsioon
==================================











> 
> 
> **Selles harjutuses õpid avama Linuxi terminali ning seal kasutama järgmiseid käske: ls, pwd, cd.**  
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



### [**1. Kataloogide vahel liikumine ja failinimekirja nägemine: ettevalmistus**](#)






**a.** Ava terminaliaken, kui see juba avatud ei ole. Tee failibrauseriga kindlaks, et kodukaustas oleks kaust nimega catkin\_ws.  
**b.** Ava terminaliaken ja sisesta sinna järgmised käsud:




```
cd catkin_ws
git clone https://github.com/ut-ims-robotics/ros_training.git ros_training
cp -a ros_training/resources/linux_intro .

```


**Iga käsu** (rea) **lõpus tuleb alati vajutada klahvi enter.**




> 
> #### 
>  Ettevaatust!
> 
> 
> 
>  Nendest kolmest käsust viimase lõpus on tühik ja siis punkt. Need kaks sümbolit on seal väga olulised - see punkt ei ole lihtsalt lauselõpumärk.
>  
> 
> 
> 



 Mida need käsud õigupoolest tegid? cd ja cp käske õpime hiljem selles peatükis. git clone käsk tõmbas alla treeningmaterjalide kausta.




> 
> 
>  Kui avad kursuse materjalide veebilehe samas Ubuntu masinas, kus teed ka harjutusi, saad soovi korral kopeerida ja kleepida antud käsud terminali (pole vaja eraldi sisse trükkida). Brauserist kopeerimiseks saad teksti valida ja kasutada klahvikombinatsiooni Ctrl+V, kuid terminalis kleepimiseks pead tavapärase asemel kasutama klahvikombinatsiooni Ctrl+Shift+V. (Sarnaselt tuleb terminalist kopeerimiseks kasutada kombinatsiooni Ctrl+Shift+C, aga seda meil hetkel veel tarvis ei lähe.)
>  
> 
> 
> 
>  Nüüd peaksid nägema catkin\_ws kaustas uut kausta nimega linux\_intro. Sellega hakkamegi edaspidi tegutsema.
>  
> 
> 
> 
> 
> 
> 





### [**2. Kataloogide vahel liikumine ja failinimekirja nägemine: käsk ls**](#)

  
Käsk ls näitab aktiivse kausta sisu (lühend sõnast “**l**i**s**t”).




**a.** Teeme kindlaks, et asume õiges kaustas. **Sisesta terminali järgmine käsk** (see liigutab sind terminalis linux\_intro kausta):




```
cd ~/catkin_ws/linux_intro

```


**b. Sisesta terminalis linux\_intro kaustas olles terminali käsk ls (kõik tähed on väiketähed).**  
Peaksid loodud nimekirjas nägema eelnevalt loodud faili test.txt ja alamkataloogi new.  
Kataloogid, nagu new, on värvitud siniseks.  
Uus fail sample\_job on roheline; see näitab, et faili saab käivitada programmina.




 Kui sa seal faile test.txt ja alamkataloogi new ei näe, siis võid eelnevalt omandatud oskuste abil need sinna ise luua.




**c. Sisesta uus käsk ls \*.txt. See näitab kõiki faile, mis lõppevad laiendiga “.txt”. Hetkel on meil kataloogis vaid üks selline fail: test.txt.**




**d. Sisesta terminali käsk ls -l. (Viimane tähemärk on väike L.)**  
Selle käsu lõppu -l lisamine asetab iga nimekirjas väljatoodud faili või kausta eraldi reale ja näitab iga rea kohta ka lisainfot.  
Esimesed 10 tähemärki näitavad faili liiki ja juurdepääsulubasid.  
Neist esimene on “d”, kui tegemist on kaustaga.  
Rea kolmas ja neljas sõna näitavad vastavalt, mis kasutaja ja kasutajategrupp on faili omanikud.  
Eelviimane väli näitab faili viimase muutmise aega.  
Kui fail on sümboolne link (umbes nagu Windowsi lühitee), siis on koht, kuhu lühitee viib, välja toodud pärast lühitee enda nime.




**e. Nüüd sisesta terminali käsk ls -a.**  
Näed lisaks üht peidetud faili (selle nimi algab punktiga) ja kaht peidetud kausta, mida failibrauserist kunagi ei näe. Nende nimed on . (üks punkt) ja .. (kaks punkti). Neist esimene tähistab hetkel aktiivset kataloogi ja teine kataloogi, mille sees aktiivne kataloog asetseb (selle “vanemat”).




**f. Sisesta nüüd käsk, mis kombineerib kaks eelmist: ls -al.**  
Nüüd peaksid nägema, et link hidden\_link.txt viitab peidetud failile .hidden\_text\_file.txt.




### [**3. Kataloogide vahel liikumine ja failinimekirja nägemine: käsud pwd ja cd**](#)

  
Käsuga pwd saab vaadata hetkel aktiivse kataloogi nime (“**p**rint **w**orking **d**irectory”) ja käsuga cd liikuda kataloogide vahel (“**c**hange **d**irectory”).




**a.** **Sisesta terminali käsk pwd.**  
See näitab sulle selle kataloogi, milles töötad, täielikku asukohta failisüsteemis. Hetkel peaks see lõppema sõnadega linux\_intro.




**b. Sisesta käsk cd new. Sellega liigud kataloogi new sisse.**  
Pane tähele, et käsuviip muutub: nüüd lõppeb see sõnaga new.  
Kui nüüd sisestad käsu pwd, siis näed, et oled vahetanud asukohta.




**c. Sisesta terminali käsk cd .. (käsu “cd” ja kahe punkti vahel on tühik).**  
Sellega liigud ühe kataloogi võrra “väljapoole”, kataloogi, mis on hetkel aktiivse kataloogi “vanem”.  
Näed, et käsuviip näitab, et oled nüüd jälle kaustas linux\_intro.




**d. Sisesta cd /bin (pööra tähelepanu tühikute paigutusele), seejärel ls.**  
See kataloog sisaldab peamisi Linuxi käsuprogramme. Pane tähele, et siin on failid nii käskude pwd kui ka ls jaoks.




**e. Sisesta cd ~ (jällegi pööra tähelepanu tühikule käsu cd ja märgi ~ vahel), et naaseda kodukataloogi.**  
Linux kasutab märki ~ lühendina kodukataloogi tähistamiseks. Seda võib kasutada ka osana teekondadest, nt “~/catkin\_ws/linux\_intro”.




**f. Liigu ühe või mitme käsuga tagasi kataloogi linux\_intro, kust alustasime.**




> 
> 
>  Kui soovid mõne käsu jaoks teada täielikku nimekirja valikutest, siis trüki terminali man <käsk>, kus <käsk> tuleb asendada käsuga, mille kohta soovid rohkem teada saada (nt man ls). See annab Sulle vastava käsu dokumentatsiooni. Üles/alla saab liikuda üles/alla klahvidega ja klahvi q vajutamine väljub vaatest.
> 
> 





### [**4. Terminali ajalugu**](#)

  
Terminalis on aeg-ajalt kasulik saada ligi eelnevalt sisestatud käskudele.




 Eelmise käsu nägemiseks vajuta "nool üles" klahvi. Näed, et käsuviiba järele ilmub viimati sisestatud käsk. Kui vajutad nüüd klahvi "enter", siis käivitatakse see käsk uuesti.




 Võid proovida ka ajaloos kaugemale tagasi liikuda. Vajuta ülemise noole klahvi mitu korda. Näed, kuidas ekraanile ilmuvad kronoloogilises järjekorras eelnevalt sisestatud käsud. Kui vajutad "nool alla" klahvi, siis liigud tagasi rohkem hiljuti sisestatud käskude poole.




Saad eelnevalt sisestatud käske ka enne uuesti käivitamist muuta, kustutades neist osa ära, trükkides neile midagi juurde või muutes käsus mõnd osa. Käsu sees liikumiseks kasuta vasakule ja paremale suunavaid nooleklahve klaviatuuril.




**Proovi veidi käsuajaloos ringi liikuda. Võid proovida ka mõningaid sisestatud käske uuesti käivitada.**



