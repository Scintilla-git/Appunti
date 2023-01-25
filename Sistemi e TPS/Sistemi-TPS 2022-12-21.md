## TPS
### Algebra Astratta - Gruppi con numero finito di elementi
#### Gruppi ciclici
Definiamo un gruppo: (G, +), e G è finito.

- La domanda è:
	- Esiste a appartenente a G tale che per ogni g appartenente a G => g = a + ... + a
		- a diventa un **numero generatore**
			- un numero generatore è un numero che, in un ciclo, dà almeno una volta in un ciclo tutti i numeri presenti nel gruppo
				- Esempio dell'orologio(numeri dal 0 al 7)
					- 1 è un generatore, così come 3, 5 e 7
				- Stessa cosa con l'orologio da 12
					- in questo caso i numeri generatori sono 1, 5, 7, 11
				- Nel caso dell'orologio da 5, tutti i numeri sono generatori
			- *Dunque se un gruppo non è commutativo, allora non ha generatori.
			  Se un gruppo ha dei generatori, allora è commutativo*
		- **G viene definito ciclico**
	- L'ordine di G è l'inisieme di elementi con compongono il gruppo.
		- G = \#G
		- facciamo un esempio
			- sia g appartenente a G
			- (g) = h
				- indica tutti gli elementi che possiamo costruire usando solo g
				- questo è anche considerato sottogruppo di g
				- tutti gli elementi qui dentro sono somme di g
			- alla fine avremo una cosa del genere:
				- g + g + ... + g => g^n
				- g^n = g^m
					- questo perchè, nonostante n e m siano diversi, alla fine aggiungendo g da una parte o dall'altra, prima o poi diventeranno uguali
				- g^x-1 = 0(neutro)

#### Transitività
(H è un sottogruppo di G)
- a = b %H e b = c %H, quindi c = a %H
	- a + b(neg) = h1
	- b + c(neg) = h2
		- H fanno parte h1 + h2 = a + b(neg) + b + c(neg) = a + c(neg) appartengono ad H

Quindi {x ∈ G : a + x(neg) ∈ H} <= *Classe*
- - - - -- - - -
Tutti gli argomenti sono segnati qui -> [RSA e Strutture Algebriche](RSA.pdf "yeet") 
Continuo in [Sistemi-TPS 2023-1-11](Sistemi-TPS%202023-1-11.md)