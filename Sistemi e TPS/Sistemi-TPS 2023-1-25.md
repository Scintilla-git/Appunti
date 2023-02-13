## Algebra astratta e dimostrazione dell'RSA
### Gruppo moltiplicativo modulo N
Scegliamo un insieme F = {0, 1, ..., n-1}. 
Creiamo il gruppo Jn, dove gli elementi che ne fanno parte rispettano questa formula:
>g ∈ G implica che ∃ g^-1 ∈ F : g \* g^-1 ≡ 1%p
>
>Facciamo un esempio:
>J5 = 5 <- F = {0, 1, 2, 3, 4}
>1 è inverso di se stesso
>2 è inverso di 3 (2\*3%5 = 1)
>4 è inverso di se stesso (4\*4%5 = 1)

#### Divisori dello zero
Definiamo tutti i divisori dello 0 tutti quei valori a != 0 per cui esiste un numero x tale che ax%n = 0
>Facciamo un esempio:
>n = 20 e vediamo quali numeri fanno parte di J20:
>0 è escluso, 1 funziona sempre.
>2 non ha inverso, e 2\*10 = 20 ≡ 0%20
>3 ha come inverso 7(e viceversa)
>4 e 5 sono divisori di 0
>6 è divisore -> 6\*10 = 60 ≡ 0%20
>8 è divisore
>9 è inverso di se stesso, così come 11
>il 10 e il 12 sono divisori
>13 è inverso di 17
>14, 15, 16 e 18 sono divisori
>19 è inverso di se stesso

Giungiamo a una conclusione interessante:
- Prendiamo un numero n, creiamo il gruppo e sappiamo che il numero n-1 è sempre inverso di se stesso e non è mai divisore di 0

#### Elementi invertibili
Se due numeri(a, p) sono coprimi allora si possono calcolare altri due numeri interi(x, y) tale che si verifica l'ugualiganza
>ax + py = 1

Che implica
>ax ≡ 1%p

Quindi x = a^-1 che sono inversi rispetto alla *moltiplicazione modulo p*.

#### n=pq
n non è un numero primo, ma è sempre la moltiplicazione tra due numeri primi p e q, con p != q.
Da F = {0, 1, 2, ..., n-1} dobbiamo togliere:
- lo zero
- multipli non nulli di p
- multipli non nulli di q

Dunque in questo gruppo avremo q-1 multipli di p e p-1 multipli di q.
Quindi restano:
- n - (p-1) - (q-1) - 1 elementi

E con quanto formula algebrica ci porta poi a dire che
>phi(n) = (p-1)(q-1)
>
>Facciamo un esempio:
>n = 15
>15 = 3 \* 5
>phi(n) = 2 \* 4 = 8
>in phi(n) quindi ci sono solo 8 elementi invertibili.

### A questo punto, dimostriamo l'RSA
Prendiamo e e d, oltre a n(=pq), e creiamo i gruppi (e, n) che chiameremo encrypting key, e (d, n) che chiameremo decrypting key.
>ed%phi(n) = 1 che implica ed = a\*phi(n)+1, a ∈ N

Chiamiamo un numero messaggio da inviare m.
Criptiamo il messaggio così:
- c = m^e%n

E lo decriptiamo:
- t = c^d%n

E questo sappiamo che t = m.
Perchè?

#### Dimostrazione
t = c^d %n ≡ (m^e)^d %n ≡ m^ed %n ≡ m^(a\*phi(n)+1) %n

Diciamo che m e n sono coprimi.
A questo punto possiamo applicare il teorema di Eulero gen. e possiamo affermare che:
>m^phi(n) %n ≡ 1

E a questo punto:
> (cose)

Ma questo opzione non è valida sempre(nonostante abbia una probabilità del 99,99999999% di capitare).

Finale in [Sistemi-TPS 2023-2-1](Sistemi-TPS%202023-2-1.md).

- - - -
## Firewall pt.2
### Protocolli e moduli
>iptables -A INPUT -p tcp -j DROP

Con questo comando ho appena detto al filtro di bloccare tutte le richieste del protocollo tpc.
Quindi se provo a collegarmi a qualsiasi sito internet, i pacchetti vengono rifiutati e scartati, e il browser continua a caricare, senza successo.

>iptables -A INPUT -p udp -j DROP

Mentre con questo blocco tutte le volte che un URL sta cercando di ottenere il suo indirizzo ip.

Volendo si può fare anche con il protocollo icmp.

Passiamo ai moduli:
>iptables -A INPUT -p tcp -m tcp --dport 22 -s [ip] -j DROP

Questo comando differenzia da quelli precedente perchè blocca tutti gli ip che provano a collegarsi in tcp al tuo pc passando per la porta 22.
