## Ejercicio 1

Primero cargamos la siguiente paqueteria:

```markdown
install.packages("TSA")
library(TSA)
```
Ahora leemos los datos
```markdown
data(units)
EG=units
EG
```
```markdown
Time Series:
Start = 1982 
End = 2005 
Frequency = 1 
        Units
 [1,]  71.746
 [2,]  78.580
 [3,] 111.112
 [4,] 125.554
 [5,] 132.978
 [6,] 141.350
 [7,] 144.602
 [8,] 139.212
 [9,] 129.680
[10,] 100.932
[11,]  87.724
[12,] 102.816
[13,] 125.872
[14,] 136.296
[15,] 146.756
[16,] 160.324
[17,] 183.302
[18,] 182.098
[19,] 164.878
[20,] 142.170
[21,] 129.730
[22,] 134.704
[23,] 178.144
[24,] 211.650
```
De la series de datos que obtuviste, cuál es la clase de tu serie de tiempo
```markdown
Clase= class(EG)
print(Clase)
```
```markdown
[1] "ts"
```
Identifica la frecuencia de registro de tus datos a través de una función de R
```markdown
Frecuencia= frequency(EG)
  print(Frecuencia)
```
```markdown
[1] 1
```
Con la función anterior escribe la frecuencia de los datos en palabras
```markdown
FrecuenciaLetra= "anual"
  print(FrecuenciaLetra)
```
```markdown
[1] "anual"
```
Identifica el año y mes/día/trimestre en el que la serie de datos comienza a registrarse 
```markdown
Inicio=start(EG)
  print(Inicio)
```
```markdown
[1] 1982    1
```
Identifica el año y mes/día/trimestre en el que la serie de datos términa a registrarse 
```markdown
Final= end(EG)
  print(Final)
```
```markdown
[1] 2005    1
```
Gráfica tu serie de tiempo, recuerda poner, título principal, y a los ejes.
```markdown
plot(EG, xlab = "Tiempo", ylab = "Unidades", lty = c(1,2),
     main ="Ventas anuales de ciertos equipos grandes",cex.main=1.5, col= "darkturquoise")
```
image (https://github.com/kennyvegaa/Practica-1/issues/2#issuecomment-548981104)

```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```
```markdown

```

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/kennyvegaa/Practica-1/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
