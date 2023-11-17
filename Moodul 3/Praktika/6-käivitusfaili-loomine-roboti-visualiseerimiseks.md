



 6. Käivitusfaili loomine roboti visualiseerimiseks
====================================================











> 
> 
> **Selles harjutuses õpid looma käivitusfaili, mis kuvaks eelmises harjutuses loodud ratasrobotit RVizis soovitud kujul.**
> 
> 
> 
> 
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



### [**1. RVizi konfiguratsioonifail**](#)

Visualiseeri ülesandes valmistatud ratasrobot RVizis.




 Kui käivitad RVizi, siis paned tähele, et pead võib-olla tuunima mõningaid parameetreid (nt *alpha* väärtus, et robot ei oleks läbipaistev) või robotit paremini aknasse sättima, et seda näha. Selleks, et seda iga kord eraldi tegema ei peaks, võime salvestada endale **RVizi konfiguratsioonifaili**. Kui anname RVizile käivitamisel salvestatud konfiguratsioonifaili ette, siis kuvab ta robotit kohe avamisel just sellisel viisil, nagu konfiguratsioonifaili salvestatud on.




 Konfiguratsioonifailid paigutatakse kimbu sees tavaliselt config-nimelisse kausta. Praegu võime konfiguratsioonifaili paigutada fourwheeler\_description kimpu. Loo selle kimbu alla uus alamkaust nimega config (selle aadress oleks siis nt /home/kasutaja/catkin\_ws/src/fourwheeler\_description/config).




 Konfiguratsioonifaili salvestamiseks säti robot just sedasi, nagu teda näha soovid, ja vali siis "*File*" menüüst valik "***Save Config As***". Salvesta fail nimega fw.rviz eelnevalt loodud fourwheeler\_description/config kausta.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/saveas.png)









### [**2. Käivitusfaili loomine**](#)

Nüüd loome käivitusfaili, mis kuvaks meile ratasrobotit just sellisel kujul, nagu välja toodud äsjasalvestatud konfiguratsioonifailis.




 Loo kimbus fourwheeler\_description uus alamkaust nimega launch (selle aadress oleks siis nt /home/kasutaja/catkin\_ws/src/fourwheeler\_description/launch). Sellise nimega kausta paigutatakse käivitusfailid.




 Loo selle uue kausta sisse käivitusfail nimega display.launch. Selle faili sisse kirjuta järgmist:




```
<launch>
  <param name="robot_description" command="$(find xacro)/xacro '$(find fourwheeler_description)/urdf/fourwheeler.urdf'" />
  <node name="robot_state_publisher" pkg="robot_state_publisher" type="robot_state_publisher" />
  <node name="joint_state_publisher_gui" pkg="joint_state_publisher_gui" type="joint_state_publisher_gui" />
  <node name="rviz" pkg="rviz" type="rviz" args="-d $(find fourwheeler_description)/config/fw.rviz" />
</launch>
```


 Salvesta fail.




 Mida see kõik tähendab? Käime selle faili rida-realt läbi.




```
<launch>
```


 See märgend näitab, et siit algab käivitusfaili sisu.




```
<param name="robot_description" command="$(find xacro)/xacro '$(find fourwheeler_description)/urdf/fourwheeler.urdf'" />
```


 See rida otsib urdf kaustast üles roboti kirjelduse ja laadib selle parameetriserverisse, et seda saaks kuvada.




```
<node name="robot_state_publisher" pkg="robot_state_publisher" type="robot_state_publisher" />
```


 See rida käivitab sõlme robot\_state publisher kimbust robot\_state\_publisher nimega robot\_state\_publisher, mis võib kindlasti tunduda segane, seega arutame, mis erinevus neil kolmel parameetril on:



* pkg määrab kimbu nime
* type määrab faili nime, kus asub käivitatav sõlm
* name määrab nime, mille all käivitatud sõlm rosnode list kasutades hiljem kuvatakse



 See sõlm võtab URDF kirjelduse ja loob sellest koordinaatsüsteemid jmt, mis kirjeldavad robotit.




```
<node name="joint_state_publisher_gui" pkg="joint_state_publisher_gui" type="joint_state_publisher_gui" />
```


 See rida käivitab sõlme joint\_state\_publisher\_gui kimbust joint\_state\_publisher\_gui. See loob meile slaiderid, mille abil saame roboti pöördliigendeid liigutada.




```
<node name="rviz" pkg="rviz" type="rviz" args="-d $(find fourwheeler_description)/config/fw.rviz" />
```


 See rida käivitab sõlme rviz kimbust rviz. Lisaks antakse talle ette argumendina meie eelnevalt loodud konfiguratsioonifail fw.rviz.




```
</launch>
```


 Viimaks sulgeb see märgend käivitusfaili sisu.




 Käivitame selle uue käivitusfaili:




```
roslaunch fourwheeler_description display.launch
```


 Kui kõik töötab õigesti, siis näed robotit soovitud konfiguratsioonis.








 


