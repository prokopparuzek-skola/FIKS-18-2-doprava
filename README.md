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
začínají a uděláme z jejich intervalů jeden velký.
### Složitost
