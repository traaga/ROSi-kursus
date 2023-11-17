



 10. Linuxi terminal: failide muutmine
=======================================











> 
> 
> **Selles harjutuses õpid kasutama järgmiseid Linuxi terminali käske: mv, cp, rm, mkdir. Harjutus eeldab, et oled läbinud Linuxi terminali navigatsiooniharjutuse.**  
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 
> 
> 
> 



### [**1. Failide muutmine: käsk mv**](#)

  
Käsku mv saab kasutada failide liigutamiseks (“**m**o**v**e”) ja ümbernimetamiseks.




 Alustamiseks peaksid terminaliga olema kaustas linux\_intro, mis sai loodud terminali navigatsiooniharjutuses. Kasuta käsku cd sinna liikumiseks.




**a. Sisesta mv test.txt test2.txt ja seejärel ls.**  
Näed, et fail test.txt on ümber nimetatud failiks test2.txt.




**b. Sisesta mv test2.txt new ja seejärel ls.**  
Faili test2.txt ei ole enam näha.




**c. Liigu kataloogi new kasutades käsku cd new, seejärel lase terminalil loetleda antud kataloogis olevad failid.**  
Näed, et fail test2.txt on liigutatud siia.




**d. Sisesta käsk mv test2.txt ../test.txt, seejärel ls.**  
Näed nüüd, et fail test2.txt on jälle kadunud.




**e. Sisesta cd .., liikudes tagasi kataloogi linux\_intro, ja seejärel ls.**  
Viimane mv käsk tegi kaht asja korraga: see muutis faili asukohta ja nimetas ta ümber, nii et lõpptulemusena on meil jälle fail test.txt.




### [**2. Failide muutmine: käsk cp**](#)

  
Käsuga cp saab failidest koopiaid teha (“**c**o**p**y”).




**a. Sisesta käsk cp test.txt new/test2.txt. See loob failist test.txt koopia kausta new nimega test2.txt.**  
Kataloogi new sisu nägemiseks võid kasutada käsku ls new.




**b. Sisesta käsk cp test.txt “test copy.txt” (jutumärgid on ka olulised). Seejärel kasuta käsku ls, et näha, mis juhtus.**  
Näed, et failist test.txt on loodud koopia nimega test copy.txt, kusjuures uue faili nime sees on tühik.  
Jutumärgid on olulised, et arvuti segadusse ei läheks, kui failinimes on tühikuid või muid erilisi märke.




### [**3. Failide muutmine: käsk rm**](#)

  
Käsuga rm saad faile kustutada (“remove”).




**Sisesta käsk rm “test copy.txt”, seejärel loetle aktiivse kataloogi sisu.**  
Näed, et faili test copy.txt seal enam ei ole.




### [**4. Failide muutmine: käsk mkdir**](#)

  
Käsuga mkdir saad luua uusi katalooge (“**m**ake **dir**ectory”).




**Sisesta käsk mkdir new2, seejärel ls.**  
Näed nimekirjas uut alamkataloogi nimega new2.




> 
> 
>  Käskude cp, mv ja rm lõppu võid soovi korral lisada ka lipu -i,  mis paneb terminali Sinult kinnitust küsima, kui käsk kirjutaks üle või kustutaks mõne olemasoleva faili.
> 
> 




