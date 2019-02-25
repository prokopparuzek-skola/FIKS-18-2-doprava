---
header-includes:
	\usepackage[czech]{babel}
	\usepackage{a4wide}
---
# Meziměstská doprava
## Řešení
### Algoritmus
Začneme tím, že porovnáme ID osob, které z měst 1-24 odjely s těmi které přijeli, pokud nalezneme odchylku, máme ID 
hledané osoby i s městem kde je. Provedme to takto: prvně u každého města vyhledáme všechny přepravníky, které v něm 
začínají a uděláme z jejich intervalů jeden velký, možná rozdělený. Uložíme si první interval, ve tvaru začátek 
konec(IDx:IDy),  a pak přidáváme další. Vezmeme IDx a hledáme interval kam patří, případně meziinterval. Hledáme 
binárním hledáním, začneme v prostředku, pokud IDx patří do intervalu, skončíme, jinak hledáme buď vprav, nebo vlevo 
podle velikosti IDx(porovnáváme s velikostí IDx intervalu). To samé provedeme u IDy. Pokud je IDx uvnitř již 
existujícího intervalu, vezmeme jako počátek nového intervalu IDx intervalu kam patří, jinak použijeme IDx. Poté 
postupujeme k IDy a pokud narazíme na jiné IDx nebo IDy odstraníme ho. Jestliže je IDy v intervalu skončíme v IDy daného 
intervalu, jink vezmeme IDy. Takto by nám měl vzniknout souhrnný interval pro všechny odjezdy i příjezdy do daného 
města.
Poté všude porovnáme interval příjezdůa odjezdů, když najdeme odchylku, člověka co je navíc, tak získáme ID i město kde 
je. Nalezneme ho jako číslo, nebo interval(o jediném členu) navíc u příjezdů oproti odjezdům.

### Složitost
Pokaždé když zařazujeme ID, trvá nám to `O(log(N))`. Potom musíme projít N intervalů abychom vytvořili interval. Celková 
složitost je tedy:
```
O(2log(N) + N)
```
tedy
```
O(log(N))
```
