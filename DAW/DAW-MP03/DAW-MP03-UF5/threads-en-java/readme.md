# Threads en Java
## DAW-MP03-UF5 - Conceptes de POO. Llibreries de classes fonamentals
Observa aquest exemple de Threads (fils d'execució) en Java. Para atenció a:

- Classe interna (inner class) ThreadExample.
- Comptador de threads global amb variable estàtica (threadnum).
- Funció sleep per "dormir" una estona el thread. Cal posar-la dins d'un try/catch.

Més material:

- [Exercicis](/DAW/DAW-MP03/DAW-MP03-UF5/threads-en-java-exercicis/readme.md).
- [Intro al Java](http://www.cacauet.org/wiki/index.php/Java%3A_introducci%C3%B3_r%C3%A0pida).

Codi: (compila'l, executa'l i observa la sortida)

```java
import java.util.*;
import java.lang.*;

class threadsexample
{
    public static int threadnum = 0;
    
    class ThreadExample extends Thread {
        int rounds = 10;
        int thread_id;
        int sleepms = 1000;
        // constructor
        ThreadExample(int ms) {
            sleepms = ms;
            thread_id = ++threadnum;
        }
        // runnable code
        public void run() {
            while(rounds>0) {
                System.out.println("Thread "+thread_id+" round "+rounds);
                rounds--;
                try {
                    sleep( sleepms );
                } catch (Exception e) {
                    // TODO: treat the exception, show error, etc.
                }
            }
        }
    }
    
    public static void main(String []args)
    {
        threadsexample te = new threadsexample();
        te.fes_algo();
    }
    
    public void fes_algo()
    {
        System.out.println("...iniciant...");
        
        ThreadExample t1 = new ThreadExample(1000);
        ThreadExample t2 = new ThreadExample(500);
        t1.start();
        t2.start();

        System.out.println("...finalitzant main...");
    }
}
```

[Exercicis aquí](/DAW/DAW-MP03/DAW-MP03-UF5/threads-en-java-exercicis/readme.md)

---

#FpInfor #Daw #DawMp03 #DawMp03Uf05

---

###### Autor: Enric Mieza 2014.04.03 09:46:20
###### Editat per: Enric Mieza 2014.04.11 16:26:33
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
