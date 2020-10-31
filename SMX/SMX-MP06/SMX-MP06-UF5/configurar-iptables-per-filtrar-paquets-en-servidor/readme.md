# Configurar iptables per filtrar paquets en servidor
## SMX-MP06-UF5 - Exercici de tallafocs i monitoratge de xarxes.
#Què necessiteu?

Una màquina virtual GNU/Linux que farà de SERVIDOR. No feu servir un sistema amb entorn gràfic (els servidors normalment són en mode text). Podeu descarregar la màquina [Turnkey Core - Debian GNU/Linux](https://www.turnkeylinux.org/core) que ja està instal·lada.

El SERVIDOR tindrà dos adaptadors de xarxa:

- **Adaptador de xarxa 1**: en mode PONT que prendrà la configuració IP automàticament del servidor DHCP de l'institut.
- **Adaptador de xarxa 2**: en mode XARXA INTERNA amb configuració IP manual.

Una màquina virtual que farà de CLIENT. Pot ser Windows o GNU/Linux.

- **Adaptador de xarxa 1**: en mode XARXA INTERNA amb configuració IP manual. El DNS pot ser el de Google (8.8.8.8) o un altre que us funcioni. La porta d'enllaç serà la IP manual que heu configurat en el SERVIDOR.

#Recursos

Us pot anar bé comprovar quina norma del tallafocs s'està executant en un moment donat. En el següent vídeo s'explica com fer-ho.

[Veure les normes actives d’iptables](https://vimeo.com/41920351)

També us pot servir comprovar que les normes que heu posat estan actives (per exemple que el servei SSH està tancat). El següent vídeo mostra formes de fer-ho:

[Comprovar normes actives d’iptables](https://vimeo.com/41791591)

#Activitat

1. Activeu el NAT en el servidor per a que tradueixi les IPs de la XARXA INTERNA a IPs de l'institut. Feu els canvis per a que al reiniciar es mantinguin i expliqueu com ho heu fet.
2. En un document, apunteu almenys quatre serveis de xarxa que instal·lareu al SERVIDOR (algunes opciones: HTTP, HTTPS, FTP, SMTP, POP3, IMAP, SSH, DNS...). Heu d'instal·lar aquests serveis al SERVIDOR i que estiguin actius.
3. La política de la cadena INPUT ha de ser restrictiva. La política de la cadena OUTPUT la decidiu vosaltres. Quina/es comanda/es heu fet servir?
4. Al document, per cada servei instal·lat al SERVIDOR, escriviu les normes que afegireu al  tallafocs. Tingueu en compte que hi ha dues xarxes (INSTITUT i XARXA INTERNA). Per exemple: Permetre accés al servidor SSH només des de la xarxa interna. Permetre l'accés al servidor WEB des de qualsevol xarxa, etc.
5. Esbrineu les comandes iptables necessàries per implementar les normes que heu llistat al punt anterior. Implementeu-les al servidor i feu els canvis per a que siguin permanents.

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf05

* Resultats d'aprenentatge 1.g
---

###### Autor: Carles Caño 2017.03.16 14:05:32
###### Editat per: Carles Caño 2017.03.16 14:19:11
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
