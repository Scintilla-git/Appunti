## Strutture Algebriche - TPS

### Struttura Algebrica Semigruppo
- è una struttura composta da una struttura binaria chiusa e associativa
- Prende il nome di **Monoide**

Un gruppo ha più elementi neutri(?)

Un elemento neutro è...

### Sottogruppo
Prendiamo un gruppo G e diciamo che (G, \*).
Diciamo che H è **sottogruppo** di G se (H, \*) è un gruppo.
E' ovvio che se H=G, allora sono lo stesso gruppo.
Per questo l'idea è di prendere un gruppo più piccolo.

Altro esempio:
>Prendiamo (Z, +) - Z considerato come insieme dei numeri interi.
>Definiamo il sottoinsieme di Z -> P, dove {P appartiene a Z : P è pari}.
>Effettivamente P è chiuso, in quanto la somma di due numeri pari sommati risultano in un terzo numero pari.
>A questo punto il gruppo P soddisfa tutti i requisiti per essere considerato sottogruppo di Z.
>
>Esiste un sottogruppo ancora più stupido, ovvero {0} -> Gruppo vuoto.
>
>Consideriamo un secondo sottoinsieme di Z -> A.
>A = {z appartiene a Z : z % 3 = 0}
>
>Prendiamo il gruppo (G, +%) e G = {0,1,2,3,4}
>- +% equivale a fare prima una somma(+) e poi fare la divisione e returnare il resto(%)
>Fatta la tabella, si nota che l'inverso di 0 è se stesso, 1 è l'inverso di 4 e 2 di 3.

#### Permutazioni
A = {a,b}
Dato questo insieme, posso creare delle sequenze:
>(a,b) e (b,a)

B = {0,1,2}
Qui le sequenze possibili aumentano
>(0,1,2) - (0,2,1) - (1,2,0) - (1,0,2) - (2,1,0) - (2,0,1)

Il modo di scambiare le sequenze è chiamato **permutazione**.
La più stupida è scambiare due elementi fra se stessi(A).
Una **trasposizione** è quando in una permutazione, vengono scambiati degli elementi tranne uno, che rimane nella posizione iniziale
>In B(0,1,2), succede in questi casi:
>(0,2,1) - (2,1,0) - (1,0,2)

Nelle permutazioni si può identificare anche l'**elemento neutro**, che equivale a un cambio un po' particolare: tutti gli elementi non vengono spostati, ma rimangono alla posizione iniziale.
>A questo punto, possiamo(in un certo senso) dare un nome a ogni permutazione di B
>(0,1,2) = e ->Elemento neutro
>(0,2,1) = t0, (2,1,0) = t1, (1,0,2) = t2
>(1,2,0) - (2,0,1) li chiamiamo cicli, perchè notiamo che gli elementi shiftano a sinistra(primo caso) o a destra(Secondo caso)

Notiamo anche che t0 è inverso di se stesso, così come t1 e t2!
>(0,1,2) -t0-> (0,2,1) -t0-> (0,1,2)

Per i cicli invece è un po' diverso...
>(0,1,2) -cd-> (2,0,1) -cd-> (1,2,0) -cd-> (0,1,2)

Dunque i cicli non sono inversi di se stessi, in quanto occupano più operazioni per tornare al punto di partenza, e per farlo gli elementi si devono spostare o a destra o a sinistra.

A questo punto possiamo dire che {e, t0} è un *sottogruppo* di B, così come {e, t1} e {e, t2}.
Questi sono più scontati.

Quelli meno scontati sono {e, cd, cs} e {e}(che dal punto di vista matematico è un po' una buffonata).

------------------------
## Firewall - Sistemi
- **Il firewall è fondamentalmente un filtro**.
- Il firewall è un filtro che decide quali pacchetti, frame, e altre cose possono passare o venire inviate.

Questo [Link](https://www.booleanworld.com/depth-guide-iptables-linux-firewall/) è stato inviato su classroom e parla dei firewall su linux

Iniziamo con le basi
- Il firewall è composto da tre elementi
	- **Tables**(Tabelle)
		- Esistono diversi tipi di tabelle pre-impostate:
			- Il *filtro*, tabella più utilizzata dal firewall e immaginiamo perchè
			- il *mangle*, ovvero una tabella che permette di cambiare gli header dei pacchetti
			- il *NAT*, ovvero la tabella che permette di mandare i pacchetti a altri hosts sulla NAT network e, nel caso, cambiando la sorgente e l'indirizzo di destinazione dei pacchetti
			- il *raw*: iptables
	- **Chains**(Catene)
		- Possono essere:
			- PREROUTING
			- INPUT: questa catena si applica sui pacchetti in entrata
			- OUTPUT: questa catena è utilizzata sui pacchetti in uscita
			- FORWARD: questa catena è utilizzata sui pacchetti che devono uscire
			- POSTROUTING
	- **Rules**(Regole)
		- Che sono:
			- ACCEPT: **No problema :)**
			- DROP: Il pacchetto viene droppato, buttato, in modo silenzioso. Se qualcuno stava provando a collegarsi da remoto, semplicemente appare come se il sistema non sia mai esistito
			- REJECT: **Get the fuck out :(**

![image](Untitled-Diagram.webp)
*Il diagramma mostra il flusso dei pacchetti attraverso le catene tra le varie tabelle*

Su Linux: comando ~\# iptables
>iptables --list
>**output**
>- Chain INPUT -> pacchetti in entrata
>- Chain FORWARD -> pacchetti processati per essere mandati
>- Chain OUTPUT -> pacchetti in uscita
>
>iptables -t filter -A INPUT -s [ipv4] -j REJECT
>Questo comando semplicemente chiama la tabella "filter", catena "INPUT", -s [ipv4] setta l'ip target e -j REJECT dice al filtro di bloccare l'ip settato
>
>Facciamo un esempio:
>\# iptables -t filter -A INPUT -s 8.8.8.8 -j REJECT
>\# ping 8.8.8.8
>il ping funziona, a metà. Infatti i pacchetti vengono inviati, ma il firewall blocca tutti i pacchetti in entrata da quel ping. Quindi funziona ma non funziona.

