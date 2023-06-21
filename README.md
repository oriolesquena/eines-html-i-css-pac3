Eines HTML i CSS -- PAC 3 – 25/06/2022 -- Documentació - Fet per Oriol Esquena (oesquena@uoc.edu)

**ENLLAÇOS REPOSITORI I PUBLICACIÓ**

El codi s'ha publicat a GitHub, al següent enllaç: [https://github.com/oriolesquena/eines-html-i-css-pac3](https://github.com/oriolesquena/eines-html-i-css-pac3)

La publicació s'ha fet amb Netlify i s'ha publicat en el següent enllaç: [https://tangerine-lebkuchen-d63ec2.netlify.app/index.html](https://tangerine-lebkuchen-d63ec2.netlify.app/index.html)

1. **TAULA VEOLICITATS DE CÀRREGA**

Per tal d'evitar URL molt llargues, la URL base del projecte és: [https://dainty-licorice-850b4d.netlify.app/](https://dainty-licorice-850b4d.netlify.app/). A la taula s'afegeix només el nom del fitxer HTML i l'enllaç.

| **Títol** | **URL** | **Temps de càrrega (mitjà)**
**(Mòbil/PC)** | **Pes total**
**(Mòbil/PC)** | **Pes transferit**
**(Mòbil/PC)** | **Quantitat de recursos**
**(Mòbil/PC)** |
| --- | --- | --- | --- | --- | --- |
| Portada | [/index.html](https://dainty-licorice-850b4d.netlify.app/index.html) | 6.23s / 7.71s | 680 / 863 kB | 514 / 696 kB | 12 / 12 requests |
| Història i formació | [/historia.html](https://dainty-licorice-850b4d.netlify.app/historia.html) | 11.88s / 12.96s | 4.1 / 4.4 MB | 1.6 / 1.7 MB | 32 / 34 requests |
| Volcans i llocs d'interès | [/volcans.html](https://dainty-licorice-850b4d.netlify.app/volcans.html) | 7.22s / 7.50s | 817 / 830 kB | 650 / 664 kB | 15 / 15 requests |
| Volcà Santa Margarida | [/sta-margarida.html](https://dainty-licorice-850b4d.netlify.app/sta-margarida.html) | 12.42s / 15.19s | 4.2 / 4.9 MB | 1.7 / 2.2 MB | 33 / 36 requests |
| Castellfollit de la Roca | [/castellfollit.html](https://dainty-licorice-850b4d.netlify.app/castellfollit.html) | 12.44s / 16.24s | 4.3 / 5.2 MB | 1.8 / 2.5 MB | 33 / 36 requests |
| Enllaços | [/links.html](https://dainty-licorice-850b4d.netlify.app/links.html) | 5.28s / 5.69s | 611 /628 kB | 441 / 458 kB | 10 / 10 requests |

Aquests són els resultats obtinguts abans de començar a aplicar canvis. S'ha observat que les pàgines on hi ha inserit un vídeo de YouTube, tenen un pes total molt elevat i per tant també un temps de càrrega força elevat. Sobretot perquè l'script de YouTube _base.js_ té molt de pes i ell sol ja triga uns 10 segons a carregar.

Un altre factor que s'ha observat és que la memòria cau hi fa molt, ja que moltes coses com la font utilitzada o dependències externes com FontAwesome, treuen una bona part del temps de càrrega, ja que s'han de connectar a un servidor extern que les emmagatzema i descarregar-se. En canvi si es carreguen quan s'accedeix a la primera pàgina, ja estan llestes per les següents pàgines i estalviaran força temps de càrrega.

2. **RESPON LES PREGUNTES**

1. **Quins canvis detectes en les eines per a desenvolupadors en aplicar** _ **lazy loading** _ **a les imatges del teu web? Com creus que afecta la performance de la teva pàgina?**

El canvi principal es nota en pàgines on hi ha imatges més avall, es carrega la part visible de la pàgina més ràpidament ja que no ha de carregar també al mateix moment les imatges de més avall, i de seguida guanya un o dos segons de temps de càrrega si hi ha vàries imatges més avall.

2. **Què passa en aplicar càrrega asíncrona als scripts de la teva pàgina? Quins problemes creus que pot haver-hi si carregues asíncronament el JavaScript?**

En no tenir scripts a la pàgina no s'ha pogut comprovar, però buscant informació si que s'observa doncs que el que passa és que el fil de càrrega de la pàgina no s'atura i segueix mentre carrega l'script. Evitant d'aquesta manera que la càrrega total de la pàgina depengui de l'script.

Un dels problemes que sembla que es podria donar és el fet que carregui la pàgina però encara no carregui el JavaScript i això faci que tot i que l'usuari percebi la pàgina com a carregada, aquesta no tingui alguna funcionalitat bàsica, cosa que pot afectar a l'experiència de l'usuari.

3. **No hem fet càrrega asíncrona d'estils. Creus que es podria fer? Quins problemes podríem tindre? Raona la resposta.**

Segurament es podria fer, però només tindria sentit si els estils estiguessin separats en diferents fulls d'estil, de manera que per la pàgina que es demana només carregués aquell estil d'aquella pàgina. Ara bé, això seria poc recomanable ja que s'intenta que el fitxer CSS final un cop fet el _build_ sigui únic. Deixant de banda que habitualment tampoc suposa una càrrega molt gran. En les pàgines del projecte per exemple triga un segon a carregar, així que tampoc seria la millora que obtindríem, potser reduint només unes dècimes de segon la càrrega.

3. **INFORME PRIMERA ITERACIÓ**


En general a nivell de PC totes tenen una bona puntuació (90-100). És a nivell mòbil on sorgeixen els problemes(40-80). Principalment totes donen l'error de que el fitxer CSS bloqueja la renderització i això fa que la primera pintada de contingut trigui uns tres segons.

Per altra banda, les pàgines que tenen en el seu contingut un vídeo inserit de YouTube, donen encara més error, pel fet que la inserció del vídeo crea la necessitat de carregar uns scripts que triguen força a carregar i bloquegen també la renderització.

Per tant, com a propostes de millora, es planteja intentar reduir la càrrega del fitxer CSS, i també intentar evitar la càrrega innecessària dels scripts que genera l'inserit de YouTube.

S'ha començat amb la inserció del vídeo de YouTube. Després d'investigar sobre el tema, s'ha observat que és quelcom recurrent i que és inevitable la càrrega dels scripts, ja que és un script de tercers i per tant no es pot modificar ni evitar la seva càrrega. Així que la solució per la qual s'ha optat, ha estat instal·lar una dependència anomenada [Lite YouTube Embed](https://github.com/paulirish/lite-youtube-embed/tree/master) que permet evitar aquesta càrrega dels scripts en la primera càrrega de la pàgina.

El que fa aquesta dependència és que permet que allà on aniria el vídeo, es carregui només la imatge en miniatura del vídeo i la icona de _play_, de forma que per l'usuari sembli que allà hi ha el vídeo inserit. Però en realitat, no és fins que es fa clic al vídeo que aquest carrega l'script necessari per reproduir-lo.

Després d'aplicar aquesta millora, els temps de càrrega de les pàgines que contenien vídeo han reduït uns 5 segons, fet molt positiu, i que també s'ha vist repercutit en l'anàlisi de PageSpeed Insights, on les pàgines amb vídeos han pujat fins a resultats del 80-85 de rendiment.

A continuació, s'ha anat per l'altre problema, que afectava a totes les pàgines i que l'informe marcava que era la càrrega del CSS.

El problema però és que el CSS no es podia separar en diferents fitxers ni tampoc és que realment tingués una mida rellevant, de fet pesa 23 kB. Aleshores, després d'investigar una mica més en el tema, s'ha vist que aquests errors de càrrega que s'atribueixen al CSS a vegades poden ser deguts a temes d'optimització de la càrrega de fonts i similars (com FontAwesome).

I això s'ha corroborat analitzant els temps de càrrega i veient que realment, just després de carregar el CSS, el que portava més temps era carregar les fonts i sobretot les FontAwesome.

Per solucionar el problema, en el cas de les FontAwesome, s'ha optat per inserir el codi SVG d'aquestes directament, de forma que no cal esperar a la càrrega de cada icona, si no que la renderitza el navegador a partir del SVG. Això ha fet desaparèixer pràcticament el temps de càrrega de les FontAwesome i ja s'ha guanyat força temps.

Faltava encara però les fonts. Per a aquest tema, per tal d'evitar la càrrega de les fonts des de Google Fonts, s'ha optat per descarregar-les, convertir-les al format _.woff2_, guardar-les al projecte i inserir-les al CSS amb _@font-face_. També inserint només els fitxers necessaris, és a dir, la font regular i la negreta, que són les que s'utilitzen principalment. Això ha provocat també una millora important en la càrrega del fitxer CSS, ja que la connexió a Google Fonts alentia aquesta càrrega. Finalment, després d'aquestes millores s'han tornat a passar els tests de PageSpeed Insights i s'han obtingut els resultats que es veuen en el següent punt.

4. **INFORME SEGONA ITERACIÓ**

En aquesta segona iteració, podem veure que les millores aplicades després de la primera, realment han tingut efecte i el rendiment ronda els 100 punts en quasi totes les pàgines. Les poques on no ronda el 100, n'hi ha dues, la de Santa Margarida i Castellfollit, que marca que és degut a que no s'ha especificat una _width_ i _height_ a l'element \<img\>, per tal de guardar aquest espai per la imatge. El problema és que en aquest cas, la imatge té una gestió de la direcció d'art, que complica poder guardar aquest espai, ja que les mides són diferents en funció de la resolució.


Després d'investigar sobre el tema s'ha vist que no hi ha gaires possibles solucions ni millores en aquest aspecte, i com que tampoc afecta molt a la càrrega ja que ara mateix ja va força ràpid, no caldria aplicar cap canvi, ja que només es dona en dues imatges de tota la pàgina.

Per la resta, tots els punts estan solucionats. En alguna pàgina encara marca que el CSS bloca la renderització, però només uns 300ms.

En no veure cap possible millora més i tenir un rendiment de quasi 100 punts o fins i tot 100 en alguns casos, es creu que el CSS ja és suficientment ràpid i eficient.


1. **TAULA VEOLICITATS DE CÀRREGA final**

Per tal d'evitar URL molt llargues, la URL base del projecte és: [https://tangerine-lebkuchen-d63ec2.netlify.app/](https://tangerine-lebkuchen-d63ec2.netlify.app/). A la taula s'afegeix només el nom del fitxer HTML i l'enllaç.

| **Títol** | **URL** | **Temps de càrrega (mitjà)**
**(Mòbil/PC)** | **Pes total**
**(Mòbil/PC)** | **Pes transferit**
**(Mòbil/PC)** | **Quantitat de recursos**
**(Mòbil/PC)** |
| --- | --- | --- | --- | --- | --- |
| Portada | [/index.html](https://tangerine-lebkuchen-d63ec2.netlify.app/index.html) | 3.77s / 4.46s | 483 / 549 kB | 320 / 386 kB | 8 / 8 requests |
| Història i formació | [/historia.html](https://tangerine-lebkuchen-d63ec2.netlify.app/historia.html) | 3.88s / 4.08s | 494 / 535 kB | 325 / 335 kB | 11 / 13 requests |
| Volcans i llocs d'interès | [/volcans.html](https://tangerine-lebkuchen-d63ec2.netlify.app/volcans.html) | 5.94s / 6.06s | 664 / 666 kB | 500 / 502 kB | 12 / 12 requests |
| Volcà Santa Margarida | [/sta-margarida.html](https://tangerine-lebkuchen-d63ec2.netlify.app/sta-margarida.html) | 4.76s / 5.91s | 567 / 714 kB | 396 / 508 kB | 13 / 15 requests |
| Castellfollit de la Roca | [/castellfollit.html](https://tangerine-lebkuchen-d63ec2.netlify.app/castellfollit.html) | 5.67s / 6.98s | 667 / 809 kB | 497 / 632 kB | 13 / 15 requests |
| Enllaços | [/links.html](https://tangerine-lebkuchen-d63ec2.netlify.app/links.html) | 4.01s / 3.98s | 465 / 465 kB | 295 / 295 kB | 7 / 7 requests |

Aquests són els resultats obtinguts després d'aplicar tots els canvis. Com es pot observar, la millora és substancial, sobretot en les pàgines amb més contingut multimèdia, on la majoria han reduït el temps per tres, passant d'uns quinze segons a només cinc segons. A més a més de reduir moltíssim el nombre de de dades transferides. Abans hi havia algunes pàgines que necessitaven 4 MB per carregar-se, i ara la més alta té 809 kB.

També el nombre de peticions s'ha vist considerablement reduït, en evitar les càrregues de YouTube i de FontAwesome.

En general doncs es podria concloure que les modificacions aplicades han estat un èxit, ja que tant la reducció en temps de càrrega com els informes del PageSpeed Insights mostren una clara millora, sense haver de prescindir de cap dels continguts o dissenys de la pàgina, la qual es veu igual que abans de realitzar cap dels canvis.

Per tant doncs, la valoració final és positiva, i es creu que seria una web molt eficient i apta per a usuaris amb connexions lentes o tarifes de dades limitades.