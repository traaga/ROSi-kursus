



 Lisamaterjal: Euleri nurkadeks teisendamine
=============================================











> 
> 
> **Nagu varem õppisime, siis kimp ar\_track\_alvar annab meile teada orientatsiooni kvaternionina. Selleks, et seda inimmõistetaval kujul tõlgendada, teisendame kvaternioni Euleri nurkadeks.**
> 
> 
> 
> 



AR märgiste põhjal roboti positsiooni hindamine on lihtne, sest positsiooni komponentide (x, y, z) ühikuteks on meetrid. Näeme positsiooni väärtuste järgi, mitu meetrit igas teljes robot märgisest paikneb. Orientatsiooniga on natuke keerulisem.




Tuletame meelde, millised on orientatsiooni komponendid, kasutades järgnevat pilti.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/position.png)




Sarnaselt positsiooniga näeme ka orientatsiooni puhul komponente x, y, z, lisaks veel w. Vaatamata sarnasusele ei ole aga tegemist meetritega, ega isegi nurkadega kraadides. Komponendid x, y, z, w moodustavad **kvaternioni**, mis on matemaatiline konstruktsioon, mida saab kasutada nurkade kirjeldamiseks kolmemõõtmelises ruumis.




Kvaternioni komponentide põhjal roboti juhtimine on keeruline, sest nende väärtuste muutumises on raske näha inimmõistetavat mustrit. Roboti liigutamiseks peame AR märgise asendi põhjal robotile andma lineaarse- ja nurkkiiruse, aga see on keeruline, kui me ei tea, mis vahemikus arve on üldse vaja teisendada. Seetõttu on kasulik teisendada esmalt kvaternionid Euleri nurkadeks.




Selle jaoks on õnneks juba olemas sobivad funktsioonid. Pythoni jaoks on olemas teek nimega tf, millel on moodul transformations. Selles moodulis on funktsioon nimega euler\_from\_quaternion(), mille sisendiks on kvaternion ja väljundiks on järjend Euleri nurkadega. Allpool on toodud näide tf.transformations.euler\_from\_quaternion() funktsiooni kasutamisest.




```
import tf
...
def callback(data):
 for marker in data.markers:
 marker\_ori = (
 marker.pose.pose.orientation.x,
 marker.pose.pose.orientation.y,
 marker.pose.pose.orientation.z,
 marker.pose.pose.orientation.w)

 euler = tf.transformations.euler\_from\_quaternion(marker\_ori)
 roll = euler[0]
 yaw = euler[1]
 pitch = euler[2]
```


  




 Pane tähele, et siin koodinäites on tagasikutsefunktsiooni nimi callback. See on toodud lihtsalt näitena - peaksid oma koodis kasutama siiski enda varem loodud tagasikutsefunktsiooni. Siinse koodinäite eeskujul võid proovida ka oma koodis kvaternioni Euleri nurkadeks teisendada.



 







