



 8. Pikem sõit
===============











> 
> 
> **Nüüd oskame robotit sõitma panna, kuid ainult lühikeseks ajaks. Mis siis, kui tahame, et ta sõidaks pikemat aega?**
> 
> 
> 
> 



Selleks, et roboti kasutamine oleks turvaline (näiteks olukorras kus ühendus roboti ja cmd\_vel kuulutaja vahel kaob), on roboti draiverisse sisse programmeeritud kaitsemehhanism, mis automaatselt peatab roboti mootorid, kui poole sekundi jooksul ei ole uut sõnumit kiiruse infoga saabunud. Kui soovime, et robot liiguks edasi kauem kui pool sekundit, peame talle pidevalt liikumiskäske saatma. Vaatame, kuidas oma koodi veidi muuta nõnda, et see liikumiskäske regulaarselt kuulutaks.




```
#!/usr/bin/env python3
import rospy
from geometry\_msgs.msg import Twist

def main():
 rospy.init\_node("velocity\_publisher")
 velocity\_pub = rospy.Publisher("cmd\_vel", Twist, queue\_size=0)
 rospy.sleep(2)

 loop\_rate = rospy.Rate(10)
 starting\_time = rospy.get\_time()

 while (not rospy.is\_shutdown()) and (rospy.get\_time() - starting\_time < 5):
 robot\_vel = Twist()
 robot\_vel.linear.x = 0.1
 robot\_vel.linear.y = 0.0
 robot\_vel.linear.z = 0.0
 robot\_vel.angular.x = 0.0
 robot\_vel.angular.y = 0.0
 robot\_vel.angular.z = 0.0

 velocity\_pub.publish(robot\_vel)

 loop\_rate.sleep()

if \_\_name\_\_ == '\_\_main\_\_':
 try:
 main()
 except rospy.ROSInterruptException:
 pass
```


  




Analüüsime selle koodi tööd.




```
starting\_time = rospy.get\_time()
```


See rida paneb muutuja starting\_time väärtuseks praeguse kellaaja, mõõdetuna sekundites kindlast ajahetkest minevikus. Teiste sõnadega: see ütleb meile, kui mitu sekundit on möödunud teatud kindlast ajahetkest. Mis hetk see täpselt on, see ei olegi meie jaoks oluline.




```
while (not rospy.is\_shutdown()) and (rospy.get\_time() - starting\_time < 5):
```


See rida tekitab tsükli, mis jookseb seni, kuni kehtivad kaks tingimust: ROSi tööd pole peatatud (not rospy.is\_shutdown()) ja vahe praeguse aja (rospy.get\_time()) ning koodi algusaja (starting\_time) vahel on väiksem kui 5 sekundit. Tegelikkuses tähendab see, et kood jookseb kuni 5 sekundit.




```
loop\_rate = rospy.Rate(10)
```


ning




```
loop\_rate.sleep()
```


Need read aitavad meil tsüklit käimas hoida konstantse kiirusega. Robootikas on sageli kasulik, kui meie kood läbib tsüklit kindla pikkusega. rospy.Rate(10) tekitab meile võimaluse panna koodi jooksma kiirusega 10 Hz (st 10 korda sekundis). Selle funktsiooni tagastatud väärtuse paneme muutujasse loop\_rate. Ning seejärel saame tsükli lõpus välja kutsuda funktsiooni loop\_rate.sleep(), mis lihtsalt aeglustab tsükli läbimist ja ootab, kuni tsükli läbimiseks kulunud aeg on täpselt kümnendik sekundit.




> 
> #### 
> Miks programmi tööd aeglustada?
> 
> 
> 
> Programmi töö aeglustamine võib olla kasulik mitmes olukorras. Tavaliselt täidab arvuti programmi nii kiiresti, kui võimalik - kasutades selleks ära kõik oma ressursid. Sõltuvalt sellest, mida programm tegema peab, võib miljonite operatsioonide sooritamine ühes sekundis olla täiesti ebapraktiline ning energiat raiskav. Selleks ongi programmeerimiskeeltes spetsiaalsed käsud, millega programmi aeglustada. Need käsud võimaldavad anda vahepeal järg üle teistele programmidele ning aeglustada või teatud ajaks sootuks peatada protsessori töö. Tasub tähele panna, et isegi 0.01 sekundi pikkune paus, mis inimese jaoks tundub tühiselt väike võib olla arvuti jaoks terve igavik, sest protsessor suudab teha mitmeid tehteid ühes nanosekundis ehk 0.000000001 sekundis.
> 
> 
> 
> 
> Aeglustamist kasutatakse ka selleks, et programmi panna käima korduvalt täpselt määratud aja tagant.
> 
> 
> 
> 



  



 







