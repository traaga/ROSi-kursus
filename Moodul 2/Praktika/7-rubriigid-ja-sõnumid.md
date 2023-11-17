



 7. Rubriigid ja sõnumid
=========================











> 
> 
> **Selles harjutuses tutvud ROSi sõlmede, rubriikide ja sõnumitega. Õpid nende käsurealt uurimiseks kasutama ROSi tööriistu.**
> 
> 
> 
> 
>  Harjutuse sooritamiseks on vaja Ubuntu ja ROSiga arvutit, kuhu on paigaldatud kimbud teleop\_twist\_keyboard, robotont\_description, robotont\_driver ja robotont\_msgs. Kui kasutad kursuse korraldajate poolt pakutud süsteemi, siis on need kimbud juba paigaldatud.
>  
> 
> 
> 
> **Harjutus ei ole mõeldud läbimiseks füüsilise robotiga.**
> 
> 
> 
> 
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



### [**1. Käivita digikaksik**](#)

Alustuseks on selles harjutuses hea mõte käivitada roscore eraldi:




```
roscore
```


 Nüüd käivita uues aknas robotondi digikaksik käsuga




```
roslaunch robotont_driver fake_driver.launch
```


 Jäta need käsklused nendes kahes terminaliaknas jooksma (**ära sulge neid Ctrl+C abiga**) ja võta vajadusel uute käskude jaoks lahti veel uusi terminaliaknaid.









### [**2. Mis on ROSi sõlmed?**](#)

ROSi **sõlmed** (ingl k. *node*) on protsessid, mis teevad ROSi süsteemis arvutusi. Tavaliselt toimetavad sõlmed paralleelselt ja saadavad üksteisele info vahetamiseks sõnumeid.




 Kõiki aktiivseid ROSi sõlmi on võimalik näha käsuga




```
rosnode list
```


 Käsk rosnode info <sõlme\_nimi> näitab infot konkreetse sõlme kohta.




 Vaata ka ise lähemalt ühe sõlme sisu. Selleks kirjuta käsureale näiteks




```
rosnode info /fake\_driver\_node
```


 Peaksid nägema vaadet, mis sarnaneb allolevale pildile:




![Käsu "rosnode info /fake_driver_node" väljund](https://sisu.ut.ee/sites/default/files/rosak/files/screenshot_from_2021-02-13_13-32-01_ba627a525f5ec24189b3da6a46782e66.png)









### [**3. Mis on ROSi rubriigid?**](#)

ROSi **rubriigid (ingl k. *topic*)** on nimelised suhtluskanalid, mille kaudu saavad sõlmed omavahel sõnumeid vahetada.




 ROSi sõlmed saavad rubriike kasutada kahel viisil: nad võivad sinna sõnumeid **kuulutada (ingl k. *publish*)** või sealt sõnumeid **tellida (ingl k. *subscribe*)**.




 Rubriigis **kuulutamine** tähendab, et sõlm **saadab selles rubriigis sõnumeid välja** eesmärgiga anda infot teistele sõlmedele. Sõlm, mis sõnumeid kuulutab, on **kuulutaja (ingl k. *publisher*)**.




 Rubriigist **tellimine** tähendab, et sõlm **kuulab, kas rubriigis on sissetulevaid sõnumeid**, mida on selles rubriigis kuulutanud mõni teine sõlm. Sõlm, mis tellib sõnumeid, on **tellija (ingl k. *subscriber*)**.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/screenshot_from_2021-02-13_13-34-03_275c766fdc5acbedf7f4c97b47f9e99c.png)




  




 Sellel joonisel on sõlmed tähistatud ellipsitena ja rubriigid nendevaheliste nooltena. Sõlmest väljuv nool näitab, et sõlm kuulutab rubriigis sõnumeid. Sõlme sissetulev nool näitab, et sõlm tellib rubriigist sõnumeid. Jooniselt on näha, et teleop\_twist\_keyboard sõlm kuulutab sõnumeid cmd\_vel rubriiki ja fake\_driver\_node tellib sõnumeid samalt rubriigist.




 Sõlm võib samaaegselt olla ka nii kuulutaja kui tellija, tavaliselt küll erinevate rubriikide suhtes. Sõlm võib ka kuulutada sõnumeid mitmes rubriigis või tellida sõnumeid mitmest rubriigist.




 Samas rubriigis võib sõnumeid kuulutada mitu sõlme, samuti võib korraga mitu sõlme samast rubriigist sõnumeid tellida. On ka võimalik, et ROSi rubriik eksisteerib nii, et ükski sõlm sinna sõnumeid ei kuuluta või ei telli sealt sõnumeid.









### [**4. Rubriikide uurimine, 1. osa**](#)

Käivita käsk, mis väljastab nimekirja kõigist aktiivsetest ROSi rubriikidest:




```
rostopic list
```


 Peaksid nägema rubriiki nimega cmd\_vel. Selles rubriigis liiguvad sõnumid roboti liikumise kohta. Uurime lähemalt. Sisesta käsk




```
rostopic info /cmd_vel
```


 Peaksid nägema umbes sellist vaadet:




![.](https://sisu.ut.ee/sites/default/files/rosak/files/screenshot_from_2021-02-13_13-35-12_4ac515d38b9e48776f1467b2b472c2f6.png)




 Ilmselt näed, et ükski sõlm praegu selles rubriigis sõnumeid ei kuuluta, aga üks sõlm (täpsemini fake\_driver\_node) tellib cmd\_vel rubriigist sõnumeid. See on ka loogiline, sest käivitasime enne roboti digikaksiku, aga ei ole veel kuulutanud sõnumeid, mis ütleksid sellele, kuidas liikuda.









### [**5. Rubriikide uurimine, 2. osa**](#)

Käivitame sõlme, mis oskab saata robotitele liikumiskäske:




```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```


 Saame uues terminaliaknas kasutada rosnode info käsku, et uurida, mis rubriikidega see uus sõlm suhtleb: rosnode info /teleop\_twist\_keyboard.




![.](https://sisu.ut.ee/sites/default/files/rosak/files/screenshot_from_2021-02-13_13-37-54_b7e62393f9b78de644c95c432b375d25.png)




 Näeme, et meie käivitatud sõlm kuulutab sõnumeid selles samas rubriigis, millelt fake\_driver\_node sõnumeid tellib: cmd\_vel rubriigis. See tähendab, et nüüd saame me roboti digikaksikule sõnumeid saata.




 Järgi juhiseid, mis on kuvatud terminaliaknas, kus käivitasid teleop\_twist\_keyboard sõlme. Kui see aken on aktiivne ja vajutad klaviatuuril õigeid klahve, näed RVizi aknas robotit liikumas.




> 
> 
>  Kui robot peaks RVizi aknas ära kaduma, võib tema otsimisest lihtsam olla fake\_driver uuesti käivitada (vt sammu 1).
>  
> 
> 
> 








### [**6. Millised on ROSi sõnumid?**](#)

ROSi sõnumid on andmestruktuurid, mis sisaldavad informatsiooni. Sõnumid on need andmed, mida sõlmed üksteisele saadavad.




 Igal ROSi sõnumil on kindel tüüp. Nägemaks, mis tüüpi sõnumeid igas rubriigis vahetatakse, saab kasutada tööriistu rostopic type ja rostopic info. Näiteks cmd\_vel rubriigis vahetatakse tihti kasutatavaid geometry\_msgs/Twist tüüpi sõnumeid.




 Lähme sügavamale ja uurime, milline näeb välja geometry\_msgs/Twist tüüpi sõnum. Selleks kasutame rosmsg tööriista. Sisesta käsk:




```
rosmsg info geometry_msgs/Twist
```


 Uuri käsu väljundit.






