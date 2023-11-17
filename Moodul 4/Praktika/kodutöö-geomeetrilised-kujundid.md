



 Kodutöö. Geomeetrilised kujundid
==================================











> 
> 
> **Nüüd oskad kirjutada koodi, mis robotit meie soovi järgi sõitma paneb. Kasuta seda oskust, et panna robot erinevaid kujundeid joonistama!**
> 
> 
> 
> 
> *Samm-sammuliste juhiste vaatamiseks kliki harjutuse vahepealkirjadele.*
> 
> 
> 
> 



Sinu ülesandeks on panna robot **autonoomselt** (st mitte seda klaviatuurilt ise sõidutades) sõitma järgmisi trajektoore. (Iga kujund võib olla koodifail, mida eraldi käivitatakse.)




Kõigepealt testi koodi fake\_driver simulaatori abil RVizis (ressursside kokkuhoiuks mitte Gazebo abil!) ja seejärel pane kood tööle ka päris robotil.




Arvesta, et päris robot käitub fake\_driveri simulatsiooniga võrreldes oluliselt teistmoodi. Seda seepärast, et fake\_driver simulaator on väga lihtne idealistlik simulatsioon, kus robotil pole massi, ratastele ei arvestata hõõrdetegurit ega pole arvestatud ühegi muu päris maailma kitsendusega. Seega sobib fake\_driver simulaator väga hästi oma sõlme koodide üldstruktuuride paika seadmiseks ja kõikvõimalikest veateadetest jagu saamiseks. Ent kujundite läbi sõitmiseks vajalikud täpsed ajavahemikud tuleb mitmel juhul päris roboti peal uuesti üle vaadata.




### [**Ühte suunda hoidev ruut (holonoomiline)**](#)

Pane robot liikuma ruudukujuliselt, nõnda, et ta vaataks vaid ühte suunda. Ruudu ühe külje joonistamine peaks olema sujuv kogu ulatuses ja võtma aega vähemalt 2 sekundit.




Siin on video robotist, kes sõidab õiget kujundit:




![.](https://sisu.ut.ee/sites/default/files/rosak/files/sideways_square_trimmed_slow.gif)




Siin on video simuleeritud robotist:




![.](https://sisu.ut.ee/sites/default/files/rosak/files/fake_driver_simple_square.gif)




### [**Pööramisega ruut (mitteholonoomiline)**](#)

Pane robot liikuma ruudukujuliselt, nõnda, et ta liiguks alati selles suunas, kuhu vaatab ta esiots. Ruudu ühe külje joonistamine peaks olema sujuv kogu ulatuses ja võtma aega vähemalt 2 sekundit.




Siin on video robotist, kes sõidab õiget kujundit:




![.](https://sisu.ut.ee/sites/default/files/rosak/files/nose-first_square_trimmed_slow.gif)




 Siin on video simuleeritud robotist:




![.](https://sisu.ut.ee/sites/default/files/rosak/files/fake_driver_non-holonomic_square.gif)




### [Ring](#)

Pane robot liikuma ringikujuliselt. Roboti liikumine peaks olema sujuv ja ta ei tohiks vahepeal seisma jääda.




Siin on üks näide ringi joonistamisest:




![.](https://sisu.ut.ee/sites/default/files/rosak/files/circle_trimmed.gif)




 Siin on video simuleeritud robotist:




![.](https://sisu.ut.ee/sites/default/files/rosak/files/fake_driver_circle.gif)




### [Programmeerimiskogemusega osalejatele: kaheksa-sümbol](#)

Pane robot joonistama “külili kaheksat”. Roboti liikumine peaks jällegi olema mittekatkendlik ning kogu “kaheksa” joonistamine peaks aega võtma kauem kui 3 sekundit.




Siin on üks näide “kaheksa” joonistamisest:




![.](https://sisu.ut.ee/sites/default/files/rosak/files/infinity_trimmed.gif)




 Siin on video simuleeritud robotist:




![.](https://sisu.ut.ee/sites/default/files/rosak/files/fake_driver_8-shape.gif)



