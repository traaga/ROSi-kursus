



 6. Keskkonna kaardistamine
============================











> 
> 
> **Selles harjutuses proovime robotit ümbritsevat keskkonda kaardistada.**
> 
> 
> 
> 
>  Harjutust saab läbida nii simulaatoris kui ka päris robotiga. Soovitatav on proovida mõlemat.
>  
> 
> 
> 
> *Harjutuse läbimiseks klikka vahepealkirjadele.*
> 
> 
> 
> 



### [**Soovituslik: kimbu loomine**](#)

Keskkonna kaardistamise harjutuse lõpuks tekib meile **kaart**, mille järgi saame hiljem roboti autonoomselt navigeerima panna. See kaart tuleb hiljem kusagile salvestada. Lisaks sellele võib tekkida soov mooduli lõpupoole kõik vajalikud käsud panna eraldi käivitusfaili - siis ei pea neid ükshaaval tööle panema. Selle kõige jaoks on kasulik endale luua üks uus kimp.




 Uuele kimbule ei pea me praegu lisama ühtegi sõltuvust teistest kimpudest. Seega käib selle loomine catkini töölaua src-kaustas olles tavapärasel viisil ja väga lihtsalt (kus kimbule võib anda endale sobiva nime):




```
catkin create pkg uue_kimbu_nimi
```







### [**Ainult simulaatoris: Gazebo ja maailm, mida kaardistada**](#)

Päris roboti peal harjutust sooritades jäta see alapunkt vahele.




 Simulaatoris alustame sellest, et avame maailma, mida soovime kaardistada.




 Kuna kasutame simulaatorit, siis on meil luksus kasutada kaardistamiseks just sellist sensorit, nagu ise soovime. Valime selleks **lidari.** Selleks kasutame robotondi mudelit nimega robotont\_gazebo\_lidar, kus meie tuttavale robotondile on peale asetatud Hokuyo lidar. Lisaks sellele avame Gazebo maailma, kus on väike labürint, milles robotont ringi liikuda saab. Käsk selle kõige jaoks on järgmine:




```
roslaunch robotont_gazebo world_minimaze.launch model:=robotont_gazebo_lidar
```







### [**SLAMi sõlm**](#)

See ja järgmised sammud on samad nii päris roboti kui ka simulaatori jaoks.




 SLAMi algoritmid võivad olla päris keerulised. ROS lubab meil aga kasutada nii mõndagi neist nii, et me ei pea neid ise implementeerima.




 Näiteks võime kasutada algoritmi nimega **gmapping**. Kui huvitab, mis seal sees toimub, siis võid selle kohta [inglise keeles rohkem lugeda siit](https://openslam-org.github.io/gmapping.html).




 Simulaatoris:
---------------



 Käivita järgmine käivitusfail, mis paneb jooksma gmapping algoritmi:




```
roslaunch robotont_demos gmapping.launch
```


 Päris robotil:
----------------



 Käivita järgmine käivitusfail, mis paneb jooksma nii gmapping algoritmi kui ka loob robotondile võlts-lidari:




```
roslaunch robotont_demos 2d_slam_create_map.launch
```


> 
> #### 
>  Kas päris robotondil on lidar?
> 
> 
> 
>  Võisid tähele panna, et gmapping tugineb lidari andmetele. Meie päris robotondil pole aga lidarit - selle asemel on tal sügavuskaamera. Kuidas süsteem sellega toime tuleb?
>  
> 
> 
> 
>  Robotont saab kasutada ROSi kimpu nimega depthimage\_to\_laserscan, kus on sõlm, mis teeskleb sügavuskaamera info põhjal, et ta robot saab andmeid lidari käest. Sisuliselt teeskleb see, et meil on lidari andmed, kuigi tegelikult ei ole.
>  
> 
> 
> 
>  See ei ole päris sama hea, mis lidari enda kasutamine, sest depthimage\_to\_laserscan viskab minema palju lidari poolt saadud andmeid ja allesjääv info ei ole päris sama täpne nagu lidari käest saadud info. Kuigi nii sügavuskaamera kui ka lidar on mõlemad head sensorid, siis on nad head natuke erinevate asjade jaoks ja ei suuda üksteist päriselt asendada. Meie jaoks on see praegu aga piisav.
>  
> 
> 
> 








### [**Kaardi kuvamine**](#)

Tore oleks näha, missugust kaarti robotont seni on suutnud joonistada. Seda saame teha RViz abil. Üks viis seda teha on avada RViz ja seal seaded paika tuunida, kuid kuna me ei ole RVizi seadistamist eriti õppinud, siis läheme lihtsama vastupanu teed ja kasutame käivitusfaili, mis avab RVizi juba valmistehtud konfiguratsioonifailiga ja kuvab just õiget infot.




```
roslaunch robotont_demos 2d_slam_display.launch
```


 Näed pilti, mis sarnaneb allolevale. Saad liigutada vaatenurka vasaku hiireklahviga pildil lohistades, rullikuga sisse ja välja liikuda ning vasakut hiireklahvi ja shift-klahvi samaaegselt all hoides (või lihtsalt hiire rullikut all hoides) hiirt liigutades viia vaadet paremale-vasakule ning üles-alla.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/kuvatommis_2022-10-31_12-58-58.png)









### [**Ringisõitmine ja kaardistamine**](#)

Nüüd, kui meil on kõik üles seatud, on meil vaja päriselt ala ära kaardistada. Seda on kõige lihtsam teha, hoides lahti RVizi akent ja juhtides robotonti klaviatuurilt. Võid vaadata ka Gazebo akent, kuid RVizi kaardikuvamine annab meile praegu paremini teada, kus robot juba käinud on ja missuguse nurga tagant ruum veel uurimata on.




> 
> #### 
>  Ettevaatust
> 
> 
> 
>  Päris roboti peal harjutust sooritades pea meeles, et meie sügavuskaamera põhjal tehtud liba-lidar ei ole just ideaalne. Sõida ringi rahulikul kiirusel.
>  
> 
> 
> 



 Oma eelnevaid teadmisi kasutades käivita roboti klaviatuurilt juhtimine ja sõida sellega ringi, kuni oled kaardiga rahul.









### [**Kaardi salvestamine**](#)

Kui oled loonud kaardi, siis viimane ülesanne on see kusagile salvestada, et saaksime seda hiljem kasutada.




 Esimese asjana navigeeri terminalis kausta, kuhu soovid uue kaardi salvestada. Võid näiteks selle tarvis eelnevalt loodud uue kimbu sees teha kausta nimega maps ja terminaliga sinna navigeerida.




 Nüüd salvestame kaardi. Selleks kasutame sõlme map\_saver kimbust map\_server ja anname talle lisaks argumendina ka failinime, kuhu soovime kaarti salvestada. Kaardi nime võid ise vabalt valida.




```
rosrun map_server map_saver -f minu_kaardi_nimi
```


 Nüüd võid käimasolevad sõlmed sulgeda.






