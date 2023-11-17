



 Kodutöö. Pööra markerite vahel
================================











> 
> 
> **Siin harjutuses saad oma seniõpitud teadmised proovile panna. Pane robot end kahe markeri vahel pöörama.**
> 
> 
> 
> 
>  Harjutuse läbimiseks on vaja robotit ja kaht AR markerit, mis on asetatud seintele roboti lähedal.
>  
> 
> 
> 



 Kirjuta kood, mis leiaks seinte pealt üles kaks AR markerit, ja keeraks robotit nende vahel. See tähendab: robot peaks end keerama ühes suunas seni, kuni näeb otsitavat markerit. Seejärel peaks robot hakkama otsima teist markerit ja keerama end teises suunas, kuni selle leiab.




 Näide roboti käitumisest on siin videos:









### [**Kui oled kinni jäänud, ei oska koodi struktureerida ja soovid vihjet, siis vaata siia**](#)

Siin pakume ühe koodistruktuuri, millest võid oma lahenduse luua. Siin on palju asju puudu - sinu ülesanne on vajalikud lüngad täita.




```
#!/usr/bin/env python3
# siin peaks importima kõik vajaliku

# siin on tegemist globaalse muutujaga
# see tähendab, et sellele muutujale saavad ligi kõik funktsioonid
# ning kui nad soovivad seda muuta, siis tuleb funktsiooni alguses talle seda öelda
# vt allpool, kuidas seda on tehtud
leitud_markeri_ID = None

def ar_message_handler(data):
    global leitud_markeri_ID

    if len(data.markers) > 0:
        for marker in data.markers:
            rospy.loginfo("Detected marker with ID " + str(marker.id))
            # siin on hea koht, kus salvestada leitud markeri ID
            # muutujasse leitud_markeri_ID
    else:
        rospy.loginfo("No AR markers detected.")

def main():
    global leitud_markeri_ID
    
    # siin peaks toimuma sõlme initsialiseerimine
    # ning kuulutaja ja tellija loomine
    
    otsitava_markeri_ID = 1 # siin muutujas võib hoida endale sobiva markeri ID-d
    
    # lisaks võiks siin paika panna, mis sagedusega while-tsükkel jookseb
    
    while not rospy.is_shutdown():
        # siin tuleks teha kõike, mida soovime pidevalt korrata
        # näiteks võrrelda leitud markeri ID-d selle markeri ID-ga, mida otsime
        # vajadusel vahetada ära markeri ID, mida otsime
        # ja kuulutada roboti liigutamiseks sobivat sõnumit
        # lõpuks võiks tsükli lõpus ka veidi aega "magada"

if __name__=='__main__':
    try:
        main()
    except rospy.ROSInterruptException:
        pass
```


> 
> #### 
>  Globaalsed muutujad?
> 
> 
> 
>  Ülalolev kood kasutab **globaalseid muutujaid** (*global variables*). See on efektiivne lahendus, kuigi mitte väga hea koodipraktika suuremates arendustes. Kui soovid nende kohta rohkem teada, siis võid Internetist infot otsida - siin proovisime kõik vajaliku nende kasutamiseks ette anda.
>  
> 
> 
> 
>  Kui aga oled arendajataustaga ja ei soovi globaalseid muutujaid kasutada (sest nad on kurjast), siis võid vabalt kasutada ka mõnd muud lahendust. Moodul 2 käigus kasutatud porgandiotsimise kood väldib klasside abil globaalseid muutujaid.
>  
> 
> 
> 







 




