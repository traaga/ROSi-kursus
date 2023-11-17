



 4. Uue kimbu loomine
======================











> 
> 
> **Oleme seni kasutanud palju olemasolevaid ROSi kimpe, kuid ei ole veel proovinud luua uut. Selles harjutuses loome ise uue ROSi kimbu.**
> 
> 
> 
> 



 Uue ROSi kimbu loomiseks on olemas käsk nimega catkin create pkg. Loome selle abil endale uue kimbu, mida selles moodulis kasutama hakkame.




 Kõigepealt **navigeeri terminalis catkini tööruumi src kausta**, kuna see on õige koht kõigi kimpude lähtekoodide jaoks.




 Siis sisesta järgmine käsk:




```
catkin create pkg fourwheeler\_description --catkin-deps urdf xacro
```


 Mida see käsk teeb? See loob uue kimbu nimega fourwheeler\_description. Lisaks sellele anname teada, et uus kimp hakkab viitama kahele juba olemasolevale kimbule: urdf ja xacro. Seda, mis need täpselt on, saad teada edaspidi.




Palun veendu, et näed nüüd src-kaustas uut kausta nimega fourwheeler\_description ja selles kahte automaatselt loodud faili nimega CMakeLists.txt ja package.xml. Need kaks faili ütlevad catkini töövahendile, et tegu on ROSi kimbu, mitte lihtsalt ühe tavalise kaustaga. Kuigi võid julgelt nende failide sisse vaadata, siis ära esialgu nende sisu muuda.




**Kompileeri ja laadi catkini tööruum.**



 







