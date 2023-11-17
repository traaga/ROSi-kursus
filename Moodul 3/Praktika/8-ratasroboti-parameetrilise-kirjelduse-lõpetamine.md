



 8. Ratasroboti parameetrilise kirjelduse lõpetamine
=====================================================











> 
> 
>  Eelmises ülesandes tutvusime XACRO mudeliga ja õppisime neljarattalise roboti mudelit parametriseerima. Saavutasime mudeli, mis skaleerub, kui muuta roboti kere laiust (y-teljes).
>  
> 
> 
> 
>  Selle ülesande eesmärk on **mudel lõpuni teha** ja tagada, et see **skaleerub õigesti** ka siis, kui muudetakse kere pikkust (x-teljes) või kõrgust (z-teljes).
>  
> 
> 
> 



![.](https://sisu.ut.ee/sites/default/files/rosak/files/4wheeler_drawings.png)




Sinu ülesandeks on lisada kõik vajalikud muutujad (base\_width, base\_length, base\_height, wheel\_width, wheel\_radius) ja x-telje jaoks koordinaatide peegeldamine sarnaselt y-teljega.




Mudeli viimistlemiseks lisa ka XACRO muutuja lowrider. Selle muutujaga peaks saama muuta, kui kõrgel paikneb roboti kere maapinnast. Nii saab robotist kergesti teha madalal istuva sõiduki või maastikusõiduki.




Järgnevates animatsioonides on näha erinevate muutujate oodatavat efekti. Muuda kõikide muutujate väärtusi sarnaselt animatsioonides toodule ja veendu, et mudel skaleerub õigesti.




*Animatsioonide nägemiseks klikka vahepealkirjadele.*




### [Kui kõik muutujad on lisatud, võiks robot näha välja umbes selline](#)

![.](https://sisu.ut.ee/sites/default/files/rosak/files/1_intro_trimmed.gif)




### [Muutuja base\_width muutmisel oodatav tulemus](#)

![.](https://sisu.ut.ee/sites/default/files/rosak/files/2_base_width_trimmed.gif)




### [Muutuja base\_length muutmisel oodatav tulemus](#)

![.](https://sisu.ut.ee/sites/default/files/rosak/files/3_base_length_trimmed.gif)




### [Muutuja base\_height muutmisel oodatav tulemus](#)

![.](https://sisu.ut.ee/sites/default/files/rosak/files/4_base_height_trimmed.gif)




### [Muutuja wheel\_width muutmisel oodatav tulemus](#)

![.](https://sisu.ut.ee/sites/default/files/rosak/files/5_wheel_width_trimmed.gif)




### [Muutuja wheel\_radius muutmisel oodatav tulemus:](#)

![.](https://sisu.ut.ee/sites/default/files/rosak/files/6_wheel_radius_trimmed.gif)




### [Muutuja lowrider muutmisel oodatav tulemus](#)

![.](https://sisu.ut.ee/sites/default/files/rosak/files/7_lowrider_trimmed.gif)



 
