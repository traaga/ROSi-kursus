



 1. Isetoimetavad robotid
==========================











> 
> 
> **Oleme pannud roboti sooritama nii mõndagi ülesannet, aga need on kõik olnud suhteliselt lihtsad. Päris maailm on tavaliselt kordades keerulisem. Kuidas üks robot selles segaduses ise hakkama saab?**
> 
> 
> 
> 



Esiteks tuletame meelde, et 4. moodulis panime roboti küll iseseisvalt liikuma, ent roboti juhtimine käis sisuliselt stopperi abil (me mõõtsime aega) ning taoline robot ei oma mitte mingit arusaama sellest, kus ta parajasti paikneb. Nt võime 4. moodulis programmeeritud roboti tõsta mistahes tasapinnale ja kui seal on piisavalt ruumi, siis sõidab robot oma ruudu ära. Kui aga paneme roboti teele mõne takistuse, siis robot sõidab sellele otsa ning ilmselt ei meenuta roboti liikumine selle tulemusena enam ruudukujulist mustrit.




5. mooduli võimaldasime robotil maailmas leida märgised, mille abil hinnata oma asukohta nende märgiste suhtes. See võrdlemisi pisike lisandus meie roboti võimetele muutis tegelikult kogu roboti juhtimise oluliselt intelligentsemaks, sest nüüd oli võimalik robotil päriselt aru saada, kas liigub päriselt ka nii nagu programm eeldab. Muide, kui kasutame telefonis GPS-i abil oma asukohta tuvastamist, siis sisuliselt teeme sama asja, mida meie robot AR-märgiste abil. Lihtsalt GPS süsteemis on märgisteks planeedi orbiidil tiirutavad satelliidid, mida siis meie nutitelefon raadiolainete abil “näeb”.




Robootikas räägime autonoomse isejuhtiva roboti puhul mitmest tehnilisest lahendusest samal ajal ning käesolevaga proovimegi selle terminoloogia näppude peale lahti võtma. Esiteks vajab isejuhtiv robot algoritmi, mis planeerib teekonna roboti hetke asukohast sihtpunkti - seda protsessi nimetatakse **rajaplaneerimiseks** (ingl *path planning*).




![.](https://sisu.ut.ee/sites/default/files/rosak/files/navigation.gif)




Lisaks sellele, et juhtida robot sihtpunkti, peab rajaplaanimine tagama, et robot põikaks mööda mistahes takistustest, mis tema teele jäävad. Selleks vaja rajaplaneerimisalgoritm kaarti (*map*), kus on üheselt selge, millistel aladel roboti tohib viibida ja millistel mitte. Näiteks must värv määrab keelutsoone ja valge/hall määratleb robotile liikumiseks vabad alad. Taoliste kaartide loomine (*mapping*) on üks väljakutse, millega isejuhtivate robotsüsteemi loojad igapäevaselt rinda pistavad.




Kui robotil on olemas rajaplaneerimisalgoritm ja kaart, siis peab veel edukaks tegutsemiseks aru saama, kus robot antud kaardil ja oma teekonnal paikneb. Roboti asukoha automaatne tuvastamine kannab nimetust lokaliseerimine (*localization*). Tihtilugu ei ole roboti kaart aga täielik ning seetõttu räägime isegi samaaegsest lokaliseerimisest ja kaardistamisest, mida inglise keele eeskujul nimetame SLAMiks (*simultaneous localization and mapping*).




Ja nagu aimata võime, siis on kõigi nende ülesannet (st rajaplaneerimise, kaardistamise ja lokaliseerimise) jaoks ROSis vajalikud võimekused mitmete kimpude näol.



 







