# Vulnerabilitats de programari
## SMX-MP06-UF4 - Exercici de seguretat activa.
Objectius: Detectar i entendre les vulnerabilitats de programari

Vulnerabilitats de programari
=======================================
Un cop realitzat el mapa de xarxa l'objectiu de qualsevol atacant és descobrir si alguna de les portes d'entrada a un dels ordinadors es pot usar per entrar de forma "irregular".

Hi ha una regla que és bàsica en la informàtica actual: “Els programes estan fets per persones i per tant contenen errors”. Des d'un punt de vista de la seguretat el problema està quan algun d'aquests errors permet a un atacant saltar-se els mecanismes de defensa i realitzar alguna tasca en el nostre sistema.

Un atacant amb coneixements pot intentar descobrir algun error en el programari però sovint no cal reinventar la roda. Podem recórrer als llistats d'errors públics que es poden trobar a Internet

CVE (Common Vulnerabilities and Exposures)
---------------------------------------------
Cada dia es descobreixen una gran quantitat de vulnerabilitats en el programari i és per això que cal alguna forma de poder-les distinguir (especialment quan n'hi ha moltes que s'assemblen molt). Els CVE (Common Vulnerability Identifiers) són una forma de identificar únicament les vulnerabilitats

Els codis estan formats per el text "CVE", l'any en que s'ha descobert la vulnerabilitat, i un número de quatre xifres
			
> CVE-2008-0068
		
Existeixen múltiples webs on es poden veure les vulnerabilitats que tenen codi CVE i les seves característiques (quina vulnerabilitat és, si es pot explotar, etc...)

* http://web.nvd.nist.gov/view/vuln/search?execution=e2s1 	 	
* http://www.cvedetails.com/ 	 	

Bases de dades d'Exploits
----------------------------------
A part de les llistes de vulnerabilitats també es poden trobar a Internet tota una sèrie de llocs web que contenen bases de dades d'exploits per aprofitar-se de les vulnerabilitats que es van descobrint en el programari públic

La més popular actualment és exploitDB però se'n poden trobar moltes més

Activitat
--------------------------------

### Detectar vulnerabilitats 

1. Localitzeu dues vulnerabilitats recents de Windows i dues de Linux en alguna de les pàgines CVE

Un atacant ha aconseguit fer un mapa d’una xarxa i els resultats són aquests:

![Xarxa](https://raw.githubusercontent.com/utrescu/utrescu.github.io/master/images/xarxa-vulnerable.png "Vulnerable")

2. Fent servir alguna de les webs de registre de vulnerabilitats descobriu si algun dels serveis de la xarxa és vulnerable

3. En alguna web d’exploits es pot trobar un atac contra algun dels serveis de la xarxa?
    - De quin tipus és l’exploit? (remot, local, DOS)
    - Creus que podria funcionar?

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf04

---

###### Autor: Xavier Sala 2017.02.08 21:15:27
###### Editat per: Xavier Sala 2017.02.08 21:15:27
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
