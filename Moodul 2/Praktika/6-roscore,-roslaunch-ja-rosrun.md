



 6. Roscore, roslaunch ja rosrun
=================================











> 
> 
> **ROSis on vajalike protsesside käivitamiseks kaks sarnast käsku: rosrun ja roslaunch. Mis on nende erinevus ja kuidas neid kasutada? Mida teeb käsk roscore?**
> 
> 
> 
> 
>  Selle harjutuse läbimiseks on vaja Ubuntu ja ROSiga arvutit ning kimpe teleop\_twist\_keyboard, robotont\_demos, robotont\_driver, robotont\_description ja robotont\_msgs.
>  
> 
> 
> 
> **See harjutus on mõeldud läbimiseks ilma füüsilise robotita.**
> 
> 
> 
> 
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



### [roscore](#)

Igas ROSi süsteemis peab ühes kohas jooksma **tuum**.




 Kui kasutad **füüsilist robotondi robotit**, siis käivitatakse tuum vaikimisi robotondi robotil.




 Kui sa ei kasuta füüsilist robotondi robotit, siis saad tuuma käivitada soovitud arvutis järgmise käsuga:




```
roscore
```


 See käsk paneb tuuma tööle. **Kui sisestad selles aknas käsu Ctrl+C, siis tuuma töö lõppeb.** Seega kui soovid, et tuum töötaks, siis jäta see antud terminaliaknas tööle ja uute käskude sisestamiseks võta lahti uusi terminaliaknaid.









### [rosrun](#)

ROSi sõlmede käivitamiseks saab kasutada käsku rosrun.




 Käsu rosrun käivitamiseks on vaja, et kusagil oleks käima pandud tuum.




 Selle käsu süntaks on järgmine:




```
rosrun kimbu_nimi sõlme_faili_nimi
```


 Proovi käivitada sõlme teleop\_twist\_keyboard.py kimbust teleop\_twist\_keyboard nõnda, et roscore on teises terminaliaknas käivitatud, ja ka nii, et see on peatatud. Käsk sõlme käivitamiseks on järgmine:




```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```


 Saad erinevad veateated: ühel juhul kurdab programm, et keegi ei telli rubriigist cmd\_vel sõnumeid, teisel juhul aga, et programm ei saa üldse ühendust tuumaga.









### [roslaunch](#)

ROSi sõlmi on võimalik käivitada ka osana käivitusfailist. Käivitusfailiga saab teha ka palju muud ja selle kohta õpime rohkem tulevatel nädalatel.




 Käsu roslaunch kasutamise süntaks on järgmine:




```
roslaunch kimbu_nimi käivitusfaili_nimi
```


 Vaatame käivitusfaili teleop\_keyboard.launch kimbust robotont\_demos. Selle sisu on järgmine:




```
<?xml version="1.0" ?>
<launch>
  <node pkg="teleop_twist_keyboard" name="teleop_twist_keyboard" type="teleop_twist_keyboard.py" output="screen">
    <param name='~speed' value="0.1" />
    <param name='~turn' value="0.3" />
  </node>
</launch>
```


 See käivitusfail käivitab ainult ühe sõlme, mis on teleop\_twist\_keyboard.py kimbust teleop\_twist\_keyboard - seesama sõlm, mida käivitasime eelmises sammus. Lisaks määratakse selle käivitusfailiga kiiruseparameetrid, mis erinevad teleop\_twist\_keyboard.py vaikeväärtustest.




 Pane aga tähele, et käsk roslaunch **ei eelda**, et kusagil on juba käima pandud ROSi tuum (roscore). Kui tuum kusagil ei käi, siis roslaunch käivitab selle ise. Sellegipoolest võib mõnikord olla kasulik tuum ise käivitada.




 Katseta käivitusfaili käivitamist järgmise käsuga:




```
roslaunch robotont_demos teleop_keyboard.launch
```


 Pane tähele, et ei saa kummalgi juhul veateadet, mis ütleks, et tuumaga ei saa ühendust, vaid mõlemal juhul öeldakse, et rubriigil cmd\_vel ei ole tellijaid.




> 
> #### 
>  Mis vahe on rosrun ja roslaunch käskudel?
> 
> 
> 
> roslaunch käsk on mõeldud käivitusfailide ehk launch-faililaiendiga failide jaoks. Sellega saab käivitada korraga nii ühe kui ka mitu sõlme - see oleneb käivitusfaili sisust.
>  
> 
> 
> 
> rosrun käsk aga on mõeldud ühe sõlme käivitamiseks. Kui see sõlm on kirjutatud Pythonis, siis antakse sellele käsule argumentideks kimbu nimi ja Pythoni faili nimi, kui aga C++-is, siis kimbu nimi ja C++ lähtekoodist kompileeritud binaari nimi.
>  
> 
> 
> 







 
