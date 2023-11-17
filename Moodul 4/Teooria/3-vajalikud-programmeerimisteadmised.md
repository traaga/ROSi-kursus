



 3. Vajalikud programmeerimisteadmised
=======================================











> 
> 
> **Selles moodulis hakkame kirjutama koodi Pythoni programmeerimiskeeles. Selle jaoks on vaja natuke osata Pythoni koodi kirjutada.**
> 
> 
> 
> 



 Õnneks ei ole teemade nimekiri, mida programmeerimise koha pealt vaja läheb, väga pikk.




 Kui sul vastavad teadmised juba olemas on, siis võid selle osa vahele jätta.




### [**Muutujad**](#)

Muutujad on nimed, mida saame anda erinevatele väärtustele. Näiteks:




```
x = 5
```


 Muutujale antakse väärtus alati ülalkirjeldatud süntaksiga: keskel on üks võrdusmärk, sellest vasakul pool on muutujanimi ja paremal pool väärtus, mida talle anda tahame. Nüüd, kui viitame kusagil väärtusele x, siis käsitletakse seda kui arvu 5. Näiteks:




```
y = x + 2
```


 Siin määratakse y väärtuseks x-ist kahe võrra suurem arv ehk 7.




> 
> #### 
>  Aritmeetilised tehted
> 
> 
> 
> Arvuti saab hästi aru aritmeetilistest tehetest +, -, \* ja /. Tehete järjekorda saab määrata sulgudega. Lisaks on Pythonis veel võimalik teha mitmeid aritmeetilisi operatsioone, nagu näiteks astendamine (seda tehakse kahe järjest pandud korrutusmärgiga \*\*, näiteks 2\*\*4 võtab 2 astmesse 4) ja jäägi leidmine mingi arvuga jagamisel (seda tehakse märgiga %, näiteks 100%7 leiab jäägi, mille saame arvu 100 jagamisel arvuga 7).
> 
> 
> 
> 



 Muutujanimed võivad olla ka pikemad kui lihtsalt ühetähelised, näiteks võib muutujaks olla roboti\_rataste\_arv.




```
roboti_rataste_arv = 3
```


 Muutuja väärtust võib ka muuta. Seda saab muuhulgas teha teistele muutujatele või isegi muutujale endale viidates. Näiteks:




```
roboti_rataste_arv = roboti_rataste_arv - 1
```


 Sellel real vaatab arvuti kõigepealt parempoolset osa. Muutuja roboti\_rataste\_arv väärtus on alguses 3, selles lahutatakse 1 ja tulemus (2) pannakse tagasi muutujasse roboti\_rataste\_arv ("kirjutatakse üle"). Selle tulemusena on muutuja roboti\_rataste\_arv väärtus nüüd hoopis 2.




 Muutujate kohta saad rohkem õppida näiteks siit: <https://courses.cs.ut.ee/2023/progmaa/spring/Main/PARTIIMuutujad>









### [**Valikulaused**](#)

Programmi käivitades järgib arvuti juhiseid üldjuhul järgemööda ülalt alla. Näiteks:




```
x = 1
x = 2
```


 Nendel kahel real määratakse muutuja x väärtuseks kõigepealt 1 ja seejärel 2. Programmi käivitamise lõpuks on x väärtus 2 ning see, et see oli vahepeal ka 1, on praegu lihtsalt ära unustatud.




 Mõnikord aga soovime, et arvuti teeks ühel juhul üht asja ja teisel juhul teist. Näiteks võime tahta, et mingisuguse muutuja roboti\_kiirus väärtus oleks kolme või vähema rattaga roboti puhul ühesugune ja nelja või rohkema rattaga roboti puhul teistsugune. Seda saame saavutada valikulausega:




```
if roboti_rataste_arv < 4:
    roboti_kiirus = 300
else:
    roboti_kiirus = 350
```


 Siin koodis vaadatakse kõigepealt, kas roboti rataste arv on väiksem kui 4. Kui nii, siis tehakse kõike, mis järgneb if-reale ja on sellest suurema **taandega** (hetkel üks rida, kus muutuja roboti\_kiirus väärtuseks pannakse 300). Kui roboti rataste arv aga ei ole väiksem kui 4, siis tehakse kõike, mis on reale else: järgnevas osas suurema taandega (jälle üksainus rida, kus muutuja roboti\_kiirus väärtuseks pannakse 350).




 Taane peaks olema alati sama: siin oleme kasutanud täpselt nelja tühikut.




else-osa ei ole kohustuslik: viimased kaks rida näitest võib ka ära jätta ja arvuti ei nurise (kuigi kood ei tee siis ka enam sama asja).




> 
> #### 
>  Mis tingimusi ma ette anda saan?
> 
> 
> 
>  Matemaatikast on tuttavad märgid < ja >, mida ka arvuti mõistab. Arvuti teab ka märke <= ja >=, mis on vastavalt "väiksem kui või võrdne" ja "suurem kui või võrdne". Kui tahame kontrollida, kas mingid väärtused on täpselt võrdsed, siis saame seda teha == (kahe järjestikuse võrdusmärgiga) - kaks on neid sellepärast, et üht kasutatakse muutujale väärtuse andmiseks.
>  
> 
> 
> 
>  Lisaks sellele saab kasutada näiteks sõnu and, or ja not. Näiteks:
>  
> 
> 
> 
> ```
> (x < 5 and (not x == 2)) or x == 100
> ```
> 
> 
>  See rida on tõene siis, kui x on väiksem kui 5 (aga tema väärtus ei tohi olla täpselt 2) või kui ta on täpselt 100.
>  
> 
> 
> 



 Rohkem saad valikulausete kohta lugeda näiteks siit: <https://courses.cs.ut.ee/2023/progmaa/spring/Main/PARTIIIValikulause1>









### [**Tsüklid**](#)

Mõnikord soovime midagi teha mitu korda (näiteks 100 korda). Seda on mugav teha tsükliga. Üks tsükli liik on while-tsükkel.




```
x = 1
while x <= 100:
    x = x + 1
```


 Siin antakse kõigepealt muutuja x väärtuseks 1 ja siis liigutakse tsüklisse. Tsükli alguses vaadatakse, kas x on väiksemvõrdne 100st (on küll) ja kui nii, siis käivitatakse read, mis asuvad tsükli "sees" ehk järgnevad while-reale ja on sellest suurema taandega. (Siin suurendatakse x väärtust 1 võrra.)




 Seejärel minnakse tsükli algusesse tagasi ja võrreldakse uuesti: kas x on väiksem kui või võrdne 100ga? (x väärtus on nüüd 2, seega jah, on küll.) Ning korratakse tsükli sisu. Seejärel minnakse algusesse uuesti tagasi ja võrreldakse x väärtust uuesti. Seda tehakse seni, kuni x <= 100 enam ei kehti: see juhtub, kui x väärtuseks saab 101. Kokkuvõttes korratakse tsüklit 100 korda.




 See tsükkel on suhteliselt mõttetu, sest midagi muud peale x väärtuse suurendamise ta ei tee. Lisame koodile veel kaks rida:




```
x = 1
summa = 0
while x <= 100:
    summa = summa + x
    x = x + 1
```


 Nüüd on meil ka teine muutuja, nimega summa. Iga kord tsüklit läbides suureneb muutuja summa väärtus x võrra. Kuna x väärtused on järjest 1, 2, ..., 100, siis liidab see kood kokku arvud 1 kuni 100 ja lõpptulemus on muutujas summa.




 Tsükli tingimused saavad olla ka teistsugused ja järgivad üldiselt samu ideid, nagu valikulausete omad.




 Rohkem saad tsüklite kohta lugeda näiteks siit: <https://courses.cs.ut.ee/2023/progmaa/spring/Main/PARTVTsykkel1>









### [**Funktsioonid**](#)

Viimaseks vaatame funktsioone. Funktsioon lubab meil panna arvuti tegema keerulisemaid operatsioone kui lihtsalt millegi liitmine või lahutamine, hoides samal ajal koodi arusaadava ja loetavana.




 Funktsioonist võib mõelda kui mustast kastist, mis teeb midagi. Mõnikord on võimalik funktsioonile anda mingit sisendit (üks või rohkem) ja mõnikord annab funktsioon pärast töö lõpetamist midagi ka välja.




 Funktsiooni tunneb Pythonis ära selle järgi, et tal on nimi (nagu muutujal), millele järgnevad kohe sulud ( ja ). Mõnikord on sulgude vahel midagi kirjas, mõnikord mitte: sinna vahele kirjutatakse funktsiooni sisendid (kui neid on).




 Näiteks võime vaadata väga lihtsat (väljamõeldud) funktsiooni liida\_kolm\_arvu:




```
liida_kolm_arvu(3, 5, 11)
```


 See funktsioon võtab kolm sisendit (hetkel on talle ette antud arvud 3, 5 ja 11) ning võiks nime järgi välja anda nende kolme arvu summa (19). Ülalolevat rida nimetatakse funktsiooni **väljakutseks**. Hetkel võime tahta tulemusega hiljem ka midagi teha: kui funktsioon midagi "välja annab" (**väärtuse tagastab**), siis saame selle salvestada muutujasse:




```
meie_summa = liida_kolm_arvu(3, 5, 11)
```


 Siin pannakse funktsiooni **tagastatav väärtus** muutujasse meie\_summa.




 Funktsiooni liida\_kolm\_arvu pole aga vaikimisi tegelikult olemas (kuigi paljud teised funktsioonid on). Funktsiooni saame ise luua sõnaga def ja sobiva taandega järgmiselt:




```
def liida_kolm_arvu(a, b, c):
    summa = a + b + c
    return summa
```


 See koodijupp loob (defineerib) funktsiooni liida\_kolm\_arvu (aga **ei kutsu seda välja**) ehk annab arvutile juhised, mida selle funktsiooni väljakutse puhul teha. Funktsioonil on kolm sisendit: sisendiks antu pannakse kolme muutujasse, nimedega vastavalt a, b ja c (seda tehakse funktsiooni väljakutsel automaatselt - arvuti oskab sisendiks antud kolm arvu järjekorras kokku viia muutujatega a, b ja c). Seejärel liidetakse need kolm arvu kokku ja pannakse tulemus muutujasse summa. Lõpuks annab käsk return teada, et funktsioon peaks tagastama leitud summa.




 (Vahemärkusena: muutujaid a, b, c ja summa väljaspool funktsiooni väljakutset sel juhul enam olemas ei ole - nad luuakse ainult selleks ajaks ja selles kohas.)




 Nüüd saab seda funktsiooni päriselt kasutada. Kokku näeks tüüpiline kood välja näiteks selline:




```
def liida\_kolm\_arvu(a, b, c):
 summa = a + b + c
 return summa

meie_arvude_summa = liida_kolm_arvu(3, 5, 11)

rospy.loginfo(meie_arvude_summa)
```


 See kood defineerib kõigepealt kolme arvu kokkuliitmise funktsiooni, siis kutsub seda välja arvudega 3, 5 ja 11, paneb tulemuse muutujasse meie\_arvude\_summa ning kutsub seejärel välja veel üht funktsiooni rospy.loginfo (täpsemini funktsiooni loginfo moodulist rospy), millele annab sisendiks meie\_arvude\_summa (mis praegu on 19). See viimane funktsioon on ROSis juba olemas (koodi alguses tuleb küll see importida - näeme hiljem, kuidas seda päriselt teha) ja see funktsioon kuvab meie arvude summa terminalis, kus vastav ROSi kood käivitati.




 (Kui kasutada midagi muud, kui ROSi, siis on kõige tüüpilisemaks info kuvamise meetodiks funktsioon print, mis töötab samamoodi.)




 Funktsioonide kohta saad rohkem lugeda näiteks siit: <https://courses.cs.ut.ee/2023/progmaa/spring/Main/PARTVIIFunktsioon1>








