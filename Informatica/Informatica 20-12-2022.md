## Introduzione alla progettazione logica dell'E-R

### Ristrutturazione del modello E-R
- **Partecipazione delle entità alle relazioni**
	- ovvero tutte le entità devono essere collegate ad almeno un'altra entità.
- **Eliminazione degli attributi composti**
	- nel caso ci fossero degli attributi composti si può procede così:
		- considerare i sotto-attributi come attributi
		- eliminare i sotto-attributi e considerare l'attributo compost come semplice
- **Eliminazione degli attributi multivalore**
	- eventuali attributi multivalore presenti devono essere convertiti a entità
		- l'entità creata contiene i valori dell'attrbuto e va collegato tramite una relazione(1 a molti) all'entità che possedeva l'attributo
- **Eliminazione delle gerarchie e specializzazioni**
	- La gerarchia deve essere trasformata in una unica entità
	- Si può ristrutturare in due modi:
		- eliminazione dei figli(*collasso dei figli*), che vengono trasformati in attributi
		- eliminazione del padre(*Esplosione dei figli*), i cui attributi vengono trasferiti ai figli

### Traduzione del modello E-R nel modello relazionale
- **Trasformazione delle entità**
	- Per ogni entità viene generata una tabella indicando il suo schema relazionale:
		- Esempio: *Entità*(Attributo, AttributoChiave(*pk*))
- **Trasformazione delle relazioni**
	- Si effettua la trasformazione delle associazioni, in base al numero di entità partecipanti e alla loro cardinalità
		- *Unificare le relazioni uno-a-uno*
			- Due entità collegate da una relazione 1-1 possono essere ridotte a un'unica entità che contiene tutti gli attributi delle due entità
		- *Semplificazione delle relazioni molti-a-molti*
			- non possono essere rappresentate nel modello relazionale
			- Bisogna fare in modo che la relazione diventi un'entità, dando eventualmente degli attributi alla relazione
			- Esempio:
				- Impiegato(attributi)
				- Progetto(attributi)
				- Impegno(*ex-relazione*)(attributi di collegamento tra le due entità)
					- Gli attributi di collegamento sono le pk e quelli della ex-relazione
- **Eliminazione delle ternarie**
	- Relazioni di questo tipo vengono eliminate e viene creata una seconda relazione che collega le tre entità
- **Relazioni ridondanti**
	- I percorsi chiusi vanno eliminati
		- Alla fine in un database i dati sono in una tabella, quindi non serve a niente!

>Esempio a pagina 100 del libro

