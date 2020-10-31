# Oracle Objecte-Relacional - Herència - Agar.io
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
Agar té molt de problemes amb el lag. Pensen que emmagatzemar les dades amb Oracle Objects els pot ajudar. Per aquest motiu busquen el millor expert (que ets tu ) per tal que els dissenyi una base de dades orientada objecte on poder emmagatzemar les cèl·lules de les partides.

Un cop has fet l'anàlisi, identifiques que hi ha el super-tipus `cèl·lula` amb les propietats `id` (enter), `massa` (enter) i `posició` ( és un tipus on emmagatzemes la `x` i la `y` de tipus float ). També hi ha un mètode ( que cal sobreescriure als subtipus ) que es diu `incrementa_massa`.

El sub-tipus `jugador` té els següents camps `nom` i `color` i el sub-tipus `virus` no té cap camp nou.

La massa d'una `cèl·lula` `jugador` es pot incrementar fins a 24.000 i la d'un `virus` fins a 182.

**Entregables:**

* Explica quines característiques d'oracle objects poden fer que es redueixi el lag de l'Agar.
* Crea les estructures necessàries i inserta un parell de virus i un parell de jugadors. Incrementa la massa de totes les cèl·lules.
* Selecciona la cèl·lula amb més massa.

![agar](https://i.imgur.com/pG1e7xV.png)

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2016.04.18 14:45:42
###### Editat per: daniel herrera 2018.04.24 13:14:57
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
