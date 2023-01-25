## Algebra Astratta: Piccolo teorema di Fermat
Facciamo un piccolo passo indietro:
*Il teorema di Eulero* dice "sia a un numero intero e n naturale coprimi fra loro, a^phi(n)%n = 1"
Ricoridamo anche che il teorema cade se i numeri non sono coprimi!
>a = 18 e n = 9 non sono coprimi, infatti il risultato è 0

Questo teorema dice che:
>prendiamo a un numero a caso e p un numero primo
>a^p%p = a%p

E questo funziona, e meno che a è multiplo di p, cui risultato darà 0.

Ma consideriamo alcune cose:
1. l'MCD(a,p) = 1
	- Implica che a non è multiplo di p
	- Vale Eulero: phi(p) = p-1
		- Quindi: a^phi(p)%p = 1 -> a^p-1%p = 1
		- Possiamo fare che (a^p-1%p)\*a%p = a%p
			- Quindi: a^p%p = a%p
2. Se l'MCD(a,p)>1 allora MCD(a,p) = p
	- La dimostrazione è facile, l'mcd di un numero primo è 1 o se stesso, ma se 1 non può essere, la risposta è piuttosto ovvia!
		- Torniamo quindi alla dimostrazione:
		  a^p%p = (xp)^p%p = 0
		- Quindi a%p = xp%p = 0

### Generalizziamo qualcosina
**Teorema di Eulero generalizzato**
Usiamo come esponente un multiplo intero di phi(n). Quindi k phi(n), con k ∈ N
>a^(k\*phi(n))%n ≡ 1;
>k ∈ N
>(a,n) = 1

**Piccolo Teorema di Fermat generalizzato**
Dato un numero primo p e un numero e tale che *e ≡ 1%(p-1)*, possiamo dire che *e%(p-1)=1*
Quindi:
>e ≡ 1%(p-1)
>e %(p-1) = 1
>e = k(p-1) +1
>e%(p-1) = [k(p-1) + 1]%(p-1) = [k(p-1)]%(p-1)+1%(p-1) = 0 + 1 = 1

Se k = 1, e = k(p-1) +1 = (p-1) + 1= p
Se k = 0, e = 1

Allora
>a^e%p = a%p 
>--se k=1--> a^p%p = a%p --> Ovvero il piccolo teorema di Fermat!
>--se k>1--> a^(k(p-1)+1)%p = a%p --> Ovvero la generalizzazione!

Conclusione in [Sistemi-TPS 2023-1-25](Sistemi-TPS%202023-1-25.md).