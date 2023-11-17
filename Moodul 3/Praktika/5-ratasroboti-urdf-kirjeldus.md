



 5. Ratasroboti URDF kirjeldus
===============================











> 
> 
>  Selles harjutuses kasutame **URDFi** (ingl k. *Unified Robot Description Format*), et luua **liikuva roboti kirjeldus**.
>  
> 
> 
> 
>  Selleks, et näite järgi kaasa teha, on vaja ROSi ja catkini tööruumi.
>  
> 
> 
> 
>  Lisaks on vaja ROSi kimpe urdf\_tutorial ning joint\_state\_publisher\_gui. Kui kasutad kursuse korraldajate poolt pakutavat keskkonda, siis on need kimbud juba paigaldatud.
>  
> 
> 
> 
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



### [**1. Mis on URDF?**](#)






 URDF on ***Unified Robot Description Format*** ehk formaat robotite kirjeldamiseks. See on XML kujul tekstifail, mis kirjeldab roboti mudelit.




 Tüüpiline URDF mudel sisaldab lülisid ja liigendeid. Lülid on roboti komponendid ja liigendid on nendevahelised ühendused.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/link.png)Allikas: ROS Wiki: Create your own URDF file




  









### [**2. URDF mudeli loomine**](#)

**a.** Avame terminali ja liigume catkini tööruumi src kaustas olevasse kausta fourwheeler\_description, mille lõime eelnevalt.




```
cd ~/catkin\_ws/src/fourwheeler\_description
```


**b.** Loome seal uue kausta nimega urdf. Sinna paigutame roboti URDF mudeli.




```
mkdir urdf
```


**c.**Liigume urdf kausta.




```
cd urdf
```


**d.** Loome URDF mudeli jaoks dokumendi nimega fourwheeler.urdf.




```
gedit fourwheeler.urdf
```







### [**3. URDF mudeli dokumenti sisu lisamine**](#)

Vaata alltoodud animatsioonist, kuidas kirjeldatud samme rakendada. Koodi leiad kopeeritaval kujul ka animatsiooni alt.




**a.** Lisame päise, et defineerida dokument kui XML.




**b.** Lisame roboti nime, kasutades XML märgendit <robot>. Antud näites on selleks nimeks fourwheeler. Lisame ka kohe avatud faili kõige viimasele reale roboti kirjeldust sulgeva märgendi </robot>.




**c.** Lisame esimese komponendi, milleks võiks olla meie roboti keskne kere. Selleks loome lüli nimega base\_link, kasutades XML märgendit link.




**d.** Olgu meie roboti keskse kere kujuks risttahukas. Et seda nüüd URDF-i abil kirjeldada, lisame base\_link lülile parameetrid, et määratleda kere täpne kuju ja suurus. Selleks kasutame XML märgendit <visual> ning selle alamärgendit <geometry>, mis võimaldab meil antud lülile anda lihtsa geomeetrilise kuju, antud juhul siis <box> ehk risttahukas.




**e.** Salvestame ja sulgeme dokumendi.




**Kood selle saavutamiseks:**




```
<?xml version="1.0"?>
<robot name="fourwheeler">

  <link name="base_link">
    <visual>
      <geometry>
        <box size="0.430 0.320 0.140" />
      </geometry>
    </visual>
  </link>

</robot>
```


**Siit näed, kuhu kood paigutada:**














### [**4. URDF mudeli visualiseerimine**](#)

Olles kaustas catkin\_ws/src/fourwheeler\_description/urdf/, saame urdf\_tutorial kimbus sisalduva käivitusfaili abil oma roboti hõlpsasti visualiseerida.




```
roslaunch urdf\_tutorial display.launch model:=fourwheeler.urdf
```


Seejärel avaneb järgnev RViz-i aken.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/3_rviz_initial.png)









### [**5. URDF mudeli värvi muutmine**](#)

Algselt on terve robot punane. Muudame roboti värvi siniseks.




Sulge RViz ja ava URDF fail (fourwheeler.urdf). RVizi sulgemiseks vajuta Terminali aknas klahvikombinatsiooni CTRL+C.




Värvi lisamiseks kasutame XML märgendit material. Alltoodud animatsioonis on näha, kuidas lisada robotile värv. Värv on toodud RGBA värviruumis, kus on neli kanalit: punane (R – red), roheline (G – green), sinine (B – blue), alfa ehk läbipaistvus (A – alpha). Neid väärtusi saab seada vahemikus 0–1, et määrata iga komponendi intensiivsus.




Näites toodud RGBA väärtused 0  0  0.8  1 annavad tumedama sinise, millel puudub läbipaistvus.




Proovi julgelt erinevaid värvikombinatsioone.




**Uus koodilõik:**




```
      <material name="blue">
        <color rgba="0 0 0.8 1" />
      </material>
```


**Kuhu kood paigutada:**








Uue värviga mudeli nägemiseks salvestame ja sulgeme fourwheeler.urdf faili ning käivitame uuesti display.launch faili.

Tulemus peaks sarnanema alltooduga.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/5_urdf_new_colour.png)









### [**6. Ühe ratta lisamine**](#)

Nagu meie loodud kimbu nimigi viitab, tahame lõpuks valmis saada nelja rattaga roboti mudeli. Alustame ühe ratta lisamisest.




Lisame lüli nimega front\_right\_wheel. Ratta mudeli kujuks valime silindri (cylinder), mille kõrgus (length) on 0,05 m ja raadius (radius) 0,1 m. Rattad on tihti musta värvi; RGB värviruumis saavutame musta, kui määrame iga kanali väärtuseks 0. Määrame alfa-kanali väärtuseks 1, et ratas ei oleks läbipaistev.




> 
> #### 
>  Näpunäide
> 
> 
> 
>  Uue lüli saamiseks tee koopia eelnevalt loodud lüli koodilõigust ja muuda ära vajalikud väärtused!
>  
> 
> 
> 







