



 6. AR märgiste positsiooni x-komponent
========================================











> 
> 
> **Seni oleme printinud välja ainult AR märgiste ID-d. AlvarMarkers sõnumite teistele komponentidele saame ligi sarnasel viisil.**
> 
> 
> 
> 



Terveid sõnumeid ar\_pose\_marker rubriigis näed tööriista rostopic echo abil tavapärasel viisil:




```
rostopic echo /ar\_pose\_marker
```


Ilmselt märkad, et AlvarMarkers sõnumid on kõik kindla struktuuriga. Natuke sarnast struktuuri oled juba näinud robotondi liigutamisel: muutsid Twist tüüpi sõnumis (olgu sõnum muutujas msg) komponente msg.linear.x ja msg.angular.z.




 Nüüd proovi AlvarMarkers tüüpi sõnumitest välja printida markerite positsiooni x-komponendid. Igas sõnumis on msg nimeline komponent tüübiga PoseStamped. Uuri [PoseStamped dokumentatsioonist](https://docs.ros.org/en/noetic/api/geometry_msgs/html/msg/PoseStamped.html), milliseid osi see sõnum sisaldab. Võid ka jälgida sõnumeid rubriigis ar\_pose\_marker. Iga järgnev paremale taandatud element on hierarhias eelnevast ühe võrra madalam.




> 
> #### 
>  Vihje
> 
> 
> 
> AlvarMarkers sõnumist saad positsiooni x-komponendi kätte, kui sõnumist msg küsid msg.pose.pose...
> 
> 
> 
> 



Täienda nüüd oma ar\_message\_handler funktsiooni selliselt, et see prindiks välja kõikide leitud AR märgiste positsiooni x-komponendi.



 







