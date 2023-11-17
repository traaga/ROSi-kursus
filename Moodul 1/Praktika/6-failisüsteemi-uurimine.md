



 6. Failisüsteemi uurimine
===========================











> 
> **Selles harjutuses õpid kasutama failibrauserit, vaatama peidetud faile ja saad teada, kus asuvad süsteemis ROSi failid. Lood kodukausta kataloogi nimega linux\_intro, selle sisse tekstifaili test.txt (sisu pole oluline) ning alamkataloogi new, mille sees on koopia failist test.txt nimega copy.txt.**  
> *Samm-sammulise juhendi vaatamiseks klikka harjutuse vahepealkirjadele.*
> 



### [**1. Failibrauseriga navigeerimine.**](#)

Ava kaustade vaatamise rakendus, mida kasutasime eelmises ülesandes. Peaksid nägema akent, mis sarnaneb allolevale. Ikoonid ja tekst akna ülemises servas näitavad lahtioleva kausta asukohta failisüsteemis.




![Vaade kodukataloogist](https://sisu.ut.ee/sites/default/files/rosak/files/kodukataloog.png)




 Ikoonid akna ülaservas moodustavad failibrauseri "aadressiriba". Aadressiriba peidab vaikimisi kahjuks akna täpset asukohta. Näed seda asukohta, kui vajutad klahve Ctrl+L. Peaksid nägema, kuidas aadressiriba muutub allpool näidatud tekstikastiks:




![Failibrauseri aadressiriba](https://sisu.ut.ee/sites/default/files/rosak/files/aadressiriba.png)




 Failibrauser avab vaikimisi kasutaja **kodukataloogi**. Selle kataloogi nimi on tüüpiliselt /home/<kasutajanimi>. See kataloog on turvalisuse huvides ainus, millele kasutajale on täielik ligipääs.




**Jäta meelde, mis on kodukataloog - sellele hakkame edaspidi palju viitama.**




 Vaikimisi ei näidata kaustades peidetud faile (failed, mille nimed algavad punktiga) ega “tagavarakoopia” faile (failid, mis lõppevad ~ märgiga). Nende failide nägemiseks vajuta Ctrl+H. Nüüd peaksid nägema kõiki peidetud faile. Nende uuesti peitmiseks vajuta uuesti sama klahvikombinatsiooni (Ctrl+H).




 Akna vasakus servas näed mõningaid lühiteesid irdseadetele, teistele kõvaketastele, järjehoidjatele jms. Vali Muud asukohad / Other Locations ja seejärel tee topeltklõps kaustal Arvuti / Computer. See viib sind süsteemi juurkataloogi, mille nimi on /. Kõik failid selles arvutis on selle kausta alamkataloogides.




 Tee topeltklõps kaustal opt, seejärel kaustal ros. Siin asub kogu ROSi tarkvara. Iga ROSi versioon on eraldi kaustas: näed seal kausta noetic. Selle sees on setup.bash fail, mida kasutame hiljem ROSi seadistamiseks terminalis. Programmid, andmed jmt on bin ja share kataloogides. Sul ei ole enamasti tarvis ühtegi selles kaustas olevatest failidest kuidagi muuta, kuid on hea teada, kus nad asuvad.









### [**2. Muudatuste tegemine.**](#)

Järgmiseks õpid looma, muutma, ümber nimetama ja eemaldama faile ja katalooge.




**a. Sisene kodukataloogis kataloogi catkin\_ws ja loo selle sisse omakorda alamkataloog linux\_intro. Selleks:**




 i. Liigu failibrauseris kodukataloogi.  
ii. Liigu topeltklõpsuga selle sees kataloogi catkin\_ws.  
iii. Tee akna põhiosa sees paremklõps ja vali Uus kataloog / New folder.  
iv. Pane kataloogi nimeks linux\_intro ja vajuta klahvi "enter”.




**b. Loo uues kaustas linux\_intro fail test.txt. Selleks:**




 i. Ava tekstiredaktor ja sisesta faili üks suvaline lause.  
ii. Vajuta tekstiredaktori nuppu Salvesta / Save.  
iii. Avanenud aknas navigeeri kausta linux\_intro ja anna faili nimeks test.txt (seda saab teha akna ülaosas). Vajuta uuesti rohelist nuppu "Salvesta”.  
iv. Näed failibrauseri aknas, et tekkinud on uus fail.




**c. Tee failist koopia. Selleks:**




 i. Vali failibrauseri aknas äsjaloodud fail. Vajuta klahvikombinatsiooni Ctrl+C, et asetada koopia failist lõikepuhvrisse.  
ii. Vajuta klahvikombinatsiooni Ctrl+V, et luua failist aktiivsesse kausta uus koopia.




**d. Anna koopiale uus nimi. Selleks:**




 i. Tee uuel failil paremklõps ja vali Muuda nime… / Rename…  
ii. Sisesta uueks nimeks copy.txt ja vajuta klahvi “enter”.




**e. Loo kaust new. Selleks:**




 i. Tee paremklõps failibrauseri akna põhiosas ja vali Uus kataloog / New folder.  
ii. Anna sellele nimi new.




**f. Liiguta fail copy.txt kataloogi new, lohistades faili copy.txt vasakut hiirenuppu all hoides kausta new peale.**




**g. Kopeeri fail test.txt kausta new, hoides all Ctrl-klahvi ja lohistades vasakut hiirenuppu all hoides fail test.txt kausta new peale.**




**h. Sisene kausta new ja kustuta fail test.txt, valides faili ja vajutades klaviatuuril Delete-klahvi.**



 


