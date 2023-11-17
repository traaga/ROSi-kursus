



 Kodutöö. Ratasroboti simuleeritud juhtimine
=============================================











> 
> 
> **Selles harjutuses paneme kokku eelnevalt õpitu: loome käivitusfaili, mis kuvab eelnevalt loodud parametriseeritud neljarattalist robotit ja lubab sellega ka simulatsioonis ringi sõita.**
> 
> 
> 
> 
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



### [**Kirjelduse täiendamine**](#)

Ava RVizis eelnevalt loodud täielikult parametriseeritud neljarattaline robot. Hetkel on see suhteliselt paigalseisev robot. Väikeste häkkidega saame aga sellegi roboti panna RVizi aknas ringi sõitma. Selleks kasutame sõlme nimega fake\_driver\_node, mille abil oleme tegelikult juba varem robotondi robotiga RVizi aknas ringi sõitnud.




fake\_driver\_node otsib lüli nimega base\_footprint ning juhib seda. Seega on meil vaja roboti sõidutamiseks luua sellise nimega lüli ja ühendada see sobiva liigendi abil robotiga.




Ava fourwheeler.urdf.xacro fail ja täienda seda, luues ilma välise ilmeta (st ilma visual märgendita) lüli nimega base\_footprint. Ühenda see liikumatu liigendi abil roboti kere lüliga base\_link nii, et liigendi ülemlüli oleks base\_footprint, alamlüli base\_link ning et base\_footprint asetseks roboti all, rataste alumise servaga samal kõrgusel “maas”.




Testi uut kirjeldust, kuvades neljarattalist sõidukit uuesti RVizi abiga.









### [**Roboti juhtimine**](#)






 Kuva RVizis uuesti oma neljarattalist robotit (või kui seda pole vahepeal seisma pandud, siis ära seda ka praegu seiska).




Selleks, et robotit päriselt klaviatuurilt juhtida, peab lisaks roboti kuvamisele käivitama ka sõlme, mis suudab simuleerida roboti liikumist. Selle nimi on fake\_driver\_node ja ta asub kimbus robotont\_driver. Käivita see sõlm uues terminaliaknas.




Nüüd peaksid saama seada RViz akna vasakus servas “Displays” paneelis “Fixed Frame” väärtuseks “odom”, nagu näidatud pildil:  
![.](https://sisu.ut.ee/sites/default/files/rosak/files/kuvatommis_2022-10-10_22-58-58.png)




Viimase asjana käivita veel ühes terminaliaknas juba tuttav sõlm teleop\_twist\_keyboard.py kimbust teleop\_twist\_keyboard ja sõida robotiga ringi.









### [**Käivitusfaili tegemine**](#)

Kõigi nende sõlmede eraldi käimapanemine eri terminaliakendes on natuke tobe. Nüüd on meil aga ka tegelikult piisavalt oskusi, et luua üks käivitusfail, mis seda kõike korraga teeb - siis saame käivitada ainult selle.




Viimase asjana loogi kõigi nende sõlmede samaaegselt käimapanemiseks uus käivitusfail. See käivitusfail peaks:



* Laadima parameetriserverisse roboti kirjelduse
* Käivitama RVizi konfiguratsioonifailiga, mis kuvab täielikult parametriseeritud robotit
* Käivitama sõlme robot\_state\_publisher kimbust robot\_state\_publisher
* Käivitama sõlme joint\_state\_publisher\_gui kimbust joint\_state\_publisher\_gui
* Käivitama sõlme fake\_driver\_node kimbust robotont\_driver
* Käivitama sõlme teleop\_twist\_keyboard.py kimbust teleop\_twist\_keyboard



Loo vastav käivitusfail ning testi seda, sulgedes kõik ROSi sõlmed ning käivitades siis kõik vajalikud ühekorraga käivitusfaili abil.




**Tee ka robot vähemalt ühe meetri jagu laiemaks ja muuda peale selle XACRO failis veel üht vabalt valitud parameetrit!**




**Lõpptulemus peaks välja nägema umbes järgmine** (siin ei ole robotit laiemaks tehtud)**:**













 
