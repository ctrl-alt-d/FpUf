# PHP - Sudoku amb formularis i sessions
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Crea un [joc del Sudoku](https://ca.wikipedia.org/wiki/Sudoku) amb PHP.

Guía:

1. Crea una taula HTML tal i com s'explica en les bases del joc, amb les línies divisòries en quadrants de 3x3 cel·les. Crea-la amb PHP i amb bucles, res de predefinits.
2. Insereix els *tags* de formulari adequats per poder enviar les dades al servidor. Fes que cada casella sigui un INPUT amb el tamany adequat.
3. Fes que les dades del formulari (els nombres) no desapareguin quan tornem a reenviar-lo. Simplement es tracta de reintroduir els valors de la variable $_POST dintre dels INPUT.
4. En la variable $_SESSION hi posarem les cel·les fixes que l'usuari no pot modificar. Aquestes han de mostrar-se en gris i "disabled" pq l'usuari no les canvii.
4. Per anar provant la visualització, inicialitza la partida (el model) amb unes quantes caselles predefinides (que sàpigues que son correctes). En les caselles que ja existeix una dada, no col·loquis INPUT en el formulari i només escriu el valor del nombre col·locat.
5. Afegeix un botó de "Nova Partida" que inicii un nou tauler amb 20 cel·les aleatòriament (s'insertaran al array $_SESSION).
6. Crea funcions de comprovació per saber si una fila o columna compleixen les normes del Sudoku, per exemple:
    * function **comprova_fila**(int numfila);
    * function **comprova_columna**(int numcol);
    * function **comprova_quadrant**(int fila, int col); Aquesta la deixarem per més endavant ja que resulta mes complexa que les altres.
7. Utilitza les funcions per comprovar les caselles fixes de la inicialització. Si detectes que una casella no compleix les normes, esborra-la i crea una de nova fins que arribis a les 20 caselles inicials.
8. Utilitza les funcions per comprovar cada cop que entrem dades noves (per POST o GET), si aquestes compleixen les regles del Sudoku. Si no les compleixen, marca-ho d'alguna manera perquè l'usuari ho pugui corregir.
9. Pensa't la manera de fer la funció **comprova_quadrant**. Recorda que per aquest tipus d'accions ens és molt útil l'**operador mòdul %**
10. Si t'animes i et veus un *crack*, intenta implementar un botó "Resol Partida" i que implementi l'[algorisme de *backtrack* que es proposa en aquest article](https://cacauet.org/wiki/index.php/Algorisme_de_backtracking). MOLT IMPORTANT: a l'hora de generar una partida, aquesta no té perquè ser resoluble, encara que les caselles creades compleixin les regles del Sudoku. En aqeues cas (que és el més comú), l'algorisme de *backtrack* fallaria. Per solventar-ho, hauries d'utilitzar aquest algorisme per chequejar cada cop que afegeixes una casella nova a la inicialització que, a part de complir les normes del Sudoku, el tauler resultant és resoluble. S'aconsella fer les proves amb poques caselles inicials, per exemple 2, enlloc de 20, i després anar augmentant, per depurar l'algorisme.

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

---

###### Autor: Enric Mieza 2016.09.30 13:37:22
###### Editat per: Enric Mieza 2016.10.09 21:10:47
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
