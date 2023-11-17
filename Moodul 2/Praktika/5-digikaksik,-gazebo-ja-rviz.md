



 5. Digikaksik, Gazebo ja RViz
===============================











> 
> 
> **Robotit katsetades on mugav, kui mõningaid teste saab teha arvutis ilma füüsilise robotita. Selleks on robotitel mõnikord olemas digikaksikud: digitaalsed versioonid, mida saab kasutada arvutis ja mis proovivad jäljendada robotit päris maailmas.**
> 
> 
> 
> 
>  Harjutuse läbimiseks on vaja Ubuntu ja ROSiga arvutit, kuhu on paigaldatud kimbud robotont\_description, robotont\_driver, robotont\_gazebo ja robotont\_msgs.
>  
> 
> 
> 
> **Harjutuse läbimiseks ei tohi kasutada füüsilist robotit.**
> 
> 
> 
> 
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



 Vaatame kaht viisi, kuidas robotonti simuleerida: 3D füüsikasimulaatori Gazebo abil ja vähem ressursse koormava fake\_driver ja RVizi visualiseerija abil.




**Kui edaspidises töös ei ole just mingil põhjusel konkreetselt vaja kasutada Gazebot, siis sageli piisab RVizi ja fake\_driver abil tehtud simulatsioonist.** See hoiab kokku jõudlust.




### [**Robotont ja Gazebo**](#)

**Gazebo** on 3D füüsikasimulaator, mida kasutatakse sageli koos ROSiga. Käivitame selle koos robotondi digikaksikuga:




```
roslaunch robotont_gazebo gazebo.launch
```


 Pärast mõningast ootamist avaneb füüsikasimulaator, kus on ka robotondi robot. Seda saab kasutada täpselt samamoodi nagu füüsilist robotit. Võid proovida selles keskkonnas ringi sõita, avades uue terminaliakna ja kasutades käsku




```
roslaunch robotont_demos teleop_keyboard.launch
```


> 
> #### 
>  Pea meeles!
> 
> 
> 
>  Selleks, et robotonti klaviatuurilt liigutada, peab olema aktiivne terminaliaken, kus käivitasid teleop\_keyboard.launch käivitusfaili!
>  
> 
> 
> 



 Kahjuks nõuab Gazebo aga arvutilt päris palju jõudlust ja sellepärast pole selle kasutamine alati mõttekas. **Sulge Gazebo praeguseks.**









### [**Robotont ja RViz**](#)

Mõnikord ei ole aga vaja tervet füüsikasimulaatorit, et näha, kuidas robot liigub. Võime kasutada hoopis palju vähem jõudust nõudvat meetodit. Sisesta järgmine käsk:




```
roslaunch robotont_driver fake_driver.launch
```


 Nüüd avaneb tööriista **RViz** aken, kus näeme jälle robotit. Ka seda robotit on võimalik kasutada sarnaselt füüsilisele robotile.




 Kuidas erineb see Gazebost? RViz **ei ole** füüsikasimulaator, vaid visualiseerimistööriist - see aitab asju näidata, aga ta ei proovi maailma simuleerida. Selle asemel käib praegu taustal väga lihtne koodijupp, mis ei ole RViziga üldse seotud ja mille nimi on fake\_driver. See koodijupp teeb väga lihtsat tööd: kuulab, mis liikumiskäske saadetakse robotile, ja ütleb vastu, et robot on just täpselt nii palju liikunud, nagu taheti. Seejärel saab RViz seda visualiseerida. See tähendab ka, et kogu süsteemis ei ole läbimatuid seinasid, hõõrdejõudu ega paljusid muid asju, mis meie füüsilises maailmas olemas on.




 Selleks, et näeksime robotit ringi sõitmas, peame RVizi veidi seadistama.




 RVizi aknas on vasakul paneelil seaded, mille hulgas "Fixed Frame". Määra selle väärtuseks odom (kui väärtuseks on juba odom, siis on kõik hästi). Samuti määra "Frame Rate" väärtuseks 10 - siis on süsteem kiirem.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/kuvatommis_2022-10-03_14-53-34.png)




 Nüüd saad (jällegi uues terminaliaknas) käivitada roboti klaviatuurilt juhtimise programmi ja seda ringi liigutada:




```
roslaunch robotont_demos teleop_keyboard.launch
```


> 
> #### 
>  Pea meeles!
> 
> 
> 
>  Selleks, et robotonti klaviatuurilt liigutada, peab olema aktiivne terminaliaken, kus käivitasid teleop\_keyboard.launch käivitusfaili!
>  
> 
> 
> 







 


