Eines HTML i CSS -- PAC 1 -- Documentació - Fet per Oriol Esquena (oesquena@uoc.edu)

## ENLLAÇOS REPOSITORI I PUBLICACIÓ

El codi s'ha publicat a GitHub, al següent enllaç:
<https://github.com/oriolesquena/eines-html-i-css-pac1>

La publicació s'ha fet amb Netlify i s'ha publicat en el següent enllaç:
<https://lustrous-eclair-11fd16.netlify.app/index.html>

## PROCÉS DE DESENVOLUPAMENT

### Creació del boilerplate

Els primers passos per poder iniciar la pràctica han estat la creació
d\'un *boilerplate* basat en *Parcel* amb els requisits indicats en el
mòdul 2. Els passos per fer-ho han estat els següents:

-   Crear un arxiu package.json executant la comanda: npm init --yes

-   Instal·lar *Parcel* amb la comanda: npm install \--save-dev parcel

-   Instal·lar RimRaf amb la comanda: npm install \--save-dev rimraf
    npm-run-all

-   Modificar les línies de start i build del fitxer package.json amb el
    codi:

    -   \"start\": \"npm-run-all clean parcel:dev\",

    -   \"build\": \"npm-run-all clean parcel:build\"

-   Afegir la línia: \"browserslist\": \"\> 0.5%, last 2 versions, not
    dead\" per tal de donar compatibilitat al lloc web compilat.

Totes aquestes comandes d'instal·lació, afegeixen línies al package.json
i fitxers a la carpeta node_modules. D'aquesta forma, si es vol editar
el projecte des d'un altre ordinador, només cal fer un npm install per
tenir-ho tot en ordre, ja que llavors s'instal·la tot el que
s'especifica en el fitxer package.json.

Un cop seguits aquests passos, amb un primer codi d'HTML i CSS molt
senzill, s'ha fet la prova d'executar la comanda: npm run build, per
veure si compilava sense errors, i així ha estat.

A partir d'aquí, s'ha executat la comanda: npm run start, que permet
compilar i veure el projecte en un entorn local (http://localhost:1234)
i accedir-hi així també des d'altres dispositius que estiguin en la
mateixa xarxa Wi-Fi. Fet que permet ja treballar correctament en el
desenvolupament del projecte.

S'ha de dir que en aquest punt, la comanda npm run start, no em
funcionava correctament si ho feia des del terminal de Linux (WSL), en
canvi des del de Windows (Powershell), no donava cap problema.

També cal tenir en compte que de bones a primeres no podia accedir a
http://localhost:1234 des d'altres dispositius. Però s'ha solucionat
desactivant el tallafocs de Windows en els moments en què s'ha
necessitat accedir-hi.

### Creació del repositori

Un cop creat el *boilerplate* amb el nom eines-html-i-css-pac1. A
continuació, seguint les instruccions de GitHub de [com afegir un codi
guardat en local a un repositori
personal](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github#adding-a-project-to-github-without-github-cli)
s'ha creat un repositori nou al GitHub personal, s'ha creat una branca
master del codi guardat en local a la carpeta eines-html-i-css-pac1,
s'ha fet un git add i un git commit, s'ha afegit la URL per el
repositori remot (git remote add origin \<REMOTE_URL\>) i finalment s'ha
fet un git push origin main.

D'aquesta manera ja es té el repositori local connectat al GitHub i cada
vegada que es facin canvis i es vulgui guardar, fent un push, ja quedarà
guardat al GitHub.

### Instal·lació de dependències

Abans de començar a desenvolupar el codi, també s'ha aprofitat per
instal·lar una nova dependència al projecte, la FontAwesome. Per fer-ho
s'executa la comanda npm install \--save \@fortawesome/fontawesome-free.
Aleshores s'instal·la la dependència a la carpeta node_modules i
s'afegeix com a dependència al fitxer package.json.

### Compilació per la producció

Per tal que el projecte web sigui visible per tothom i no només des de
l'entorn de desenvolupament local, s'ha penjat en un servidor web.

Per fer-ho, s'ha creat un compte al proveïdor de servidors Netlify i a
continuació s'ha vinculat aquest compte amb el repositori de GitHub. A
continuació, s'ha determinat la comanda de *build*: npm run build, i la
carpeta destí: dist. Fet això, s'ha fet un "*Deploy"* i s'ha activat el
"*Continuous Deployment"* de forma que cada vegada que es fa un push a
la branca enllaçada del GitHub, Netlify fa un *"Deploy"* automàticament.

D'aquesta manera ens assegurem que sempre tenim publicada la última
versió del codi del projecte web.

## DISSENY I DESENVOLUPAMENT

Per tal de dissenyar i desenvolupar el projecte, el primer ha estat
escollir un lloc d'interès de la meva localitat, per poder plantejar què
es volia posar a la web i com. Un cop escollit, s'ha desenvolupat la
idea i la distribució de la informació, i s'ha començat a escriure el
codi HTML per tal de definir l'esquelet de la pàgina. La informació que
hi apareix s'ha extret principalment de la
[Viquipèdia](https://ca.wikipedia.org/wiki/Parc_Natural_de_la_Zona_Volc%C3%A0nica_de_la_Garrotxa)
i de la pàgina de [Turisme
Garrotxa](https://ca.turismegarrotxa.com/territori-i-natura/parc-natural-i-espais-protegits/parc-natural-de-la-zona-volcanica-de-la-garrotxa/).

L'estructura que segueix la pàgina és tenir una pàgina d'inici o portada
amb una imatge i una breu explicació general de la pàgina.

Després tenim una pàgina de presentació i més explicació del parc, amb
la seva història i formació.

També trobem una pàgina que conté una llista de llocs d'interès, que
s'avindria amb la pàgina de categoria que es demana per la pràctica.
Dins d'aquesta, trobem dues pàgines detall amb informació més específica
sobre cadascun d'aquests llocs d'interès (se n'han creat dues com a
exemple, els últims tres llocs de la llista no tenen pàgina ja que no
aporta res a nivell de novetat en l'HTML i/o el CSS).

I finalment tenim la pàgina d'enllaços, que conté els links de les
diferents fonts d'informació, d'imatge i de vídeo utilitzades pel
desenvolupament del projecte.

Un cop amb la base de l'HTML creada, s'ha anat donant forma a l'estil
amb CSS. S'ha enfocat amb l'estil *mobile first* ja que és el que es
recomanava a l'assignatura anterior d'HTML i CSS. També, abans de
començar a escriure el codi de CSS, es va decidir una paleta de colors i
un estil a seguir, que combinen amb els colors de terra i natura que
envolten el Parc Natural de la Zona Volcànica de la Garrotxa (tema
escollit pel projecte).

Al principi d'escriure l'HTML ja s'havien anat definint classes pensades
pels estils CSS. Tot i així, durant l'escriptura de codi del CSS s'han
hagut de canviar i ajustar algunes classes per tal de que el codi fos
més eficient i fidel a la guia.

De cares a la *responsiveness* de la pàgina, com s'ha partit del disseny
*mobile first* s'ha intentat ja que moltes coses fossin adaptables a
totes les mides de pantalla i dispositius. Pel que no podia ser així
però, s'han definit unes *media queries* per tal de redefinir l'estil en
dispositius com tablets i també per ordinadors (pantalles més grans en
general). Fent un bon planteig de *responsiveness* però, s'ha pogut
estalviar força codi en les *media queries* quedant només allò que és
essencialment diferent en diferents dispositius.

Tot el codi CSS està comentat per tal de facilitar l'entesa d'aquest.
Els punts més obvis, com per exemple el color del text o els marges no
estan comentats, ja que se suposa que qualsevol que entengui una mica de
CSS comprèn què significa.
