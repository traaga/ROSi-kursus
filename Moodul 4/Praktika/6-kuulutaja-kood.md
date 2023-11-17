



 6. Kuulutaja kood
===================











> 
> 
> **Vaatame nüüd, kuidas kirjutada ROSi koodi.**
> 
> 
> 
> 
> *Samm-sammulise juhendi vaatamiseks kliki harjutuse vahepealkirjadele.*
> 
> 
> 
> 



> 
> #### 
> Pane tähele!
> 
> 
> 
> Pythoni koodi kirjutades pööra tähelepanu ridade taanetele! Kood peab alati olema õigesti taandatud.
> 
> 
> 
> 



Loome uue tekstifaili ja anname selle nimeks näiteks simple\_velocity\_publisher.py. Selle sisse hakkame kirjutama oma koodi.




### [**Koodi päis**](#)






```
#!/usr/bin/env python3
import rospy
from geometry\_msgs.msg import Twist
```


Alustame faili kolme tekstirea lisamisest (need on kirjas ülal).




Kõigepealt peame ROSile teada andma, kust leida Pythoni koodifailide käivitamiseks vajalik programm. Selleks lisame faili esimesele reale spetsiaalse kommentaari #!/usr/bin/env python3.




Järgmiseks peame importima kaks moodulit. Esimene neist on rospy - see lubab meil kirjutada Pythonis ROSi koodi. Viimaseks impordime sõnumitüübi Twist, kuna soovime kuulutama hakata just seda tüüpi sõnumeid.









### [**Sõlme loomine**](#)






```
#!/usr/bin/env python3
import rospy
from geometry\_msgs.msg import Twist

rospy.init\_node("velocity\_publisher")
```

Et meie Pythoni koodist saaks ROSi sõlm, tuleb ta sõlmena lähtestada ehk initsialiseerida. Koodis saame seda teha, kutsudes välja initsialiseerimise funktsiooni rospy.init\_node ja andes sellele argumendiks sõlme soovitud nime, näiteks velocity\_publisher.






### [**Kuulutaja loomine**](#)






```
#!/usr/bin/env python3
import rospy
from geometry_msgs.msg import Twist

rospy.init\_node("velocity\_publisher")
velocity\_pub = rospy.Publisher("cmd\_vel", Twist, queue\_size=0)
rospy.sleep(2)

```


Kuna robotile liikumiskäskude edastamiseks tuleb meil asuda kuulutama Twist-tüüpi sõnumeid rubriigis cmd\_vel, siis järgmiseks lisamegi oma loodud sõlmele ühe kuulutaja. (Võime kuulutajast mõelda kui uuest muutujast, millel tuleb anda ka nimi, antud juhul anname kuulutajale nimeks velocity\_pub.) Kuulutaja tegemiseks kasutame  funktsiooni Publisher, mis asub rospy moodulis. See funktsioon ootab sisendina kolme argumenti: rubriigi nime, milles soovime kuulutada, sõnumitüüpi, mis kirjeldab selles rubriigis kuulutatavaid sõnumeid, ja järjekorra suurust. Neist esimese väärtuseks anname cmd\_vel (jutumärkides!), teise väärtuseks Twist ja järjekorra suuruseks 0, sest me ei taha, et sõnumid järjekorras ootaks: rospy.Publisher("cmd\_vel", Twist, queue\_size=0)




See funktsiooni väljakutse tagastab meile objekti, millest võime mõelda kui meie kuulutajast. Selleks, et seda hiljem kasutada ja sinna meile sobivaid sõnumeid saata, määrame ta muutuja velocity\_pub väärtuseks: velocity\_pub = rospy.Publisher("cmd\_vel", Twist, queue\_size=0)




Viimaseks lisame rea, mis paneb koodi ootama kaks sekundit enne jätkamist: rospy.sleep(2). See lubab süsteemil pärast kuulutaja loomist kõik vajalikud toimingud lõpetada, enne kui hakkame sinna sõnumeid saatma - meil ei ole sellega kiiret.




> 
> #### 
> Pane tähele!
> 
> 
> 
> Ära lisa rubriigi nime algusesse kaldkriipsu. Nii hoiame koodi kasutusvõimalused paindlikumad.
> 
> 
> 
> 








### [**Twist-sõnumi loomine**](#)






```
#!/usr/bin/env python3
import rospy
from geometry\_msgs.msg import Twist

rospy.init\_node("velocity\_publisher")
velocity\_pub = rospy.Publisher("cmd\_vel", Twist, queue\_size=0)
rospy.sleep(2)

robot\_vel = Twist()
robot\_vel.linear.x = 0.1
robot\_vel.linear.y = 0.0
robot\_vel.linear.z = 0.0
robot\_vel.angular.x = 0.0
robot\_vel.angular.y = 0.0
robot\_vel.angular.z = 0.0
```


 Tühja Twist-sõnumi loomiseks kasutame funktsiooni Twist(). Sedasi loodud sõnumi määrame muutuja robot\_vel väärtuseks.




Seejärel saame Twist-sõnumi väljadele ükshaaval ligi, lisades vastloodud muutujale lõppu, missugust komponenti soovime muuta või lugeda: näiteks .linear.x või .angular.z. Kasutame seda, et anda kõigile Twist-sõnumi väljadele väärtuseks 0, peale lineaarse liikumise x-komponendi, mille väärtuseks anname 0.1. See peaks panema meie roboti otsesuunas edasi liikuma kiirusega 0.1 m/s.









### [**Twist-sõnumi kuulutamine**](#)






```
#!/usr/bin/env python3
import rospy
from geometry\_msgs.msg import Twist

rospy.init\_node("velocity\_publisher")
velocity\_pub = rospy.Publisher("cmd\_vel", Twist, queue\_size=0)
rospy.sleep(2)

robot\_vel = Twist()
robot\_vel.linear.x = 0.1
robot\_vel.linear.y = 0.0
robot\_vel.linear.z = 0.0
robot\_vel.angular.x = 0.0
robot\_vel.angular.y = 0.0
robot\_vel.angular.z = 0.0

velocity\_pub.publish(robot\_vel)
```


 Nüüd kui sõnumi sisu on kirjeldatud, on viimase sammuna tarvis see sõnum rubriigis cmd\_vel kuulutada. Selleks kasutame eespool defineeritud kuulutajat nimega velocity\_pub, mis oskab täpselt seda: kuulutada Twist-sõnumeid rubriigis cmd\_vel. Ühe sõnumi kuulutamiseks kasutame kuulutajas leiduvat meetodit publish, mis võtab argumendiks vastloodud sõnumi.









### [**Main-funktsiooni loomine**](#)






```
#!/usr/bin/env python3
import rospy
from geometry\_msgs.msg import Twist

def main():
 rospy.init\_node("velocity\_publisher")
 velocity\_pub = rospy.Publisher("cmd\_vel", Twist, queue\_size=0)
 rospy.sleep(2)

 robot\_vel = Twist()
 robot\_vel.linear.x = 0.1
 robot\_vel.linear.y = 0.0
 robot\_vel.linear.z = 0.0
 robot\_vel.angular.x = 0.0
 robot\_vel.angular.y = 0.0
 robot\_vel.angular.z = 0.0

 velocity\_pub.publish(robot\_vel)

if \_\_name\_\_ == '\_\_main\_\_':
 try:
 main()
 except rospy.ROSInterruptException:
 pass
```


 Pane tähele, et siin näites on peale uute koodiridade muudetud ka mõningate olemasolevate taanet.




 ROSi koodi Pythonis struktureerimiseks on ilus luua main-funktsioon, mida kutsutakse välja ainult siis, kui käivitatakse tõepoolest seda faili, mitte ei impordita teda mujale. Lisaks on hea main-funktsiooni väljakutse panna try ja except ploki sisse, mis jälgib, ega koodi käivitamist kuidagi ei häirita (nt Ctrl+C vajutades) - siis saame soovi korral koodi viisakalt peatada.




Liigutame oma eelnevalt loodud koodilõigu (välja arvatud koodi päis) main-funktsiooni sisse ja lisame koodi lõppu osa, mis seda välja kutsub.




Kood töötaks ka ilma eraldi main-funktsiooni loomata, aga hea praktika on see sellegipoolest lisada.






