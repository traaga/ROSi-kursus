



 4. ROSi tellija kirjutamine
=============================











> 
> 
> **Eelnevalt tutvusime AR märgistega ja uurisime, millist infot on võimalik nende abil saada. Selles harjutuses kirjutame lihtsa ROSi tellija (ingl *subscriber*), et saada oma koodis kätte AR märgiste positsiooni ja orientatsiooni info, mida kuulutab ar\_track\_alvar kimbu sõlm. See on aluseks, et saaksime AR märgiste põhjal panna roboti midagi tegema.**
> 
> 
> 
> 



### [**Kimbu loomine**](#)

Loo uus ROSi kimp, mis sõltub järgmistest kimpudest: ar\_track\_alvar\_msgs, geometry\_msgs, rospy ja tf. Kui vaja, siis vaata eelmisest materjalist, kuidas kimpu luua.









### [**Koodifail**](#)

Loo uue kimbu sisse scripts kaust ja selle sisse koodifail, mis sisaldab järgmiseid kuulutaja kirjutamisest tuttavaid elemente ROSi kasutamiseks:



* rospy importimine
* main funktsioon ja selle väljakutsumine
* sobivate argumentidega sõlme loomine
* while-tsükkel, mis jookseb seni, kuni sõlm kinni pannakse (nt Ctrl+C abil)








### [**Sõnumitüüp**](#)

Lisa koodifaili päisesse importimine, mis võimaldab koodis kasutada sõnumeid, mida kuulutab ar\_track\_alvar. Need sõnumid on tüübiga AlvarMarkers.




```
from ar_track_alvar_msgs.msg import AlvarMarkers
```







### [**Tellija loomine**](#)

Nüüd saame luua tellija ja lisada muud koodiread, mis on vajalikud tellija toimimiseks. Tellija loomine on sarnane kuulutaja loomisele. Kasutame selleks käsku rospy.Subscriber(), millele anname sulgude sees järgmised argumendid:



* selle **rubriigi nimi**, kus kuulutatavaid sõnumeid tellija peab kuulama;
* rubriigis kuulutatavate sõnumite **sõnumitüüp**;
* **tagasikutsefunktsiooni** nimi, mis tegeleb sõnumitega, kui need saabuvad (sellest räägime rohkem natukese aja pärast).



 Tellija loomine peab koodis toimuma pärast sõlme loomist, aga enne peamist while-tsüklit. Loomiseks kasuta järgmist koodirida:




```
rospy.Subscriber("ar_pose_marker", AlvarMarkers, ar_message_handler)
```


 Meie tellija kuulab AlvarMarkers tüüpi sõnumeid rubriigis ar\_pose\_marker. Vastuvõetud sõnumitega tegeleb funktsioon nimega ar\_message\_handler. See on tagasikutsefunktsioon (ingl *callback function*) ehk funktsioon, mis käivitub iga sõnumi saabumisel. Funktsiooni koodis rohkem välja kutsuda ei ole vaja - tellija loomisel on vajalikud seosed juba loodud.









### [**Tagasikutsefunktsioon**](#)

Loo tagasikutsefunktsioon AlvarMarkers sõnumitega tegelemiseks. Selle funktsiooni sisendparameetriks on viimane AlvarMarkers tüüpi sõnum, mille meie tellija vastu võttis.




 Oluline asi, mida meeles pidada, on et tagasikutsefunktsioon tuleb luua enne, kui seda kasutatakse. Tellija loomisel seda juba kasutatakse, sest anname ar\_message\_handler funktsiooni rospy.Subscriber() funktsioonile argumendiks. Seetõttu tuleb see funktsioon koodis paigutada main-funktsioonist ettepoole (aga päisest allapoole).




 Lihtne variant ar\_message\_handler funktsioonist on toodud järgnevalt. See funktsioon prindib välja kõigi tuvastatud AR märgiste ID, kui kaamerapildis mõni leitakse, ja informatiivse sõnumi, kui ühtegi märgist ei leitud.




```
def ar_message_handler(data):
   if len(data.markers) > 0:
      for marker in data.markers:
         rospy.loginfo("Detected marker with ID " + str(marker.id))

   else:
      rospy.loginfo("No AR markers detected.")
```


Ongi kõik, tellija on valmis!









### [**Koodi katsetamine**](#)

Selleks, et koodi saaks käivitada, tuleb sellele anda vastavad õigused samamoodi, nagu tegime moodul 4 käigus. Failiga samas kaustas:




```
chmod +x faili_nimi.py
```


Oma koodi saame käivitada järgneva tuttava süntaksiga käsuga:




```
rosrun kimbu\_nimi faili\_nimi.py
```


Asenda käsus kimbunimi ja failinimi oma kimbu ja faili nimedega.




On ootuspärane, et kui nüüd ilmub kaamerapilti mõni AR märgis, siis prindib meie kood välja selle ID. AR märgiste puudumisel prinditakse välja infot, et märgiseid ei leitud. **Seda aga ei juhtu.** Kogu põhjus on selles, et me pole veel käivitanud sõlme, mis AR märgiseid tuvastab ja rubriiki ar\_pose\_marker kuulutab. Teeme seda järgmises harjutuses.






