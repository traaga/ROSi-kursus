



 8. Rubriigi nime muutmine
===========================











> 
> 
>  Nüüdseks teame, et saame käivitada erinevaid ROSi **sõlmesid** või **käivitusfaile**, mida leiame olemasolevatest **kimpudest**.
>  
> 
> 
> 
>  Mis aga siis, kui meil on olemas kaks sõlme, millest üks oskab õigeid **sõnumeid** **kuulutada** ja teine neid **tellida**, aga **rubriik**, milles esimene sõnumeid kuulutab, **ei ole sama**, mis see, kus teine neid tellida soovib?
>  
> 
> 
> 
>  Selle probleemi lahendamiseks saame sõlmesid käivitades rubriikide **nimesid muuta**.
>  
> 
> 
> 
>  Harjutuse sooritamiseks on vaja ligipääsu Ubuntu ja ROSiga arvutile, kuhu on paigaldatud kimbud teleop\_twist\_keyboard ja turtlesim. Kui kasutad kursuse korraldajate poolt pakutud süsteemi, siis on need kimbud juba paigaldatud.
>  
> 
> 
> 
> **Harjutus ei ole mõeldud läbimiseks füüsilise robotiga.**
> 
> 
> 
> 
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



### [**1. Sobimatute rubriikide ülesseadmine**](#)

Alustame kahe ROSi sõlme käivitamisest.




 Kõigepealt tee kindlaks, et ühes terminaliaknas on käivitatud ROSi tuum:




```
roscore
```


 Siis ava veel kolm terminaliakent.




 Ühes käivita juba tuntud teleop\_twist\_keyboard.py sõlm kimbust teleop\_twist\_keyboard:




```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```


 Teises käivita sõlm nimega turtlesim\_node kimbust turtlesim:




```
rosrun turtlesim turtlesim_node
```


 Avaneb aken, kus on pealtvaates näha väikest kilpkonnakujutist.




 Kolmandas kasuta tööriista rosnode, et näha, mis rubriikidel kuulutatakse ja mida tellitakse:




```
rosnode list
rosnode info /teleop_twist_keyboard
rosnode info /turtlesim
```


 Uuri nende käskude väljundit. Näed seal, et teleop\_twist\_keyboard kuulutab rubriigis /cmd\_vel (see on kirjas teise käsu väljundi "Publications" osas), aga turtlesim tellib rubriiki /turtle1/cmd\_vel (see on kirjas kolmanda käsu väljundi "Subscriptions" osas).









### [**2. Tellija käivitamine**](#)

Peata sõlme turtlesim töö kasutades klahvikombinatsiooni Ctrl+C, kuid jäta teleop\_twist\_keyboard tööle.




 Käivitame sõlme turtlesim uuesti, kuid seekord ütleme talle, et soovime, et ta kasutaks rubriigi turtle1/cmd\_vel asemel rubriiki cmd\_vel. Seda saame teha, lisades käsu lõppu turtle1/cmd\_vel:=cmd\_vel:




```
rosrun turtlesim turtlesim_node turtle1/cmd_vel:=cmd_vel
```


 Proovi nüüd aktiveerida terminaliaken, kus jookseb teleop\_twist\_keyboard sõlm, ja sealt juhtida kilpkonna.




 Niimoodi **nimetasime rubriigi ümber**. Seda saab kõigi käskude puhul alati teha ühtmoodi: tuleb käsule lisada :=-ga eraldatult rubriigi nimi, mida sõlm vaikimisi kasutab, ja rubriigi nimi, mida soovime, et ta kasutaks.









### [**3. Kuulutaja käivitamine**](#)

Eelmises sammus panime tellija tellima teistsugust rubriiki. Saame tegelikult sama teha ka kuulutajaga.




 Peata nii sõlme turtlesim kui ka sõlme teleop\_twist\_keyboard töö, vajutades vastavates terminaliaknates klahvikombinatsiooni Ctrl+C ajal, mil nad on aktiivsed.




 Nüüd käivita turtlesim uuesti samamoodi, nagu esimeses sammus, ilma rubriike ümber nimetamata:




```
rosrun turtlesim turtlesim_node
```


 Seejärel käivita teleop\_twist\_keyboard, muutes rubriigi cmd\_vel nime:




```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py cmd_vel:=turtle1/cmd_vel
```


 Nüüd saad proovida uuesti kilpkonna liigutada - seda saab jälle teha. Kui vaatad rostopic info /turtle1/cmd\_vel käsuga selle rubriigi kuulutajaid ja tellijaid, siis näed, et üks sõlm kuulutab sellesse rubriiki ja teine tellib.








 
