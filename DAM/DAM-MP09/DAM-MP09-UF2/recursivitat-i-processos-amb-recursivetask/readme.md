# Recursivitat i processos amb RecursiveTask
## DAM-MP09-UF2 - Exercici de Processos i fils
### Càlcul del factorial d'un nombre
- Implementa les parts de falten senyalades amb **//per implementar l'alumne** en el codi que calcula el factorial d'un nombre del codi següent.
- Decideix quin pot ser el millor llindar per l'eficiència del càlcul

**FactorialTaskAlumne.java**

```java
import java.util.concurrent.ForkJoinPool;
import java.util.concurrent.RecursiveTask;
```

      public class FactorialTaskAlumne extends RecursiveTask<Long>{

      private int n;
      public static final int LLINDAR = 10;

      public FactorialTaskAlumne(int _n) {
         // per implementar l'alumne
      }

      private Long factorialR() {
          // no cal comprovar per n=1 perquè ja ho fa el seqüencial
          FactorialTask f1 = new FactorialTask(n-1);
          f1.fork();
          return //per implementar l'alumne
      }

      private Long factorialS() {
          // per implentar l'alumne
      }

      @Override
      protected Long compute() {
          if(n < LLINDAR) {
              // per implementar l'alumne
          }
          else {
              // per implementar l'alumne
          }

      }

      public static void main(String[] args) {
          ForkJoinPool pool = new ForkJoinPool();
          FactorialTaskAlumne factorialTask = new FactorialTaskAlumne(25);

          /**
           * Per implentar l'alumne
           */


          System.out.println(result);
      }
    }

---

#FpInfor #Dam #DamMp09 #DamMp09Uf02

* Resultats d'aprenentatge 1.e, 1.g, 1.h
* Continguts 1.6, 1.8, 1.9
---

###### Autor: Jordi Hernandez 2016.12.07 10:07:28
###### Editat per: daniel herrera 2017.02.04 14:15:23
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
