## Resoconto Primo Quadrimestre 2022-23

### Modello ISO-OSI

Per modello ISO-OSI si intende il modello che e' stato approvato dall'**International Standards Organization**, ed e' utilizzato come primo passo per l'assegnazione dei protocolli nei vari livelli.
Questo modello prende il nome di OSI, ovvero **Open System Interconnection**.
I livelli del modello OSI sono 7:
- 1 - Livello fisico
- 2 - Livello DataLink
- 3 - Livello Network
- 4 - Livello di transporto
- 5 e 6 - Livelli di sessione e presentazione
- 7 - Livello di Applicazione

![[OSI_Model_v1.svg.png]]

Ovviamente ognuno di questi livelli ha uno suo scopo:

#### 1 - Livello fisico
>Il livello fisico si occupa semplicemente di **controllare la rete, gli hardware che la compongono e i dispositivi che permettono di stabilire, mantenere e disattivare una connessione o un collegamento fisico.**
>
>Inoltre, questo livello decide diverse altre cose, come il numero di bit per un collegamento, la durata in microsecondi che identifica un bit, la modulazione e la codifica utilizzata, e altro.
>
>Alcuni apparecchi che lavorano a questo livello sono i router e gli hub.
- Servizi come il Bluetooth e' gestito in questo livello

#### 2 - Livello DataLink
>Il livello DataLink si occupa di permettere il **trasferimento affidabile di dati attraverso il livello fisico**. Invia frame di dati con la necessaria sincronizzazione ed effettua un controllo degli errori e delle perdite di segnale. Tutto ciò consente di far apparire, al livello superiore, il mezzo fisico come una linea di trasmissione esente da errori di trasmissione.
>
>A questo livello e' assegnato anche una unita' di dati fondamentale, ovvero il **frame**.
>
>Gli apparecchi a questo livello sono switch e bridge.
- Sono gestiti protocolli come Ethernet e Wi-Fi

#### 3 - Livello Network
>Obiettivo: rendere i livelli superiori indipendenti dai meccanismi e dalle tecnologie di trasmissione usate per la connessione e prendersi carico della consegna a destinazione dei pacchetti.
>
>E' Responsabile del routing e della conversione dei dati nel passaggio fra una rete e l'altra 
>
>A questo livello lavorano i router
- E' gestito qui il protocollo IP

#### 4 - Livello trasporto, sessione e presentazione
>Livelli meno importanti, che sostanzialmente permettono il trasferimento di dati trasparente e affidabile(**trasporto**), controllare la comunicazione tra applicazioni(**Sessione**) e trasformare i dati forniti dalle applicazioni in un formato standardizzato e offrire servizi come la crittografia(**Presentazione**)
- Qui sono gestiti protocolli come TCP e UDP

#### 5 - Livello Applicazione
>Questo livello si occupa delle funzioni di interfaccia tra utente e macchina
- Sono gestiti tutti i protocolli di servizio, come il DHCP e il DNS, di accesso a terminali remoti, come l'SSH, protocolli di posta elettronica, come l'SMTP, il POP e l'IMAP, e di trasferimento file, come l'FTP e l'HTTP.

### Protocolli
Cos'è un protocollo?
>Un protocollo, in informatica, equivale a un insieme di regole che definiscono la modalità di comunicazione tra due o più entità.

I protocolli più usati, o comunque che hanno una maggiore rilevanza, sono:
- HTTP/S
	- Ovvero l'**Hypertext Trasfer Protcol / Secure**, protocollo utilizzato per di più nei siti web
- TCP
	- Ovvero il **Transmission Control Protocol**