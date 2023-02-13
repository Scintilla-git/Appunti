## Dimostrazione finale dell'RSA
Dunque per dimostrare l'RSA basta tenere a mente due cose: **i teoremi generalizzati di Eulero e Fermat**.

Iniziamo:
L'RSA si basa sulla scelta di due numeri primi grandi diversi tra loro, che chiameremo creativamente *p e q*.
Definiamo n = p\*q.
Quindi la phi di Eulero è: phi(n) = (p-1)(q-1).

Scegliamo un numero naturale e appartenente a N, tale che e sia coprimo di phi(n).
>e sarà l'elemento fondamentale della chiave pubblica

Con l'algoritmo di Euclide esteso troviamo l'inverso di e:
>e\*d % phi(n) = 1
>-> e\*d = a phi(n) + 1, con a appartenente a N

La coppia (e,n) è la chiave pubblica, o di cifratura.
La coppia (d,n) è la chiave privata, o di decifratura.

L'RSA prevede anche che il messaggio viene convertito in numero naturale(o una sequenza) durante la trasmissione.
Dunque chiamiamo m il numero che rappresenta il messaggio.
>c = m^e %n -> per la cifratura
>t = c^d %n -> per la decifratura

Dobbiamo dimostrare che *m = t*:
>t = c^d %n ≡ (m^e)^d %n ≡ m^e\*d %n ≡ m^(a\*phi(n)+1) %n

Se m e n sono coprimi, vale il teorema generalizzato di Eulero e possiamo affermare che:
>m^(a\*phi(n)+1) %n ≡ m%n

Come già scritto precedentemente, questo caso vale per il 99% dei casi.
Ma in quell'1% in cui il teorema non vale, ovvero se n è multiplo di m(o viceversa), si applica questo algoritmo:
>possiamo definire m = x\*p, con x numero qualunque
>m%p ≡ 0 -> m^e\*d %p ≡ 0%p ≡ m%p
>
>Applichiamolo anche a m^e\*d %q.
>m^e\*d %q ≡ m%q

Quindi:
- m = xp -> m^ed = x^ed \* p^ed = x' p
	- ovvero, m^ed è multiplo di p
- m^ed = yq + m = yq + xp

m^ed = x' p = yq + xp -> Siccome p divide m allora p divide xp e quindi anche yp, quindi divide anche y, -> y = pz.

Dunque:
>m^ed % p ≡ m%p
>m^ed % q ≡ m%q
>m^ed % (pq) ≡ m%(pq)
>m^ed % n ≡ m%n

Inoltre:
>m^ed = xp+m
>m^ed = yq+m
>Quindi xp + m = yq + m -> xp=yq

E con xp = yq possiamo dire che:
- q | x (q divide x)
- p | y
- x = ap
- y = bq

E quindi
>aqp = bpq
>ma qp e pq sono n
>-> an = bn

Ma a questo punto sappiamo anche che xp = an:
>prendendo la formula di prima, sostituiamo:
>an + m = bn + m

A questo punto possiamo dire che:
- m^ed %n +m = n%m
- siamo tornati al punto d'inizio!

- - - - - -
## Firewall - TPS
Torniamo a parlare dei firewall.
L'ultima volta abbiamo visto come mettere i filtri alle porte.

Oggi vedremo come bloccare invece le ricerche a un sito in particolare, ovvero le **proxy**.
>Una proxy funge da intermediario per le richieste da parte dei client alla ricerca di risorse su altri server, disaccoppiando l'accesso al web dal browser.

Ma facciamo un passo indietro, visto che per capire questi concetti servono diversi altri concetti, quali quelle di *socket*.

### Ri-diamo una definizione di socket
Dunque dobbiamo porci diverse domande sulle socket:
- Cos'è esattamente una socket?
	- E' un sistema di comunicazione tra host o tra processi
	- Spesso è TCP, ma esistono anche altri tipi di protocolli, come l'UTP o l'SCTP.
- Come distinguiamo una socket da un'altra?
	- Cosa gestisce le socket?
		- Chiaramente il sistema operativo.
			- Perchè il OS gestisce le risorse, quali i processi
	- Innanzitutto a una socket è assegnato un protocollo di trasporto.
	- fatto il comando ```~>ss``` su linux, si ottiene la lista di processi socket attivi.
		- Da qui si vede il protocollo di trasporto, l'ip locale con la sua porta e l'ip remoto e la sua porta.
		- Se i processi sono locali, quelli non tcp/udp l'ip è sostituito dal percorso assoluto da cui è partito il processo
- Perchè usare una socket?
	- Ci si può sbizzarrire a proposito
		- Ad esempio per collegare due dispoitivi diversi o anche per collegare due processi di due sistemi diversi
- Come usare una socket?

La socket ha ovviamente uno *STATE*, che può essere in LISTEN, nel caso stesse ascoltando da un client, o ESTABilished quando sia da una parte che dall'altra ci sono stati pacchetti di risposta.