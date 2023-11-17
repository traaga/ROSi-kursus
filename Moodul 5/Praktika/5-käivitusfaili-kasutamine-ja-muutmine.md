



 5. Käivitusfaili kasutamine ja muutmine
=========================================











> 
> 
> **Enne oma tellija koodi käivitamist peaksime veenduma, et meie tellijal on midagi kuulata. Selleks peame käivitama AR märgiste leidja ar\_track\_alvar kimbust. See otsib kaamerapildist AR märgiseid ja kuulutab tulemusi rubriigis ar\_pose\_marker, mida kuulab meie tellija.**
> 
> 
> 
> 



> 
> #### 
>  Robot või simulatsioon?
> 
> 
> 
>  Selle harjutuse juhised on mõeldud kasutamiseks päris robotil. Soovi korral võid aga proovida seda läbida ka simulatsioonis. Selleks võid kasutada käsku
>  
> 
> 
> 
> ```
> roslaunch robotont_gazebo world_minimaze_ar.launch
> ```
> 
> 
>  Gazebos pead aga silmas pidama, et ei saa kasutada kaamera rubriiki camera/color/image\_raw\_throttled. Selle asemel pead kasutama rubriiki camera/color/image\_raw. Jäta aga meelde, et hiljem päris roboti peal koodi käivitades on kindlasti vaja rubriigiks uuesti seada camera/color/image\_raw\_throttled! Vastasel juhul võib süsteem umbe minna.
>  
> 
> 
> 



 AR märgiste tuvastamise koodi käivitamiseks saab kasutada käsku




```
roslaunch ar_track_alvar pr2_indiv_no_kinect.launch
```


 Kui paned käima eelnevalt loodud tellija koodi, siis ilmselt märkad, et endiselt ei tuvastatud ühtegi AR märgist. See on nii sellepärast, et käivitusfail pr2\_indiv\_no\_kinect.launch otsib märgiste leidmiseks vajalikku kaamerapilti valedest rubriikidest. Selle parandamiseks saame teha uue käivitusfaili, mis kasutab käivitusfaili pr2\_indiv\_no\_kinect.launch, kuid annab kaamerapildi rubriigi teiste argumentidega ette.




 Tee oma eelnevalt loodud kimbu launch-kausta uus käivitusfail. (launch-kaust tuleb luua teiste kimpudega analoogsesse asukohta - vt Moodul 3!)




 Lisa sinna järgmine sisu:




```
<launch>
  <include file="$(find ar_track_alvar)/launch/pr2_indiv_no_kinect.launch">
    <arg name="cam_image_topic" value="camera/color/image_raw_throttled"/>
    <arg name="cam_info_topic" value="camera/color/camera_info"/>
    <arg name="output_frame" value="camera_link"/>
    <arg name="marker_size" value="10"/>
  </include>
</launch>
```


 Natuke selgitust selle kohta, mis siin toimub. Kõigepealt ütleb kood, et kasutame faili pr2\_indiv\_no\_kinect.launch. Seejärel anname talle ette neli argumenti, mille vaikeväärtused algses failis meile ei sobi. Võid selle uurimiseks kõrvale lahti võtta ka faili pr2\_indiv\_no\_kinect.launch, mis asub kimbus ar\_track\_alvar.



1. Argumendi cam\_image\_topic vaikeväärtuseks on pr2\_indiv\_no\_kinect.launch failis seatud /wide\_stereo/left/image\_color. See on rubriik, kust AR märgiste leidja otsib kaamerapilti. Rubriiki nimega /wide\_stereo/left/image\_color meil ei ole, nagu võid ka ise veenduda, kui käivitad uues terminaliaknas käsu rostopic list. Selle asemel on meil rubriik /camera/color/image\_raw\_throttled. Kasutame seda.
2. Argument cam\_info\_topic: See on rubriik, kust AR märgiste leidja otsib infot kaamera kohta. Sarnaselt eelmise punktiga ei sobi meile ka selle vaikeväärtus /wide\_stereo/left/camera\_info. Soovime kasutada väärtust /camera/color/camera\_info.
3. Argument output\_frame tähistab lüli, mis vastab kaamera sensori asukohale. Meie robotil aga ei ole lüli nimega /torso\_lift\_link (mida kasutatakse vaikeväärtusena), vaid on hoopis /camera\_link.
4. AR märgiste leidja käivitamise jaoks oleme nüüd vajalikud sammud läbinud. Siiski on vaja teha veel üks muudatus, et tuvastatud AR märgised annaks meile korrektset infot. Nimelt peame seadistama, kui suured meie märgised füüsilises maailmas on. Selle info põhjal saame hiljem teada, kui kaugel oleme märgistest ja palju muud kasulikku. Argument marker\_size näitab AR märgise küljepikkust sentimeetrites. Vaikeväärtuse (vaikimisi 4.4) asemel kasutame väärtust 10.



Käivita nüüd AR märgiste leidja, kasutades uut käivitusfaili.




Juhul, kui peatasid vahepeal oma Pythoni koodi, käivita ka see nüüd uuesti. Nüüd peaks terminalis kuvatama tuvastatud AR märgiste ID-sid, juhul, kui kaamerapildis mõni leidub. Kui ei leidu, siis võid robotit liigutada nii, et mõni seinal olev AR märgis jääks kaamera vaatevälja.




> 
> #### 
>  Kaamera kalibreerimine
> 
> 
> 
>  Tegelikult on enne ar\_track\_alvar kasutamist vaja kaamera ka kalibreerida. Meie robotitel ja simulaatoritel on kõik selleks vajalikud toimingud juba läbitud, kuid uue kaamera kasutuselevõtul pead ka selle sammu läbima. See ei ole õnneks keeruline ja internetis leiduvad selle jaoks juhised.
>  
> 
> 
> 


 







