



 3. Kinemaatika ROSis
======================











> 
> 
> Nagu paljude muude robootika peamiste ehituskividega, pakub ROS meile ka robotite kinemaatika kirjeldamiseks standardiseeritud töövahendeid. Robotite kinemaatika kirjeldamiseks saame kasutada töövahendit nimega **URDF (*Unified Robot Description Format*****)**. URDF on keel, mille abil saame kirjeldada, **millistest lülidest** robot koosneb ning **kuidas** need lülid teineteise suhtes **liiguvad**. Kuna ROSi üks juhtmõte on maksimaalselt ära kasutada olemasolevat, siis tugineb URDF ülilevinud märgenduskeelele XML (eXtensible Markup Language).
> 
> 
> 
> 
> *Õppematerjali vaatamiseks klikka vahepealkirjadele.*
> 
> 
> 
> 



### [**XMLi põhitõed**](#)

ROSis on meie eesmärk jõuda võrdlemisi kiiresti XMLi kasutamiseni, seega ei pea me esialgu süübima väga sügavale, et mõista, mis on XML. Oluline on jätta meelde, et tänu XMLile saame arvutite jaoks info struktureerida ja anda sellele konteksti. Seda tehakse, kasutades infot ennast ning seda raamivat metainfot.




Võtame näiteks ühe isiku Roberta, kes on 42 aastat vana. Mis infot ja ja metainfot saame sellest lausest välja võtta? Teeme näiteks sellise tabeli:





| 
 Metainfo
  | 
 Info
  |
| --- | --- |
| 
 Nimi
  | 
 Roberta
  |
| 
 Vanus
  | 
 42
  |



Et sama info panna kirja xml-faili, võime avada lihtsa tekstifaili ja kirjutada sinna:




```
<nimi>Roberta</nimi>
<vanus>42</vanus>
```


Nagu näeme, siis metainfo on nurksulgude <> vahel. Ka märkame, et info alguse ja lõpu piiritlemiseks on metainfo märgendeid alati kaks: <nimi> (avanev märgend) ja </nimi> (sulgev märgend, mida tähistab /-märk pärast esimest nurksulgu). Sedasi on alati ühemõtteliselt selge, et nende kahe märgendi vahel on kirjas nimi.




Taolise märgendamise jõud muutub aga eriti ilmseks, kui avastame, et märgendid saab grupeerida täiendavate märgendite abil. Hetkel on eespool toodud näite <nimi> ja <vanus> lihtsalt kaks rida, mida ei seo omavahel miski, aga kui grupeerime nt <isik>-märgendi abil, saame kirjeldada eri isikute omadusi. Alljärgnev struktuur ütleb meile, et nii <nimi> kui ka <vanus> käivad ühe ja sama isiku kohta, sest <isik> märgend suletakse (</isik> märgendi abil) alles pärast nime ja vanuse kirjeldamist.




```
<isik>
 <nimi>Roberta</nimi>
 <vanus>42</vanus>
</isik>
```


Kui selline info esitlus võib inimesele tunduda tüütu, siis masinate jaoks muutub pilt ühemõtteliseks. See aga tagab selle, et masinad saavad infost “õigesti” aru. 









### [**URDFi põhitõed**](#)

Kui XML on mõeldud mistahes info märgendamiseks, siis URDF kasutab XML-i, et saavutada ühtne moodus robotite kinemaatika kirjeldamiseks. Seda kirjeldust saavad siis vajadusel kasutada kõik need ROSi sõlmed, mis peavad lähtuma roboti kinemaatikast. Seega on URDF mõeldud ainult üheks konkreetseks ülesandeks ning ta kasutab selleks XML-i.




URDF-i abil soovime kirjeldada kõik robotite lülid ja nende vahelised liigendid. Igal lülil saab olla teatavaid omadusi ning igal liigendil saab olla mingi kogus omadusi, kuid kõige laiemas plaanis järgib roboti URDF-kirjeldus järgnevat struktuuri:




```
<robot name="minu\_robot">
 <link> ... </link>
 <link> ... </link>
 <link> ... </link>
 <joint> ... </joint>
 <joint> ... </joint>
 <joint> ... </joint>
</robot>
```


Nagu näeme, siis robot koosneb kindlast arvust lülidest (ingl *link*) ja liigenditest (*joint*). Ja kõik, mis tuleb täpsustavalt kirjeldada iga lüli ja liigendi jaoks, peab masinale looma tervikliku pildi selle kohta, milline näeb iga lüli välja ja kuidas liigend võimaldab kahel erineval lülil omavaheliselt liikuda. Just seda teadmist hoiamegi endaga kaasas, kui hakkame järgnevalt robotite URDF-kirjelduste loomist harjutama.








 


