



 3. Kimp ar\_track\_alvar
==========================











> 
> 
> **Selles harjutuses paigaldame ROSi kimbu, mis tuvastab AR märgiseid.**
> 
> 
> 
> 



AR märgiste tuvastamiseks on meil vaja tarkvara, mis suudaks seda teha. Kuna tegemist on laialt levinud rakendusega, on selle tarbeks juba olemas ROSi kimp. Kimbu nimi on ar\_track\_alvar ja selle paigaldamine käib tavapärasel viisil. Liigu oma catkini tööruumi src kausta ja sisesta




```
git clone https://github.com/rios-ai/ar_track_alvar.git
cd ar\_track\_alvar
git checkout feature/rios_bug_fix
```


 Nüüd on sul olemas tarkvara AR märgiste tuvastamiseks. Kompileeri ja laadi uuesti catkini tööruum, et see oleks ka kasutatav.




 Edaspidi koodi katsetamiseks on vaja ka keskkonda, kus on olemas AR märgised. Selleks võid kasutada päris robotit koos AR-markeritega roboti lähedal seintel. Kui aga päris robotit kasutada ei saa, siis võid mõningaid katsetusi korda saata AR-märgistega Gazebo simulatsioonikeskkonnas, mille saad laadida järgneva käsu abil.




**Järgnevat käsku kasuta ainult siis, kui sul ligipääsu päris robotile parasjagu pole:**




```
roslaunch robotont_gazebo world_minimaze_ar.launch
```


 Seejärel saad kasutada juba varasemast tuttavaid lahendusi, et sõita simuleeritud robotiga simuleeritud märgiste juurde.



 







