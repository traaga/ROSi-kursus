



 Kodutöö. Autonoomne navigeerimine
===================================











> 
> 
> **Siin harjutuses õpime, kuidas kaardi abil autonoomselt navigeerida.**
> 
> 
> 
> 
> *Harjutuse läbimiseks klikka vahepealkirjadele.*
> 
> 
> 
> 



> 
> #### 
>  Liiga palju terminaliaknaid!
> 
> 
> 
>  Selles harjutuses on vaja käivitada päris palju erinevaid sõlmi eri terminaliaknates. Kui soovid, võid luua endale selle jaoks käivitusfaili, mis vastavad sõlmed käima paneb.
>  
> 
> 
> 



### [**Robot valmis**](#)

Sea valmis oma robot või simulaator. Roboti puhul on vaja, et ta oleks sisse lülitatud ja eelnevalt kaardistatud alas. Simulaatori puhul on vaja käivitada Gazebo simulatsioon, mis sisaldab eelnevalt kaardistatud ala ja robotit sobiva sensoriga.









### [**Kaardi laadimine**](#)

Nüüd on meil vaja ROSile ette anda eelnevalt loodud kaart. Liigu terminalis kausta, kuhu eelnevalt salvestasid kaardi. Tuleta meelde, mis nimega faili salvestasid sellele keskkonnale vastava kaardi, ja laadi see järgmise käsuga (kus kaardi nimi on asendatud õige nimega, nime lõpus laiend .yaml):




```
rosrun map_server map_server minu_kaardi_nimi.yaml
```







### [**Lokaliseerimine**](#)

Seekord ei ole meil vaja samaaegselt kaardistada ja lokaliseerida. Selle asemel peame tegelema lihtsalt lokaliseerimisega. Selleks kasutame meetodit nimega "adaptiivne Monte Carlo lokaliseerimine", mida võime lühendada kui amcl ja mis on keeruline nimi ühe tõenäosuspõhise asukohaleidmise meetodi jaoks.




 Selleks kasutame sõlme amcl kimbust amcl:




```
rosrun amcl amcl
```


> 
> #### 
>  Pilt virvendab?
> 
> 
> 
>  Kontrolli, ega kaardistamissõlm gmapping kimbust pole käima pandud! Nüüd, kui meil kaart juba olemas, ei ole meil enam aktiivselt kaardistamisega vaja tegeleda.
>  
> 
> 
> 








### [**Planeerimine ja navigeerimine**](#)

Rajaplaneerimine ja autonoomne navigeerimine on ROSis samuti olemas. Selleks, et neid kasutada, on meil olemas kimp nimega move\_base.




 Simulaatoris:
---------------



 Sellest kimbust sõlme käivitamiseks õigete parameetritega on käivitusfail kimbus robotont\_navigation. Sobiv käsk selle käivitamiseks on meile igati tuttaval kujul:




```
roslaunch robotont_navigation move_base.launch
```


 Päris robotil:
----------------



 Meil on vaja käivitada nii move\_base põhine rajaplaneerimine ja autonoomne navigeerimine kui ka depthimage\_to\_laserscan sõlm, mis teeskleb meie sügavuskaamera põhjal lidarit. Seda kõike teeb järgmine käivitusfail:




```
roslaunch robotont_demos 2d_slam_navigation.launch
```







### [**RViz ja navigeerimine**](#)

Nüüd avame RVizi sobiva seadistusega. Saame kasutada sama käivitusfaili, mis ennegi:




```
roslaunch robotont_demos 2d_slam_display.launch
```


 Saad vaadet seadistada samamoodi, nagu eelmiseski harjutuses: pöörata vasakut hiireklahvi all hoides ja hiirt liigutades, lähemale või kaugemale liikuda rulliku abil ja vaadet paremale-vasakule ning üles-alla liigutada kas vasakut hiireklahvi ja shift-klahvi all hoides ja hiirt liigutades või rullikut all hoides ja hiirt liigutades.




 Suure tõenäosusega ei asu robot päris seal, kuhu programm ta kaardil paigutanud on. Selleks, et asukohta korrigeerida, kasuta RVizi nuppu 2D Pose Estimate. Kliki kaardil õigel kohal (kus asub robotont), hoia hiirt all, lohista suunas, kuhu robot vaatab, ja lase siis hiireklahv lahti. Vajadusel võid seda proovida teha mitu korda.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/2d_pose_estimate.png)




 Ja nüüd oledki valmis robotil laskma autonoomselt navigeerida! Selleks kliki RVizis nupul 2D Nav Goal. Kasutamiseks kliki kohale, kuhu tahad, et robot sõidaks, ja vea hiirega suunas, kuhu tahad, et robot vaataks. Seejärel lase klahv lahti ja vaata, kuidas robot proovib sinna navigeerida.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/2d_nav_goal.png)




> 
> #### 
>  Robot sõidab halvasti ja jääb kinni
> 
> 
> 
>  Meie süsteem ei ole ideaalne. Päris roboti puhul on sensor puudulik ja robot kipub mitte teadma, mida teha seinte lähedal. Kartuses neile otsa sõita võib ta lihtsalt liikumast keelduda. Seega ära aseta sihtpunkte seintele väga lähedale.
>  
> 
> 
> 
>  Simuleeritud roboti puhul on robotil probleeme ümber nurkade liikumisega. Anna talle ruumi ja vajadusel korrigeeri soovitud asukohta.
>  
> 
> 
> 
>  Kui robot jääb ikkagi kusagile kinni ja ei suuda edasi liikuda, siis võid **uues aknas käivitada roboti klaviatuurilt juhtimise sõlme** ja teda ise sobivamasse asukohta sõidutada. Kui robotil on ümber rohkem ruumi, siis suudab ta juba ka ise edasi navigeerida.
>  
> 
> 
> 



 Lõpuks peaks süsteem töötatama umbes nii:













