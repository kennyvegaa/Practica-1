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
![i need a screenshot](https://github.com/kennyvegaa/Practica-1/issues/2#issuecomment-548981104)
![https://github.com/kennyvegaa/Practica-1/issues/2#issuecomment-548981104].(src)
<img src="https://github.com/kennyvegaa/Practica-1/issues/2#issuecomment-548981104" />

De la gráfica anterior observas, ¿Cuál es su tendencia?

```markdown
Tendencia= "creciente"
  print(Tendencia)
```
```markdown
[1] "creciente"
```
¿Tiene periodicidad, muy evidente?
```markdown
Periodicidad= TRUE
  print(Periodicidad)
```
```markdown
[1] TRUE
```
Para verificar tus suposiciones realiza una gráfica con la descomposición del modelo 
Periodicidad+Tendencia+Aleatoriedad
```markdown
X= ts(EG,start=(1982), frequency = 12)
plot(decompose(X))
```
Sí tu base abarca, realiza una gráfica de caja para cada mes identificando valores atípicos, si sólo tiene un registro por año realiza una gráfica de caja con todos los datos identificando outlier (atípicos) y sí tu base tiene menos de dos años de información realiza una gráfica de caja con todos los datos identificando outlier (atípicos).

```markdown
boxplot(X, main="Diagrama de cajas", col= "mediumspringgreen")
```
es anual o menos de dos años de información
MesesOutlier=c("anual")
```markdown
MesesOutlier= c("anual")
  NumeroOutlier= c (1)
  Outlier=data.frame(MesesOutlier, NumeroOutlier)
print(Outlier)
```
```markdown
 MesesOutlier NumeroOutlier
1        anual             1
```
Realiza el correlograma de tu serie de tiempo
```markdown
acf(X, main= "Correlograma de EG")
```
¿Del correlograma anterior pudes asumir que las observaciones son correlacionadas entre si con un 95% de confianza?
```markdown
Correlacion= TRUE
  print(Correlacion)
```
```markdown
[1] TRUE
```
Descomponer la serie de tiempo en el modelo aditivo y realice gráfica.
```markdown
eg1.decom = decompose(X, type = "additive")
plot(eg1.decom)
```
¿Cuál es la estimación para la Tendencia estimada?
```markdown
TendenciaEstimadaAditivo=  eg1.decom$trend
  print(TendenciaEstimadaAditivo)
```
```markdown
  Jan      Feb      Mar      Apr      May      Jun      Jul      Aug
1982       NA       NA       NA       NA       NA       NA 116.1124 120.7725
1983 137.4793 138.4474 138.5727 139.9820 145.1567 153.4589       NA       NA
          Sep      Oct      Nov      Dec
1982 124.6625 127.5964 131.1420 134.9367
1983       NA       NA       NA       NA
```
¿Cuál es la estacionalidad (periodicidad) estimada?
```markdown
EstacionalidadEstimadaAditiva= eg1.decom$seasonal
  print(EstacionalidadEstimadaAditiva)
```
```markdown
Jan        Feb        Mar        Apr        May        Jun        Jul
1982 -14.215201  -4.759285   5.575382  17.734132  35.537465  26.031215  25.881715
1983 -14.215201  -4.759285   5.575382  17.734132  35.537465  26.031215  25.881715
            Aug        Sep        Oct        Nov        Dec
1982  15.831632   2.409632 -29.272285 -46.025868 -34.728535
1983  15.831632   2.409632 -29.272285 -46.025868 -34.728535
```
¿Cuál es el error estimado?
```markdown
ErrorEstimadoAditivo= eg1.decom$random
  print(ErrorEstimadoAditivo)
```
```markdown
 Jan      Feb      Mar      Apr      May      Jun      Jul      Aug
1982       NA       NA       NA       NA       NA       NA 2.607868 2.607868
1983 2.607868 2.607868 2.607868 2.607868 2.607868 2.607868       NA       NA
          Sep      Oct      Nov      Dec
1982 2.607868 2.607868 2.607868 2.607868
1983       NA       NA       NA       NA
```
Sume la tendencia con la estacionalidad
```markdown
AditivoModel1= (TendenciaEstimadaAditivo + EstacionalidadEstimadaAditiva)
  print(AditivoModel1)
```
```markdown
Jan       Feb       Mar       Apr       May       Jun       Jul
1982        NA        NA        NA        NA        NA        NA 141.99413
1983 123.26413 133.68813 144.14813 157.71613 180.69413 179.49013        NA
           Aug       Sep       Oct       Nov       Dec
1982 136.60413 127.07213  98.32413  85.11613 100.20813
1983        NA        NA        NA        NA        NA
```
Gráfique la serie de tiempo y sobre la misma gráfica imprima la suma de tendencia con estacionalidad
```markdown
plot(X,AditivoModel1, col=c(2,4))
```
Los Valores son parecidos: TRUE (Sí), FALSE (No)
```markdown
ParecidosAditivo="TRUE"
  print(ParecidosAditivo) 
```
```markdown
[1] "TRUE"
```
Descomponer la serie de tiempo en el modelo máltiplicativo y realice gráfica.
```markdown
eg.decom = decompose(X, type = "mult")
plot(eg.decom)
```
¿Cuál es la estimación para la Tendencia estimada?

```markdown
TendenciaEstimadaMultiplicativo= eg.decom$trend
  print(TendenciaEstimadaMultiplicativo)
```
```markdown
Jan      Feb      Mar      Apr      May      Jun      Jul      Aug
1982       NA       NA       NA       NA       NA       NA 116.1124 120.7725
1983 137.4793 138.4474 138.5727 139.9820 145.1567 153.4589       NA       NA
          Sep      Oct      Nov      Dec
1982 124.6625 127.5964 131.1420 134.9367
1983       NA       NA       NA       NA
```
¿Cuál es la estacionalidad (periodicidad) estimada?
```markdown
EstacionalidadEstimadaMultipicativo= eg.decom$seasonal
  print(EstacionalidadEstimadaMultipicativo)
```
```markdown
 Jan       Feb       Mar       Apr       May       Jun       Jul
1982 0.8995279 0.9672109 1.0404973 1.1252507 1.2406610 1.1658320 1.2235411
1983 0.8995279 0.9672109 1.0404973 1.1252507 1.2406610 1.1658320 1.2235411
           Aug       Sep       Oct       Nov       Dec
1982 1.1324826 1.0220217 0.7771652 0.6572030 0.7486066
1983 1.1324826 1.0220217 0.7771652 0.6572030 0.7486066
```
¿Cuál es el error estimado?:
```markdown
ErrorEstimadoMultiplicativo= eg.decom$random
  print(ErrorEstimadoMultiplicativo)
```
```markdown
Jan      Feb      Mar      Apr      May      Jun      Jul      Aug
1982       NA       NA       NA       NA       NA       NA 1.017834 1.017834
1983 1.017834 1.017834 1.017834 1.017834 1.017834 1.017834       NA       NA
          Sep      Oct      Nov      Dec
1982 1.017834 1.017834 1.017834 1.017834
1983       NA       NA       NA       NA
```
Multiplique la tendencia con la estacionalidad,
```markdown
MultiplicativoModel1= (TendenciaEstimadaMultiplicativo)* (EstacionalidadEstimadaMultipicativo)
  print(MultiplicativoModel1)
```
```markdown
Jan       Feb       Mar       Apr       May       Jun       Jul
1982        NA        NA        NA        NA        NA        NA 142.06831
1983 123.66650 133.90785 144.18457 157.51484 180.09022 178.90732        NA
           Aug       Sep       Oct       Nov       Dec
1982 136.77276 127.40777  99.16349  86.18692 101.01448
1983        NA        NA        NA        NA        NA
```
Gráfique la serie de tiempo y sobre la misma gráfica imprima la multiplicacion de tendencia con estacionalidad
```markdown
plot(X,MultiplicativoModel1, col=c(3,5))
```
Los Valores son parecidos: TRUE (Sí), FALSE (No)
```markdown
ParecidosMultiplicativo="TRUE"
print(ParecidosMultiplicativo)
```
```markdown
[1] "TRUE"
```
Realiza el modelo de Holt Winters usando la el modelo multiplicativo
```markdown
HoltWinters= HoltWinters(X, seasonal="mult")
  plot(HoltWinters)
```
Con el mismo modelo obten una predicción de 5 años posteriores a tus datos
```markdown
HoltWintersPredict=predict(HoltWinters,n.ahead=5)
  ts.plot(X, HoltWintersPredict, lty=1:2)
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
