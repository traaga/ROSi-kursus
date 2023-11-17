



 9. Manipulaatorroboti URDF kirjeldus
======================================











> 
> 
> **Praeguseks oleme juba teinud URDFis neljarattalise roboti mudeli. Samuti oleme tutvunud kinemaatika põhitõdedega ja erinevate liigenditüüpidega. Nüüd on aeg panna kokku neis peatükkides omandatud oskused ja teadmised ning teha ise valmis nn manipulaatorroboti URDF mudel.**
> 
> 
> 
> 
> *Samm-sammulise juhendi nägemiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



Järgnevalt loome URDFi kasutades sellise roboti kirjelduse:




![.](https://sisu.ut.ee/sites/default/files/rosak/files/1_end_goal.gif)




### [**1. Ettevalmistused**](#)

Alustuseks paigaldadame ROSi kimbu aironbot\_description, mis sisaldab 3D-mudeleid roboti lülidest. Mudeli failid asuvad kaustas aironbot\_description/meshes




Kimbu paigaldamiseks **liigu terminalis kausta** ~/catkin\_ws/src ja klooni sinna **kimbu lähtekood**:




```
git clone https://github.com/unitartu-edu/aironbot_description.git
```


 Seejärel **kompileeri** ja **laadi** uuesti catkini tööruum.




![](https://sisu.ut.ee/sites/default/files/rosak/files/2_setup.gif)









### [**2. Lihtsa manipulaatori visualiseerimine**](#)

Kimbus aironbot\_description on juba olemas ühe väga lihtsa manipulaatori URDF kirjeldus. Visualiseerime selle roboti mudeli:




**a.** Liigu terminalis kausta catkin\_ws/src/aironbot\_description/urdf/




**b.** Käivita RViz järgneva käsuga:




```
roslaunch urdf\_tutorial display.launch model:=aironbot.urdf
```


Pane tähele, et see on sama käsk, millega olema ka varem mudeleid visualiseerinud. Ainus erinevus seisneb käivitatava mudeli failinimes.




**c.** Avaneb kaks akent. Suuremas aknas näeme roboti kolmemõõtmelist visualiseeringut. Väiksemas aknas näeme liugurit, mis liigutab roboti ühte liigendit.




**d.** Proovi erinevaid liuguri väärtusi ja jälgi, mis mõju see roboti mudelile avaldab.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/3_manip_two_links.gif)









### [**3. Mudeliga tutvumine**](#)

Nähtud manipulaatori mudel on kirjeldatud URDF failis, mis asub aironbot\_description/urdf kataloogis. Ava see fail ja vaata, kuidas on see robot kinemaatiliselt kirjeldatud.




Suurem osa failist kirjeldab roboti põhja (base\_link), esimest lüli (link\_1) ja liigendit nende kahe lüli vahel.




Järgnevalt on toodud roboti põhja ja esimest lüli kirjeldavad joonised. Kõik mõõtmed joonistel on meetrites.




Roboti põhja geomeetria ja mõõtmed:  
![.](https://sisu.ut.ee/sites/default/files/rosak/files/4_base_link.png)




Roboti esimese lüli geomeetria ja mõõtmed:  
![.](https://sisu.ut.ee/sites/default/files/rosak/files/5_manipulator_link.png)









### [**4. Mudeli täiendamine**](#)

Muuda nüüd URDF faili selliselt, et robotil oleks veel üks lüli (paneme sellele nimeks link\_2). See lüli on täpselt sama geomeetriaga nagu link\_1.




Loo liigend, mis seob 2. lüli pöördliigendiga 1. lüli tipu külge.




Peale muudatuste tegemist visualiseeri robot, et veenduda, et kõik sai õigesti. Hetkel võiks tulemus olla selline:  
![.](https://sisu.ut.ee/sites/default/files/rosak/files/6_two_links.png)




> 
> #### 
>  Kui läks valesti
> 
> 
> 
>  Tagasi algseisu saamiseks otsi lähtekoodi aironboti GitHubi repositooriumist: <https://github.com/unitartu-edu/aironbot_description>
> 
> 
> 
> 








### [**5. Rohkemate lülide lisamine**](#)

Meie manipulaator ei ulatu veel eriti kaugele. Lisa sellele veel kaks lüli: link\_3 ja link\_4, mis on sama geomeetriaga nagu juba olemasolevad lülid.




Tulemus peaks olema sarnane järgneva pildiga.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/7_four_links.png)









### [**6. Haaratsi lisamine**](#)

Meie manipulaator ulatub juba üsna kaugele, aga praegu ei saa see veel asjadest kinni võtta. Enamasti paikneb manipulaatorrobotite otsas mõni tööriist, nt haarats.




Lisame oma mudelile haaratsi. See on samuti füüsiline lüli nagu kõik eelnevad, aga see on teistsuguse geomeetriaga. Haaratsi geomeetria on kirjeldatud gripper.stl failis, mis asub aironbot\_description/meshes kataloogis.




Haaratsi lisamisel pane tähele, et seda lüli on vaja pöörata, et see sobituks 4. lüli tipuga. Kasuta haaratsi pööramiseks rpy (*roll, pitch, yaw*) väärtusi.




Haarats näeb välja selline:  
![.](https://sisu.ut.ee/sites/default/files/rosak/files/8_gripper.png)




Peale haaratsi lisamist peaks tulemus sarnanema järgnevaga:




![.](https://sisu.ut.ee/sites/default/files/rosak/files/9_robot_with_gripper.png)




![.](https://sisu.ut.ee/sites/default/files/rosak/files/10_robot_with_gripper.png)






