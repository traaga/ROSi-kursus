



 7. Kuulutaja katsetamine
==========================











> 
> 
> **Nüüd, kui meil on kuulutaja loodud, proovime seda päriselt käivitada. Lisaks sellele katsetame erinevaid liikumiskäsu väärtuseid.**
> 
> 
> 
> 
> *Samm-sammulise harjutuse vaatamiseks kliki vahepealkirjadele.*
> 
> 
> 
> 



### [**Käivitamisõiguste lisamine**](#)

Kõigepealt on meil vaja vastloodud sõlmele anda juurde käivitamisõigused - siis teab ROS, et seda tekstifaili saab käivitada koodina.




Liigu terminalis kausta, kus asub meie loodud Pythoni fail.




Siis anna sellele käivitamisõigused käsuga chmod u+x failinimi. Täpsemini on see hetkel




```
chmod u+x simple\_velocity\_publisher.py
```







### [**Kompileerimine, laadimine, käivitamine**](#)

Järgmiste sammudena peame catkini tööruumi **kompileerima**.




Pärast seda peame selle ka **laadima**.




Siis sooviksime näha, kas meie kood ka midagi teeb. Kõige lihtsam viis seda näha on kuulata pealt cmd\_vel rubriigis kuulutatud sõnumeid.




Käivita roscore ja seejärel sisesta teises terminaliaknas tuttav käsk




```
rostopic echo cmd\_vel
```


Viimaseks käivitame oma vastloodud sõlme. Käivita uues aknas meie sõlm simple\_velocity\_publisher.py kimbust geometric\_shapes. Seejärel vaata, kas rostopic echo aknas on kuvatud meie koodi kuulutatud sõnum.









### [**Kas robot liigub ka?**](#)

Kui oleme kindlaks teinud, et meie kood kuulutab sõnumeid cmd\_vel rubriigis, siis võime proovida, kas see ka robotit liigutab.




Käivita robotondi simulaator fake\_driver abil:




```
roslaunch robotont\_driver fake\_driver.launch
```


Nüüd võta lahti terminaliaken, kus saad käivitada meie loodud koodi, nagu eelmiseski sammus. Liiguta aknad nõnda, et näeksid samaaegselt nii RVizi akent kui ka saaksid sisestada käsku meie koodi käivitamiseks. Vajadusel tee aknaid väiksemaks.




Käivita simple\_velocity\_publisher.py ja vaata, kas see liigutab robotit.









### [**Muudes suundades liikumine**](#)

Nüüd võiksime katsetada, kas suudame robotit ka teistmoodi liikuma panna.




Muuda mõnd Twist-sõnumi väärtust koodis, salvesta kood ja käivita see uuesti. Pythoni koodi puhul on hea see, et me ei pea iga kord catkini tööruumi uuesti kompileerima - C++ koodi kirjutades peaksime seda tegema.




Proovi välja mõelda (ja järgi proovida), kuidas panna robotit liikuma:



* tagurpidi;
* külgepidi vasakule;
* külgepidi paremale;
* pöörama;
* liikuma diagonaalis;
* kiiremini.







