# Vull el comandament
## DAM-MP09-UF2 - Exercici de Processos i fils
En una llar (*Llar.java*) tots els membres d'una família (*MembreFamilia.java*) es barallen per agafar el comandament a distància per mirar la tele.

A partir de la implementació donada crea el monitor (*Comandament.java*) per controlar que només un membre hi tingui accés.

Quan un membre de la família agafi el comandament i vulgui continuar mirant el mateix canal, no cal indicar quin canal mira, però si canvia de canal, cal indicar que tal membre ha canviat de canal.
El canal ha de ser un número aleatori entre entre 1 i 10, i qui té el comandament s'està també un temps aleatori mirant la tele.

`Llar.java`

```java
```
	public class Llar {

	public static void main(String[] args) throws InterruptedException {
		Comandament c = new Comandament();
		int numMembres = 5;
		
		//Es creen el membres de la família, se'ls dona un nom i es posen a mirar la tele
		MembreFamilia[] fam = new MembreFamilia[numMembres];
			for(int i=0; i<numMembres; i++) {
			fam[i] = new MembreFamilia(c);
			fam[i].setName("Membre-"+i);
			fam[i].start();
		}
		//Esperem que tots acabin de mirar la tele
		for(int i=0; i<numMembres; i++) {
			fam[i].join();
		}
		
		System.out.println("Tots han acabat de mirar la tele!");
		
	  }
	}

`MembreFamilia.java`

```java
public class MembreFamilia extends Thread {
```
	Comandament com;
	static int canal;
	
	public MembreFamilia(Comandament c) {
		com = c;
		canal=0;
	}

	@Override
	public void run() {
		//Agafa el comandament
		com.Agafa();
		int canal = (int)((Math.random()*10)+1);
		System.out.println(getName() + " està mirant el canal " + canal);
		
		//Mira la tele
		try {
			Thread.sleep((long) (Math.random()*300)+200);
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		//Deixa el comandament
		com.Deixa();
	  }
	
	}


---

#FpInfor #Dam #DamMp09 #DamMp09Uf02

* Resultats d'aprenentatge 1.e 1.f 1.g 1.h
* Continguts 1.6 1.7 1.8 1.9
---

###### Autor: Jordi Hernandez 2014.12.10 17:50:43
###### Editat per: daniel herrera 2014.12.12 12:48:58
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
