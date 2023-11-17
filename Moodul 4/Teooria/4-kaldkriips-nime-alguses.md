



 4. Kaldkriips nime alguses
============================











> 
> 
> **Nii terminalis kataloogide aadresse kasutades kui ka ROSi rubriikide kontekstis oled võib-olla tähele pannud, et nad algavad mõnikord kaldkriipsuga ja mõnikord mitte. Millest tuleb erinevus?**
> 
> 
> 
> 



### [**Kataloogide nimedes**](#)

Mõnikord näeme kataloogide või failide nimesid, mis algavad kaldkriipsuga, näiteks:




```
/home/kasutaja/catkin_ws/src
```


 Teinekord aga näeme nimesid, mis ei alga kaldkriipsuga, näiteks:




```
catkin_ws/src
```


Erinevusest nende vahel võib mõelda järgmiselt: / tähistab juurkataloogi. Sellega algavad aadressid määravad asukoha juurkataloogi suhtes - võime seda kutsuda absoluutseks aadressiks.




Kui aga aadress ei alga /-märgiga, siis määratakse asukoht hetkel aktiivse kataloogi suhtes. Näiteks kui liigume terminalis teatud kataloogi, siis saame teiste kataloogide vahel liikuda, andes cd käsule ette sihtkoha suhtelise aadressi selle kataloogi suhtes, kus asume hetkel. Samuti võime cd käsule anda ette absoluutse aadressi, kuid sageli on see mõttetult pikk.




> 
> #### 
> Lisaks: ~
> 
> 
> 
> Kui aadress algab ~-märgiga, siis määrab see asukoha kasutaja kodukataloogi suhtes. Näiteks aadress
> 
> 
> 
> 
> ```
> ~/catkin\_ws/src
> ```
> 
> 
> on sama, mis aadress
> 
> 
> 
> 
> ```
> /home/kasutaja/catkin\_ws/src
> ```
> 
> 








### [**Rubriikide nimedes**](#)

Kaldkriipsu olemasolu või puudumine rubriigi nimes on sarnane terminali aadressitele: sellega algavad nii-öelda rubriikide absoluutsed nimed. ROSis on võimalik koodi käivitada ka teatud **nimeruumis**, st lisada sõlmede, rubriikide jmt algusesse kindel eesliide ehk prefiks - selleks aga tuleb meil hoiduda ise kaldkriipsu lisamisest rubriigi nimede algusesse.




Mida see praktikas tähendab? Reeglina pole rubriigi nime algusesse kaldkriipsu vaja lisada, seega kui kahtled, siis on kindlam see ära jätta.








 


