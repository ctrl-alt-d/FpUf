# Clustering amb MySQL (XtraDB Cluster Percona)
## ASIX-MP10-UF2 - Exercici de instal·lació i ajustament de SGBD corporatiu.
### CLUSTERING

Donada l'especificació d'un MySQL Cluster es vol muntar un entron SGBD amb clustering  mitjançant Percona XtraDB Cluster.

**Documentació:**

* [https://www.percona.com/software/mysql-database/percona-xtradb-cluster](https://www.percona.com/software/mysql-database/percona-xtradb-cluster " Pàgina inicial de Percona XtraDB Cluster")
* [https://www.percona.com/doc/percona-xtradb-cluster/5.5/index.html](https://www.percona.com/doc/percona-xtradb-cluster/5.5/index.html " Dcoumentació Percona XtraDB Cluster")
* [https://www.percona.com/doc/percona-xtradb-cluster/5.5/howtos/centos_howto.html](https://www.percona.com/doc/percona-xtradb-cluster/5.5/howtos/centos_howto.html "XtraDB Cluster in CentOS").

**Esquema:**

Esquema d'instal·lació d'un MySQL Cluster amb 3 màquines virtuals amb 1 GB de RAM i CentOS 6.5 Desactiva el firewall o permet la connexió als ports 3306, 4444, 4567, 4568

IPs de cada Node:

- Node 1: nodeid = 1, hostname=percona1, IP=192.168.70.71
- Node 2: nodeid = 2, hostname=percona2, IP=192.168.70.72
- Node 3: nodeid = 3, hostname=percona3, IP=192.168.70.73


**ENTREGA**

Realitza la documentació de la instal·lació i configuració que has hagut de dur a terme per pereparar un Percona XtraDB Cluster. Mostra al professor la funcionalitat del Cluster.

Intenta de provar una parada d'una màquina del Cluster i veure com es recupera després de la parada.


---

#FpInfor #Asix #AsixMp10 #AsixMp10Uf02

---

###### Autor: Robert Ventura 2016.06.29 07:11:00
###### Editat per: daniel herrera 2016.06.29 08:59:55
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
