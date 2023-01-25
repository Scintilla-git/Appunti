## Algebra astratta - Teorema di Lagrange
Prendiamo un sottogruppo H di G.
Facciamo questa operazione:
>prendiamo h ∈ H
>{h\*a ∀ h ∈ H} = Ha
>Sostanzialmente sto moltiplicando gli elementi di H per a. Per assurdo, il numero di elementi di Ha sono gli stessi di H.
>
>o(Ha) > o(H)
>Chiaramente una cosa del genere non può accadere.
>Invece questo può accadere:
>o(Ha) < o(H)
>Se ∃ h1 != h2 ∈ H : h1a = h2a -> h1 = h2
>Ma questa è una contraddizione.
>Quindi per concludere, Ha non può avere ne più ne meno elementi di H.

### Ma Ha può essere un sottogruppo?
La risposta è dipende da a.
La domanda seguente sorge quasi spontanea:
- Per quali elementi di a, Ha diventa sottogruppo;
- Per quali elementi di a, Ha non è sottogruppo.

Da questo punto di vista, se a = e(Elemento Neutro), allora Ha è sottogruppo.

Inoltre, con h ∈ H, Hh(neg) è sottogruppo di H!

## Teorema di Eulero
n ∈ N.
phi(n) = numero di elementi di n stesso che non hanno divisori comuni.
>n = 10
>cerchiamo i divisori comuni tra i primi 9 numeri:
>l'1 lo consideriamo di base.
>il 2 lo buttiamo
>il 3 lo prendiamo
>il 4 no
>il 5 neanche
>il 6 nemmeno
>il 7 si
>l'8 no
>il 9 si
>Dunque il phi(n) = 4

Altri esempi, phi(4) = 2, phi(15) = 8
Piccolo trucchetto:
se n = p\*q (dove p e q sono primi)
-> phi(n) = (p-1)(q-1)
perchè?
>phi(n) = n - q - p +1
>= pq - q - p +1
>= q(p - 1) - p + 1
>= q(p - 1) - (p - 1)
>= (q - 1)(p - 1)

Ma prendiamo un numero primo n.
n=7, phi(6).
La risposta è semplice, un numero primo non ha divisori oltre a 1.

Infine, un'ultima formuletta:
>a,n ∈ N e H(a,n) = 1
>a^phi(n) % n = 1

- - - - -
Continuo in [Sistemi-TPS 2023-1-18](Sistemi-TPS%202023-1-18.md).