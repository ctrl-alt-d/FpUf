# Ela alumnes s'examinen de M9
## DAM-MP09-UF2 - Exercici de Processos i fils
### Els alumnes s'examinen de M9.
Tenim un programa (Alumnes.java , Notes.java) on els alumnes entren a classe i fan un examen, però fins que no acaba un, no comença l'altre.

-  Transformar l'aplicació on els alumnes s'examinen de forma seqüencial, a una aplicació en què els alumnes s'examinin tots a la vegada.
-  Fes la transformació utilitzant les següents classes: Callable, Executor i Future
-  Comprova que el temps d'execució en els dos casos. Quin és inferior? Perquè?


**Alumnes.java**

    public class Alumne {
	private String Nom;
		
	public Alumne(String nom) {
		Nom = nom;
	}

	public int Examinar() {
		//temps que triga a fer l'examen
		try {
			Thread.sleep((long) (Math.random()*2000)+1000);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		//nota de l'examen
		int nota = (int) (Math.random()*10);
		return nota;
	}

	public String getNom() {
		return Nom;
	}

	public void setNom(String nom) {
		Nom = nom;
	}
}

**Notes.java**

    public class Notes {

	public static void main(String[] args) {
		int numAlumnes = 10, te, ti;
		String Modul = "M9";
		int notes[] = new int[numAlumnes];
		
		//instanciem els alumnes
		Alumne[] A_m9 = new Alumne[numAlumnes];
		
		//comencem a contar el temps
		ti = (int) System.currentTimeMillis();
		//Donem nom als alumnes i els posem a fer l'examen
		for (int i=0;i<numAlumnes;i++) {
			A_m9[i] = new Alumne(Modul+"-"+i);
			notes[i] = A_m9[i].Examinar();
		}
		//Han acabat i agafem el temps final
		te = (int) System.currentTimeMillis();
		
		//traiem els resultats i el temps que han trigat
		for (int i=0;i<numAlumnes;i++) {
			System.out.println("Alumne "+A_m9[i].getNom()+" : " + notes[i]);
		}
		System.out.println("Han trigat: " + (te - ti)/1000 + " segons");
	}
}

---

#FpInfor #Dam #DamMp09 #DamMp09Uf02

* Resultats d'aprenentatge 1.e 1.f 1.g 1.h
* Continguts 1.6 1.7 1.8 1.9
---

###### Autor: Jordi Hernandez 2014.12.02 09:36:33
###### Editat per: Jordi Hernandez 2016.12.07 09:58:02
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
