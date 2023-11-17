



 1. Lülid, liigendid ja kinemaatiline ahel
===========================================











> 
> 
> **Järgnevalt õpime, kuidas paljusid roboteid lihtsasti kirjeldada ja mis on kinemaatiline ahel.**
> 
> 
> 
> 
> *Õppematerjali vaatamiseks klikka vahepealkirjadele.*
> 
> 
> 
> 



### [**1. Robotite lihtsustamine**](#)

Maailmas leidub väga palju erinevaid roboteid. Paljusid neist on võimalik kirjeldada üsna lihtsalt ja primitiivselt.




**Robot koosneb portsust lülidest (ingl link), mis on ühendatud liigendite (joint) abil.**




Lülid on defineeritud kui paindumatud osad, mis moodustavad roboti. Neil on inerts, visuaalne omapära, ja need võivad muude asjadega kokku põrgata.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/kinematics_joined_franka_diagram_b7928ba7479e9e411cfbe7ae8529fd0e.jpg)Foto kohandatud allikast: https://commons.wikimedia.org/wiki/File:Franka\_Emika2.jpg, CC BY-SA 4.0 litsensi all









### [**2. Liigendid**](#)

Liigendid ühendavad lülisid. Või abstraktsemalt: liigend määrab, kuidas on lüli liikumine referentsiks oleva koordinaatsüsteemi suhtes piiratud. Seega määravad liigendid lõpuks, kuidas robot saab liikuda.




Liigendite klassifitseerimiseks on mitmeid eri viise. Järgnevalt tutvume erinevate ühe või mitme vabadusastmega (*degrees of freedom*) liigenditega.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/kinetics_joints_on_abstract_franka_5166161ad43c6c265c5e34e097377db3.png)









### [**3. Ühe vabadusastmega liigendid**](#)

Siin näed erinevaid liigendeid, millel on **üks vabadusaste**: nad saavad liikuda ainult ühel viisil või ühes suunas. Nendes näidetes ühendab liigend sinist lüli ja rohelist lüli.




*Klikka video peale, et vaadata, kuidas liigend liigub.*




**Pöördliigend** saab pöörelda ümber ühe telje.  





**Translatsioonipaari** korral on üks detail fikseeritud ning teine saab libiseda ühes teljes.  





**Kruviliigend** koosneb keermelatist, mis liigub edasi-tagasi ühes teljes.  










### [**4. Mitme vabadusastmega liigendid**](#)

MItme vabadusastmega liigendid saavad liikuda sõltumatult vähemalt kahes teljes või telje ümber. Allpool näed näiteid neist.




*Klikka video peale, et vaadata, kuidas liigend liigub.*




**Silindriline liigend** on kombinatsioon pöörd- ja translatsiooni liigenditest. See võimaldab ühes teljes nii pöörlemist kui ka libisemist. Kokku on sellisel liigendil kaks vabadusastet.  





**Kuuli ja sokli liigend** koosnebki kuulist, mis saab sokli sees pöörelda. See annab kolm vabadusastet.  





**Tasapinnaline liigend** võimaldab liikumist ühel tasandil, aga mitte väljaspool seda tasandit. Sellisel liigendil on kolm vabadusastet.  





**Hõljuv liigend** ei ole füüsiline liigend, aga tuleb kasuks, kui on tarvis kirjeldada kahte lüli, mis ei ole füüsiliselt üksteisega ühendatud. Näiteks on see kasulik, et kirjeldada lendava roboti paiknemist teatud punkti suhtes. Sellisel liigendil on liikumisvabadus igas suunas ehk kuus vabadusastet.  










### [**5. Jadamanipulaatorid**](#)

Järjestikused üksteisega ühendatud lülid ja liigendid moodustavad **kinemaatilise ahela** (ingl k. *kinematic chain*). Üks kinemaatilise ahela vormidest on **jadamanipulaator** (ingl k. *serial manipulator*): lülid, mis on omavahel ühendatud pöördliigenditega. Näideteks on robotkäed, tööstusrobotid ja koostöörobotid.




 Selle lüliahela algus on tavaliselt kuhugi fikseeritud. Ahela lõpp on roboti mõjur (ingl k. *end effector*). See peab tihti asjadest kinni võtma nagu haarats.




 Üks pöördliigend annab ühe vabadusastme, seega kuue strateegiliselt paigutatud pöördliigendi abil saavutame kõigi kuue vabadusastmega roboti.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/franka_emika_from_wikimedia_fca5a3a5627c5e8581ca3a6070f37501.jpg)Foto allikas: https://commons.wikimedia.org/wiki/File:Franka\_Emika2.jpg, litsents: CC BY-SA 4.0  




