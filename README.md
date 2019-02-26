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
začínají a uděláme z jejich intervalů jeden velký, s informací kolikrát lidé přijeli/odjeli, možná rozdělený.

Uložíme si první nalezený interval, ve tvaru začátek konec(IDx:IDy),  a pak přidáváme další. Vezmeme IDx a hledáme 
interval kam patří, případně meziinterval. Hledáme binárním hledáním, začneme v prostředku, pokud IDx patří do 
intervalu, skončíme, jinak hledáme buď vprav, nebo vlevo podle velikosti IDx(porovnáváme s velikostí IDx intervalu). To 
samé provedeme u IDy. Vezmeme IDx a zjistíme jeho výšku, tj. kolikrát již dané IDx přijelo/odjelo, to si zapamatujeme. 
Poté postupujeme k další hranici intervalu, již zapsaného. Pokud je po přičtení jedničky k jeho úrovni, stejně vysoko 
jako náš interval, pokračujeme. Pokud je menší propadneme a pokračujeme níže, adektvátně snížíme úroveň, pokud výše 
stoupneme. Pokud zaplníme mezeru mezi intervaly sloučíme je.

Poté všude porovnáme interval příjezdů a odjezdů, když najdeme odchylku, člověka co je navíc, tak získáme ID i město kde 
je. Nalezneme ho jako číslo, nebo interval(o jediném členu) navíc u příjezdů oproti odjezdům. Musíme porovnat úrovně 
intervalů.

### Složitost
Pokaždé když zařazujeme ID, trvá nám to `O(log(N))`. Potom musíme projít N intervalů abychom vytvořili interval. Celková 
složitost je tedy:
```
O(2log(N) + N)
```
tedy
```
O(log(N) + N)
```
