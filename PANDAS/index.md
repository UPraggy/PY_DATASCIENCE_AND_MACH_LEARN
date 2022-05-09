# ACESSO À PORTA SERIAL

# SUMÁRIO
- **[INTRODUÇÃO](#introdução)**
- **[LIMITES](#limites)**
- **[DERIVADA](#derivada)**
- **[RETA TANGENTE A UMA CURVA](#reta-tangente-a-uma-curva)**
- **[CALCULO VETORIAL](#calculo-vetorial)**


# INTRODUÇÃO
Neste Módulo, tem como objetivo resumir os conceitos de Calculo II.
**Ele será resumido em topicos simples com base em alguns conceitos e formulas baseados no que o professor passou em sala e em breve oque consta no Conteúdo digital.**

# LIMITES
```
Supondo que lim F(x) e lim G(x) existam e C é um numero real então
            x->a       x->a 
```
## FORMÚLAS
```
lim [F(x) +- G(x)] = lim F(x) +- lim G(x)
x->a                 x->a        x->a

 
lim C * F(x) = C * lim F(x)
x->a               x->a       

 
lim [F(x) * G(x)] = lim F(x) * lim G(x)
x->a                 x->a      x->a
 
 
lim [F(x) / G(x)] = lim F(x) / lim G(x)
x->a                x->a       x->a


lim F(x)ⁿ = [lim F(x)]ⁿ
x->a         x->a  


lim √F(x) = √[lim F(x)]
x->a          x->a    


lim |F(x)| = |lim F(x)|
x->a          x->a  


lim C = C
x->a  


lim x = a
x->a 

lim 1/xⁿ = 0
x->+-∞ 

lim K = K
x->+-∞  
```
# DERIVADA  
## FORMÚLAS
```
C' = 0

(xⁿ)' = n*xⁿ⁻¹

(C * xⁿ)' = C * n*xⁿ⁻¹

(C * F(x))' = C * F(x)'

(F(x) +- G(x))' = F(x)' +- G(x)'

(F(x) * G(x))' = F(x)' * G(x) + F(x) * G(x)'

(F(x) / G(x))' = [F(x)' * G(x) - F(x) * G(x)']/ G(x)²
```

# RETA TANGENTE A UMA CURVA
- **[COEFICIENTE ANGULAR DA RETA TANGENTE](#coeficiente-angular-da-reta-tangente)**
- **[EQUAÇÃO DA RETA TANGENTE](#equação-da-reta-tangente)**

## COEFICIENTE ANGULAR DA RETA TANGENTE

### FORMÚLA
```
Mt = lim (F(X₁ + ΔX) - F(X₁)) / Δx
     Δx->0  
```
### EXEMPLO
> Encontre a inclinação da reta tangente a curva ```Y = x² -6x + 8``` o ponto ```(X₁,Y₁)```

```
Mt = lim (F(X₁ + ΔX) - F(X₁)) / ΔX
     Δx->0 

F(X₁ + ΔX) = (X₁ + ΔX)² -6(X₁ + ΔX) + 8 = (X₁)² + 2X₁ΔX + ΔX² -6X₁ -6ΔX + 8
F(X₁ + ΔX) = (X₁)² + 2X₁ΔX + ΔX² -6X₁ -6ΔX + 8

F(X₁) = (X₁)² -6X₁ + 8


Mt = lim  ((X₁)² + 2X₁ΔX + ΔX² -6X₁ -6ΔX + 8 - ((X₁)² -6X₁ + 8)) / ΔX
     Δx->0
Mt = lim  ((X₁)² + 2X₁ΔX + ΔX² -6X₁ -6ΔX + 8 -(X₁)² +6X₁ -8) / ΔX
     Δx->0
Mt = lim   (2X₁ΔX + ΔX² -6ΔX)/ ΔX
     Δx->0
Mt = lim   ΔX(2X₁ + ΔX -6)/ ΔX
     Δx->0
Mt = lim   2X₁ + ΔX -6
     Δx->0
     
Mt = 2X₁ -6
```
## EQUAÇÃO DA RETA TANGENTE

### FORMÚLA
``` 
Y - Yₒ = m(X - Xₒ)
```
### EXEMPLO
> Encontre a equação da reta tangente em que ```F(X) = 3X² - 5X```; ponto ```X = 1/2```; <br>```m = 6X - 5```<br>
> OBS.:  m = Mt 

```
Yₒ = F(Xₒ) = F(1/2) = 3X² - 5X = 3(1/2)² - 5(1/2)
F(1/2) = 3(1/4) - 5(1/2)
F(1/2) = 3/4 - 5/2
F(1/2) = (3 - 10)/4
F(1/2) = -7/4

Y - Yₒ = m(X - Xₒ)
Y - Yₒ = (6X - 5)(X - Xₒ)
Y - (-7/4) = [6(1/2) -5](X -1/2)
Y + 7/4 = (6/2 -5)(X -1/2)
Y + 7/4 = (-4/2)(X -1/2)
Y + 7/4 = (-2)(X -1/2)
Y + 7/4 = -2X +1
(4Y + 7)/4 = (-8X + 4)/4
4Y + 7 = -8X + 4
4Y + 8X + 7 - 4 = 0
4Y + 8X + 3= 0
```
> equação da reta tangente ```4Y + 8X + 3= 0```


# CALCULO VETORIAL
- **[CONCEITOS](#conceitos)**
- **[MODULO](#modulo)**
- **[SOMA DE DOIS VETORES](#soma-de-dois-vetores)**
- **[MULTIPLICAÇÃO ESCALAR](#multiplicação-escalar)**


## CONCEITOS
> **Vetor** -> Segmento orientado<br>
> **Magnitude** -> O mesmo que **Modulo**, distancia percorrida ou comprimento de um vetor

## MODULO
### FORMÚLA


## SOMA DE DOIS VETORES
### FORMÚLA
Dado um vetor **-W->** = (Xᵢ,Yᵢ) e **-V->** = (Xₒ,Yₒ)
```
-W-> + -V-> = (Xᵢ,Yᵢ)  + (Xₒ,Yₒ)
-W-> + -V-> = (Xᵢ + Xₒ,Yᵢ + Yₒ)
```

## MULTIPLICAÇÃO ESCALAR
### FORMÚLA
Dado um vetor **-V->** = (Xₒ,Yₒ) e um escalar real **a**
```html
a * -V-> = (aXₒ,aYₒ)
```
