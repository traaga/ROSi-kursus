



 4. Catkini tööruum
====================











> 
> 
> **ROSiga töötamisel on oluline aru saada, mis on catkini tööruum, kuidas seda kompileerida ja laadida. Teeme seda koos.**
> 
> 
> 
> 
>  Harjutuse sooritamiseks on vaja ligipääsu Ubuntuga arvutile, kuhu on paigaldatud ROS. Kui kasutad kursuse korraldajate poolt loodud süsteemi, siis on sinna nii Ubuntu kui ROS paigaldatud.
>  
> 
> 
> 
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



### [**Kuidas leida catkini tööruum**](#)

Catkini tööruum on lihtsalt üks kaust, mille sees omakorda on kaust nimega src, kus asuvad ROSi kimbud. Sageli on aga catkini tööruumil nimi catkin\_ws ning see võib asuda näiteks kasutaja kodukaustas. Vaata järgi, kas leiad oma süsteemist juba olemasoleva catkini tööruumi.









### [**Kui catkini tööruum on leitud**](#)

Kui arvutis leidub catkini tööruum, siis tuleb pärast selles asuvasse src-kausta uute kimpude lähtekoodi paigutamist need kimbud kompileerida. Tööruumi võib aga kompileerida ka ilma uusi kimpe juurde lisamata, seega proovime seda koos teha.



#### 
 Kompileerimine



 Catkini tööruumis olevate kimpude kompileerimiseks **liigu terminalis catkini tööruumi käsuga cd**




```
cd ~/catkin_ws
```


**Seejärel sisesta kompileerimiseks järgmine käsk**:




```
catkin build
```


 Selle käsu täitmine võib võtta mõnevõrra aega, olenevalt sellest, kui palju on catkini tööruumis kimpe ja mis neis sisaldub.



#### 
 Laadimine



 Catkini tööruumis olevate kimpude kasutamiseks on vaja tööruum **laadida**. **Kui oled terminaliga catkini tööruumi põhikaustas (nt kaustas catkin\_ws)**, siis saab seda pärast kompileerimist teha järgmise käsuga:




```
source devel/setup.bash
```


> 
> 
>  Kui lisad ROSiga töötamisel catkini tööruumi uue kimbu, siis paiguta see alati catkini tööruumis olevasse src kausta.  
> Pärast seda ära unusta tööruumi **kompileerida** ja pärast seda ka **laadida**.
>  
> 
> 
> 



> 
> 
>  Kui avatud on mitu terminali, siis piisab, et **kompileerida** vaid **ühes** neist, kuid tööruumi **laadimine** on tarvis teha **kõigis terminaliakendes** eraldi.
>  
> 
> 
> 



> 
> 
>  Võid laadimiskäsu lõpetamiseks kasutada tab-klahvi. Võid lasta arvutil seda ka osaliselt lõpetada, siis mõne tähemärgi ise trükkida ja uuesti tab-klahvi proovida kasutada.
>  
> 
> 
> 







 


