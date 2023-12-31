# Vulnerabilidad_PSSWRD
Proyecto Final de Estadística y Probabilidades
--------------------------------------------------
---
# La vulnerabilidad de las contraseñas de redes sociales hoy en día desde la generación centenial hasta la Generación X de la población de Lima metropolitana

---

------------------------------------------------------------------------

| <span style="color:#0CB0F6">**INTEGRANTES** | <span style="color:#0CB0F6">**CÓDIGO** | <span style="color:#0CB0F6">**PARTICIPACIÓN** |
|---------------------------------------------|:--------------------------------------:|:---------------------------------------------:|
| Valeria Arana Uzátegui                      |               202110015                |                     100%                      |
| Gabriel Blanco Gutierrez                    |               202210049                |                     100%                      |
| Katherine Lopez Villano                     |               202220312                |                     100%                      |
| José Barrenechea Merino                     |               202110512                |                     100%                      |
| Cristian Flores Pérez                       |               202120222                |                      15%                      |

# **INTRODUCCIÓN**

<div/>

<div style="text-align: justify">

Hoy en día vivimos en un mundo más conectado y dependiente de las redes
sociales, estas pueden ser nuestras mejores alidas como tambien algo
perjudicial para nosotros. Aplicaciones como Whattssap, facebook e
Instagram nos permiten estar informados permamentemente de lo que pasa
en todo el mundos. Sin embargo al crear una cuenta en estas apliciones
corremos el riesgo a ser hackeados, ya que estas aplicaciones pueden
acceder a una base de datos en donde se encuentran todos nuestros datos
personales.

-   **RELEVANCIA** Conocer la brecha tecnológica en cuanto a seguridad
    en sus cuentas de instagram en la generacion centenial hasta la
    generación X. Asimismo, este estudio estadístico busca informar a
    las personas sobre la seguridad de sus cuentas de Instagram.

# **OBJETIVOS**

## - **General**

Comparar la calidad de seguridad entre las contraseñas creadas por
personas de la generación centenial hasta la generación X.

## - **Específico**

Determinar que generación presenta una mayor seguridad al crear su
cuenta de de red social

Analizar la influencia que tiene la edad de los participantes al momento
de establecer una contraseña de seguridad en sus cuentas de red social.

Demostrar que la generación X es la más propensa a ser hackeada.

Determinar la relación entre cantidad de caracteres y la seguridad en
sus cuentas de red social.

# **DATOS**

## **Proceso de recolección de datos**

En esta oportunidad la recolección de datos se dará a través de una
encuesta enfocada en el rango poblacional elegido. Se utilizará la
herramienta de Google Forms, debido a su sencilla elaboración. Asimismo,
nos permitirá descargar los datos obtenidos en formato csv.

En cuanto al rango de tiempo para la recolección de datos se dió desde
el 30 de abril hatsa el 5 mayo del 2023.

## **Población de muestra y muestreo**

-   **Población:**Generación centenial hasta la generación X.

-   **Muestra:** Generación centenial hasta la generación X que usen
    instagram.

-   **Unidad muestral:** Una persona de la generación centenial,
    milenial y X que utilice instagram.

-   **Muestreo:** Muestreo Probabilístico aleatorio Simple.

## **Variables**

------------------------------------------------------------------------

| <span style="color:#0CB0F6">**Variables**                | <span style="color:#0CB0F6">**Tipo de variable** |
|:---------------------------------------------------------|:-------------------------------------------------|
| Edad                                                     | cuantitativa discreta                            |
| Cantidad de redes sociales                               | cuantativa discreta                              |
| Cantidad de caracteres de la contraseña                  | cuantitiva discreta                              |
| Características de la contraseña                         | cualitativa nominal                              |
| Cantidad de veces hackeado                               | cuantitiva discreta                              |
| Nivel de seguridad                                       | cualitativa ordinal                              |
| Frecuencia con la que utiliza más seguido redes sociales | cualitativa ordinal                              |
| Tipo Generación                                          | cualitativa nominal                              |
| Género                                                   | cualitativa nominal                              |
| Tiempo que lleva instalado redes sociales                | cuantitativa continua                            |
| Tiempo en horas al día que utiliza Instagram             | cuantitativa discreta                            |
| Espectro de seguidores                                   | cualitativa ordinal                              |
| Tiempo que cambias la contraseña de redes sociales       | cuantitativa continua                            |

# **INSTALAMOS LIBRERÍAS**

```{r}
#install.packages("readr")
```

```{r}
#install.packages("readr")
```

```{r}
library("ggplot2")
library(stringr)
library(dplyr)
library(readr)
```

```{r}
cv <- function(X){
  return (sd(X, na.rm = T)/mean(X, na.rm = T))
}
```

```{r}
r <- function(n){
  round(n ,2)
}
```

```{r}
#install.packages("stringr")
```

```{r}
#install.packages("ggplot2")
```

## **Remonbramos la base de datos y leemos datos de la data**

```{r}
VDC=read.csv("~/Documents/GENERALES UTEC/ESTADÍSTICA/PROYECTO ESTADISTICA/_LA VULNERABILIDAD DE LAS CONTRASEÑAS DE INSTAGRAM  (respuestas) - Respuestas de formulario 1.csv")
```

```{r}
ncol(VDC) # leer el número de columnas(variables)
nrow(VDC) # leer la cantidad de filas (obervaciones o número de unidades elemetales)
dim(VDC) # Devuelve las dimensiones de la base de datos (f*c)
```

```{r}
#str(VDC) # Resuemen del tipo de variable de la base de datos
```

```{r}
#summary(VDC) #Resumen general de la base de datos
```

# **LIMPIEZA DE DATOS**

#### Renombramos la data:

```{r}
VDC= rename(VDC,Edad = 'Edad.en.años.cumplidos...ejemplo..19..',Genero='Género..elegir.solo.una.opción.',Generacion = 'X.A.qué.generación.pertenece....importante..elegir.solo.una.opción.', Generacion= 'X.A.qué.generación.pertenece....importante..elegir.solo.una.opción.',RedesSociales='X.Cantidad.de.redes.sociales.que.utiliza.actualmente....Ejemplo..4.',  Tiempoinstalado= 'X.Desde.hace.cuánto.tiempo..en.años..utiliza.redes.sociales....Inserte.un.número.entero.o.decimal.', Seguidores='X.Cuántos.seguidores.tiene.en.sus.redes.sociales.aproximadamente.o.la.red.social.que.utiliza.más.seguido....Inserte.un.número.', Tiempodeuso= 'X.En.qué.momento.del.día.utiliza.más.seguido.redes.Sociales...elegir.solo.una.opción.', Canticaracteres ='X.Cuántos.caracteres.en.promedio.tienen.sus.contraseñas.de.redes.sociales...Inserte.un.número..Ejemplo..5',TipoCaracteres ='X.Qué.caracteres.contiene.generalmente.sus.contraseñas.de.redes.sociales...puede.seleccionar.más.de.una.opción.',Nseguridad = 'X.Considera.que.la.contraseñas.de.su.cuenta.de.red.social.es.segura...siendo.1..No.segura.y.5..Muy.segura.',Usodecontraseña= 'X.Prefiere.utilizar.una..misma.contraseña.para.ingresar.a.todas.sus.redes.sociales...elija.solo.una.opción.', Tcambiocontraseña = 'Hace.algunos.días.Facebook.publicó.en.su.blog.oficial.una.infografía.en.la.que.se.estima.que.a.diario.600.00.cuentas.de.Facebook.han.estado.en.peligro.de.ser.hackeadas....Sabiendo.esa.noticia.y.sobre.los.peligros.del.hackeo.en.redes.sociales..cada.cuánto.tiempo.en.días..cambiarías.tu.contraseña..',Cuentahackeada='X.Su.cuenta.ha.sido.hackeada.anteriormente...elija.solo.una.opción.', Numnotificaciones= 'X.Cada.cuántas.veces.al.día.usted.revisa.las.notificaciones.que.le.llegan.a.su.celular...inserte.un.número..Ejemplo..10'
)
```

### **Modificamos las categorías de Generacion**

```{r}
VDC$Generacion[VDC$Generacion == "Generación centenial ( comprende un rango de edad entre los 12 - 27 años )" ] = "Centenial"
```

```{r}
VDC$Generacion[VDC$Generacion == "Generación milenial  ( comprende un rango de edad entre los 28 - 41 años )"] = "Milenial"
```

```{r}
unique(VDC$Generacion)
```

```{r}
VDC$Generacion[VDC$Generacion =="Generación x ( comprende un rango de edad entre los 42 - 53 años )"] = "GX"
```

```{r}
names(VDC)
```

```{r}
#VDC
```

### **Exportar base de datos limpia**

```{r}
write_csv(VDC,"LIMPIOPROYECT.csv")
```

```{r}
VDC1 <-read_csv("~/Documents/GENERALES UTEC/ESTADÍSTICA/PROYECTO ESTADISTICA/LIMPIOPROYECT.csv")
VDC1
```

#### **Eliminamos las dos primeras columnas de variables, ya que no no contienen ningún dato**

```{r}
VDC1 <- VDC1 %>% select(3:16)
```

## **Aplicación de filtros**

```{r}
VDC1 <- VDC1 %>% filter(Edad >= 12 & Edad <= 53)
range(VDC1$Edad)
```

Con el fin de saber los valores máximo y mínimos de la variable redes
sociales aplicamos la función summary(). Dando como resultado lo
siguiente.

min: 1 máx: 1234

```{r}
range(VDC1$RedesSociales)
```

Dado que el máximo valor 1234, aplicaremos el siguiente filtro, ya que
no es posible que una persona tenga 1234 redes sociales generalmente
tienen entre 10 a 20 redes sociales.

```{r}
VDC1 <- VDC1 %>% filter(RedesSociales >= 1 & RedesSociales <= 20)
```

Con el objetivo que el programa Rstudio , me lea a la variable
Numnotificaciones como un `num` y no como un `chr` haremos lo
siguiente....

```{r}
VDC1 $Numnotificaciones <-as.numeric(VDC1$Numnotificaciones, na.rm=TRUE)
```

```{r}
VDC1$Tiempoinstalado<-as.integer(VDC1$Tiempoinstalado)
```

**Retiramos dato erróneo de Tiempo =\> 1900**

```{r}
VDC1 <- VDC1 %>% filter(Tiempoinstalado <= 22)
```

**Retiramos observaciones con dato de +400 en Canticaracteres**

```{r}
VDC1 <- VDC1 %>% filter(Canticaracteres <= 50)
```

```{r}
#str(VDC1)
```

```{r}
#summary(VDC1)
```

### **Exportar la base de datos utilizando "write_csv()"**

Luego de haber aplicado los filtros exportamos una nueva base de datos
limpia

```{r}
write_csv(VDC1, "Baselimpia.csv")
```

# **ANÁLISIS DESCRIPTIVO**

```{r}
VDCnew <-read_csv("~/Documents/GENERALES UTEC/ESTADÍSTICA/PROYECTO ESTADISTICA/Baselimpia.csv")
VDCnew
```

Recordemos que: - `Generación centenial: 12-27 años` -
`Generación milenial: 28-41 años` - `Generación x: 42-53`

## **Medidas de tendencia central Y gráficos**

Hallaremos la media, mediana, varianza y dsviación estándar.

donde: - mean: mediana - median: media - var: varianza - sd: desviación
estándar

para el caso de la moda usaremos los comandos: count y arrange

sabiendo ello obtendremos lo siguiente...

### **Edad:**

```{r}
VDCnew$Edad
```

```{r}
max(VDCnew$Edad)
```

```{r}
r(mean(VDCnew$Edad, na.rm = T)) #media 
r(median(VDCnew$Edad, na.rm = T)) #mediana 
r(var(VDCnew$Edad, na.rm = T)) #varianza
r(sd(VDCnew$Edad, na.rm = T)) #desviación estándar
```

```{r}
sd(VDCnew$Edad)/ mean(VDCnew$Edad)
```

El coeficiente de variación es: 0.41 -\> 41%

```{r}
VDCnew %>% count(Edad) %>% arrange(desc(n)) %>% slice(1)
```

Como resultado nos dió que...

-   `moda es: 19`
-   `numero de veces que se repite el número: 28`

```{r}
table(VDCnew$Edad)
```

### **Género**

```{r}
table(VDCnew$Genero)
```

### **Redes sociales:**

```{r}
max(VDCnew$RedesSociales, na.rm = T)
```

```{r}
r(mean(VDCnew$RedesSociales, na.rm = T))
r(median(VDCnew$RedesSociales, na.rm = T))
r(var(VDCnew$RedesSociales, na.rm = T))
r(sd(VDCnew$RedesSociales, na.rm = T))
```

```{r}
VDCnew %>% count(RedesSociales) %>% arrange(desc(n)) %>% slice(1)
```

Como resultado nos dió que...

-   `moda es: 4`
-   `numero de veces que se repite el número: 63`

**gráfico de dispersión Redes sociales vs Edad**

Mediante este gráfico de dispersión observamos una mayor concentración
en el rango de edad entre 18 a 23 aproximadamente. Sin embargo, a partir
del rango de edad de 23 años en adelante observamos una menor
concentración, es decir que los valores individuales están más separados
o extendidos entre sí, lo que implica una mayor variabilidad o
heterogeneidad en los datos.

```{r}
plot(VDCnew$RedesSociales ~ VDCnew$Edad, xlim = c(10, 60), xlab = "Edad", ylab = "Redes Sociales", main="GRÁFICO Nr2º:CANTIDAD DE REDES SOCIALES DE SEGÚN LA EDAD")
```

Con este gráfico podemos deducir que, aparentemente, existe una
correlación inversamente proporcional baja entre las variables Redes
sociales(Y) y Edad(X), ya que a medida que va aumentando la edad va
disminuyendo la cantidad de redes sociales que utiliza.

Usaremos el coeficiente correlación para determinar la proporcionalidad
entre estas dos variables.

```{r}
cor(VDCnew$Edad,VDCnew$RedesSociales)
```

Un coeficiente de correlación de -0.2023768 indica una correlación
negativa en la que los valores de una variable tienden a incrementarse
mientras que los valores de la otra variable descienden.

Asimismo, podemos decir que los valores 1 y -1 representan una
correlación "perfecta" positiva y negativa, respectivamente.

### **Tiempo que lleva instala la aplicación:**

```{r}
r(mean(VDCnew$Tiempoinstalado, na.rm = T))
r(median(VDCnew$Tiempoinstalado, na.rm = T))
r(var(VDCnew$Tiempoinstalado, na.rm = T))
r(sd(VDCnew$Tiempoinstalado, na.rm = T))
```

hallaremos la moda de la variable tiempo ....

```{r}
VDCnew %>% count(Tiempoinstalado) %>% arrange(desc(n)) %>% slice(1)
```

Como resultado nos dió que...

-   `moda es: 10`
-   `numero de veces que se repite el número: 52`

Mediante este comando "table" nos dara un tabla una tabla de frecuencia,
la cual nos dará cuantas se han repetido ciertos valores.

**Gráfico de barras sobre la variable tiempo que lleva instalado una red
social**

```{r}
barplot(table(VDCnew$Tiempoinstalado), main = "GRÁFICO Nr3º:TIEMPO QUE LLEVA INSTALADO REDES SOCIALES", xlab= "tiempo instalado redes sociales(Años)", ylab = "frecuencia", col = "orange")
```

**Gráfico de cajas y bigotes: tiempo que lleva instalado una red social
según su generación**

Como observamos a continuación, la generación que utiliza más redes
sociales es la generacion Centenial a comparación de las otras
generaciones. Esto nos refleja que la generación centenial esta más
expuesta desde temprana edad a los riesgos que involucran las redes
sociales, ya que la generación centenial lleva más años instalado redes
sociales.

```{r}
boxplot(VDCnew$Tiempoinstalado ~ VDCnew$Generacion, horizontal = T, main = "GRÁFICO Nr4º:TIEMPO DE INSTALACIÓN SEGUN SU GENERACIÓN", varwidth = T, xlab = "Tiempo de instalación de redes sociales(años)", ylab = "Generación", col=c("orange"))
```

A continuación, presentamos un gráfico Boxplot indexado asimétrico con
las variables Tiempo y Generación. Asimismo, obervamos que la mediana de
la generación X y milenial coinciden.

Mediante esta gráfica interpretamos que las personas de la generación
centenial tienden a tener instalado sus redes sociales hace 8 años. Sin
embargo, en el caso de la generación Milenial y X, la mediana nos
muestra que tienden a tener instaldo redes desde hace 10 años.

### **Seguidores:**

```{r}
r(mean(VDCnew$Seguidores, na.rm = T))
r(median(VDCnew$Seguidores, na.rm = T))
r(var(VDCnew$Seguidores, na.rm = T))
r(sd(VDCnew$Seguidores, na.rm = T))
```

Para el caso de cantidad de seguidores observamos que tanto la
desviación estándar nos salió 62839.88 como varianza 3948851030. Ello
nos lleva a connotar que los valores dentro de la variable Seguidores se
encuentran muy dispersos con respecto a la media. Cuanto mayor sea el
valor de la desviación estándar, mayor será la dispersión de los
datos.Asimismo, al ser la varianza de 3948851030 implica que los valores
individuales en tu conjunto de datos están muy alejados de la media, lo
que indica una gran variabilidad. Esto significa que los valores tienden
a ser muy diferentes entre sí y no se agrupan cerca de la media.

Esta alta dispersion de los datos se puede reflejar mediante el
siguiente codigo...

hallaremos la moda de la variable seguidores....

```{r}
VDCnew %>% count(Seguidores) %>% arrange(desc(n))
```

Como resultado nos dió que...

-   `moda es: 300`
-   `numero de veces que se repite el número: 22`

A continuación observamos una tabla de frecuencia de la variable
seguidores , con la finalidad de saber cual ha sido la frecuencia de
cada valor.

Si bien la mayoría de valores oscilan entre los 100 a 1500 seguidores,
sin embargo dentro de nuestra data hemos encontrado valores como
"5632","10000","65156","100000".

```{r}
VDCnew %>% count(Seguidores) %>% arrange(-Seguidores)
```

```{r}
table(VDCnew$Seguidores)
```

```{r}
barplot(table(VDCnew$Seguidores),
main = "Frecuencia de seguidores",
xlab = "Cantidad de seguidores",
ylab = "Frecuencia", 
col = c("#DE6950")) 
```

```{r}
plot(VDCnew$Seguidores~VDCnew$Edad, xlab = "Edad(años)", ylab = "Seguidores", main = "GRÁFICO Nr5º:CANTIDAD DE SEGUIDORES SEGÚN LA EDAD")
```

```{r}
cor(VDCnew$Edad,VDCnew$Seguidores)
```

Un coeficiente de correlación de 0.1852957 indica una correlación
positiva débil entre las variables que estás analizando.En este caso, un
valor de 0.1852957 sugiere que hay una tendencia positiva, pero muy
débil, entre las variables. Esto significa que a medida que los valores
de una variable aumentan, los valores de la otra variable también
tienden a aumentar, pero la relación no es muy fuerte. En general, un
coeficiente de correlación cercano a cero indica una correlación débil o
prácticamente inexistente.

**Eliminamos usuarios que tengan una cantidad de seguidores mayor a
5000, ya que nos representa una dispersión muy amplia en nuestra data**

```{r}
VDCnew <- VDCnew %>% filter(Seguidores >= 1 & Seguidores <=5000)
```

```{r}
VDCnew %>% count(Seguidores) %>% arrange(-Seguidores)
```

**Cantidad de Seguidores luego de haberle aplicado filtros**

```{r}
r(mean(VDCnew$Seguidores, na.rm = T))
r(median(VDCnew$Seguidores, na.rm = T))
r(var(VDCnew$Seguidores, na.rm = T))
r(sd(VDCnew$Seguidores, na.rm = T))
```

```{r}
plot(VDCnew$Seguidores~VDCnew$Edad, xlab = "Edad(años)", ylab = "Seguidores", main = "GRÁFICO Nr6º:Relación entre la cantidad de Seguidores y la edad", col = "red")
```

```{r}
cor(VDCnew$Edad,VDCnew$Seguidores)
```

Observamos una mayor concentración de seguidores entre el rango de edad
de 17 a 23 años aproximadamente. Sin embargo, a partir del rango de edad
mayor a 23 años hay una mayor dispersión. Asimismo, observamos que la
cantida de seguidores promedio es 200.

En cuanto al comportamiento de la gráfica. Sin embargo, no pasa lo mismo
con el rango de edad de 27 años en adelante, ya que los datos se
encuentran más dispersos.

**Diagrama de cajas y bigotes entre la variable cantidad de seguidores y
la generación**

```{r}
boxplot(VDCnew$Seguidores ~ VDCnew$Generacion, horizontal = T,  main = "Relación entre de seguidores  de acuerdo a su Genereción", varwidth = T, xlab = "Seguidores", ylab = "Generación", col= c("purple"))
```

En la presente gráfica observamos datos atípicos en los maximos de las
tres generaciones. Por otra parte, en cuanto a la mediana de cada
generación, tanto la generación centenial, como X coinciden en la
mediana. Si bien los centenial tienen una mayor cantidad de datos
acomparación de las demas generaciones, sin embargo, los milenials en
promedio tienen una mayor cantidad de seguirdores siendo 753.97.

```{r}
#Generación centenial: 12-27 años 
#Generación milenial: 28-41 años
#Generación x: 42-53

#muestra la cantidad de datos de cada generación: 
table(VDCnew$Generacion)
generaciones = data.frame(VDCnew$Generacion, VDCnew$Seguidores)
```

```{r}
#Promedio - Milenial
milenial = generaciones$VDCnew.Seguidores[generaciones$VDCnew.Generacion == "Milenial"]
sum(milenial/34)

#Promedio - GX
gx = generaciones$VDCnew.Seguidores[generaciones$VDCnew.Generacion == "GX"]
sum(gx/35)

#Promedio - Centenial
centenial = generaciones$VDCnew.Seguidores[generaciones$VDCnew.Generacion == "Centenial"]
sum(centenial/180)

#milenial = (VDCnew$Generacion, )
#milenial = VDCnew$Generacion[VDCnew$Generacion == "Milenial"]
#sum(milenial)
```

### **Tiempo de uso:**

hallaremos la moda de la variable tiempo de uso o momento del día en que
utilizas más redes sociales....

```{r}
VDCnew %>% count(Tiempodeuso) %>% arrange(desc(n))
```

Como resultado nos dió que...

-   `moda es:  en la noche`
-   `numero de veces que se repite el número: 179`

```{r}
table(VDCnew$Tiempodeuso)
```

Como observamos, los usuarios usan durante mayor cantidad de tiempo
redes sociales en la noche, en lugar de en el tarde o en la mañana. Esto
se debe a que durante la tarde o la mañana pueden estar ocupados en el
trabajo o en el colegio o en la universidad. Y en la noche a modo de
relajación o descanso pueden pasar mas tiempo en redes sociales.

```{r}
boxplot(VDCnew$Edad ~ VDCnew$Tiempodeuso, horizontal = F,  main = "GRÁFICO Nr7º: Cantidad de tiempo de uso de acuerdo a su edad", varwidth = T, xlab = "Tiempo de uso", ylab = "Edad ", col = c("yellow"))
```

Observamos que este gráfico presenta valores atípicos o puntos en el
extremo derecho. Con relación al tiempo de uso "en la mañana", no
presenta una dispersión significativamente grande. Sin embargo, en el
caso de "en la noche", la gráfica presenta whiskers o bigotes más
largos, lo cual indica que los datos se extienden más lejos de la
mediana y del rango intercuartílico. Esto sugiere una mayor variabilidad
y dispersión de los datos en este grupo. Asimismo, observamos que tanto
la mediana de "en la mañana" y "en la noche" coinciden.

La gráfica nos permite interpetar que dentro de la variable "en la
noche" el 25% de datos por encima de la mediana presente una mayor
concentración y se encuentra entre las personas de 20 a 30 años.

### **Cantidad de caracteres de la contraseña:**

```{r}
r(mean(VDCnew$Canticaracteres, na.rm = T))
r(median(VDCnew$Canticaracteres, na.rm = T))
r(var(VDCnew$Canticaracteres, na.rm = T))
r(sd(VDCnew$Canticaracteres, na.rm = T))
```

hallaremos la moda de la variable canticaracteres....

```{r}
VDCnew%>% count(Canticaracteres) %>% arrange(desc(n))%>% arrange(desc(-Canticaracteres))
```

Como resultado nos dió que...

-   `moda es: 8`
-   `numero de veces que se repite el número: 62`
-   `Cantidad de caracteres de la contraseña VS Nivel de seguridad`

```{r}
table(VDCnew$Canticaracteres,VDCnew$Nseguridad)
```

```{r}
barplot(table(VDCnew$Canticaracteres),
main = "GRÁFICO Nr8º:Cantidad de caracteres de las contraseñas",
xlab = "Cantidad de caracteres", 
ylab = "Frecuencia", 
col = c("skyblue")) 
```

**Gráfico de dispersión: Relación entre la variable edad y cantidad de
caracteres**

```{r}
plot(VDCnew$Canticaracteres~VDCnew$Edad, xlab = "Edad", ylab = "Canticaracteres", main = "GRÁFICO Nr9º:Relación entre la variable edad y cantidad de caracteres")
```

El presente gráfico nos muestra como las personas dentro del rango de
edad de 17 a 27(generación centenial) aproximademente hay una menor
dispersión a diferencia de las otras edades. Esto se puede deber a dos
razones. En primer lugar,esto podría deberse a que el grupo de personas
entre los 17 - 25 esta mayor informada acerca de los cuidados para la
seguridad de su cuenta de red social. Por otra parte , puede deberse a
que las personas de la mayores a 17 , es decir generación milenial y x
prefieren no tener muchas cantidad de caracteres en sus contraseñas de
cuentas de redes sociales, ya que les es mas dificil recordarlas o
prefieren no hacerlo, por ende recurren a una contraseña corta y que
tenga relación con un dato o fecha importante.

```{r}
boxplot(VDCnew$Canticaracteres~ VDCnew$Genero, horizontal = T, main = "GRÁFICO Nr10º:Cantidad de caracteres segun su género",col=c("pink","blue"), varwidth = T, xlab = "Cantidad de caracteres", ylab = "Género")
```

El género con mayor cantidad de caracteres en sus contraseñas de redes
sociales es el masculino en comparación al género femenino.

### **Nivel de seguridad:**

```{r}
r(mean(VDCnew$Nseguridad,na.rm = T))
r(median(VDCnew$Nseguridad,na.rm = T))
r(var(VDCnew$Nseguridad,na.rm = T)) 
r(sd(VDCnew$Nseguridad,na.rm = T))
```

hallaremos la moda de la variable canticaracteres....

```{r}
VDCnew%>% count(Nseguridad) %>% arrange(desc(n))
```

Como resultado nos dió que...

-   `moda es: 4`
-   `numero de veces que se repite el número: 101`

```{r}
barplot(table(VDCnew$Nseguridad),
main = "GRÁFICO Nr11º:Frecuencia del nivel de seguridad",
xlab = "nivel de seguridad", 
ylab = "Frecuencia", 
col = c("pink")) 
```

El presente gráfico nos muestra que la mayoría de usuarios consideran
que tienen un nivel de seguridad alto.

```{r}
variables_interes <- VDCnew%>%select(`Nseguridad`, `Generacion`)

frecuencias <- variables_interes %>%count(`Nseguridad`, `Generacion`)

ggplot(frecuencias, aes(x = `Generacion`,
                       y = `Nseguridad`,
                       fill = n)) +
  geom_tile() +
  scale_fill_gradient(low = "blue", high = "red") +
  theme_minimal() +
  labs(title = "GRÁFICO Nr12º:Mapa de calor",
       x = "Generación",
       y = "Nivel de seguridad")

```

Esto nos permite analizar el nivel de seguridad que los usuarios
consideran que presentan al crear sus contraseñas de redes sociales.
Asimismo se observa que en el mapa de calor que la generacion centenial
es la que tiene mayor nivel de seguridad a comparación de las otras
generaciones, despues le sigue la generacion milenial y por lo ultimo la
generacion x.

Es importante tener en cuenta que las generalizaciones sobre una
generación completa pueden ser simplificaciones excesivas, ya que cada
individuo es único y sus características pueden variar ampliamente. Sin
embargo, se han observado algunas tendencias generales en relación con
la seguridad de las cuentas entre las generaciones.

Factores que podrían influir en la mayor preocupación por la seguridad
de las cuentas en la generación centenial en comparación con la
generación millenial y X:

-   Crecimiento en la era digital

-   Acceso a mejores recursos y programas de concienciación sobre
    seguridad en línea desde temprana edad.

-   Mayor dependencia de las redes sociales

**Gráfico de dispersión: Relación entre la variable nivel de seguridad
según la cantidad de caracteres**

```{r}
plot(VDCnew$Nseguridad~VDCnew$Canticaracteres, xlab = "Canticaracteres", ylab = "Nivel de seguridad", main = "GRÁFICO Nr13º:Relación entre la variable nivel de seguridad vs la canticaracteres ")
```

Este gráfico nos lleva a reflexinar que si bien la seguridad para
nuestro grupo de encuestados es importante, sin embargo la mayoría de
personas opta por una cantidad de caracteres entre 8 a 12 caracteres
aproximadamente, ya que al tener más caracteres si bien su contraseña
será más segura, sin embargo, será más dificil recordarla y por ende la
olvidará y tendrá que crear una nueva contraseña constantemente.

### **Uso de la misma contraseña para todas sus redes sociales:**

hallaremos la moda de la variable Usodecontraseña....

```{r}
VDCnew%>% count(Usodecontraseña) %>% arrange(desc(n))
```

### **Cantidad de tiempo con la que cambian su contraseña:**

```{r}
r(mean(VDCnew$Tcambiocontraseña,na.rm = T))
r(median(VDCnew$Tcambiocontraseña,na.rm = T))
r(var(VDCnew$Tcambiocontraseña,na.rm = T)) 
r(sd(VDCnew$Tcambiocontraseña,na.rm = T))
```

En esta ocación la media nos salió 485.13, lo cual es un valor alto.
Ello nos indica que los valores individuales tienden a ser mayores que
el promedio.Esto significa que los valores individuales están inclinados
hacia el extremo superior del rango de datos.

```{r}
sqrt(39334097)
```

hallaremos la moda de la variable Tcambiocontraseña....

```{r}
VDCnew%>% count(Tcambiocontraseña) %>% arrange(desc(n))
```

Como resultado nos dió que...

-   `moda es: 30`
-   `numero de veces que se repite el número: 43`

```{r}
barplot(table(VDCnew$Tcambiocontraseña),
main = "GRÁFICO Nr14º: Frecuencia con la que cambia la contraseña",
xlab = "Tiempo (días) que cambias la contraseña", 
ylab = "Frecuencia", 
col = c("green")) 
```

Esta gráfica nos lleva a connotar que hay un cierto grupo de personas
que prefieren no combiar nunca su contraseña de sus cuentas de redes
sociales. Asimismo,observamos que la mayoría de usuarios cambian su
contraseña cada 30 días o cada mes.

*Hallamos su máximo*

```{r}
max(VDCnew$Tcambiocontraseña)
```

Dado que el máximo de la variable Tiempo de cambio de contraseña es
2000, por ende le aplicamos un filter ya que va afectar nuestro
análisis.

**Eliminamos usuarios que tengan una cantidad de seguidores mayor a
5000, ya que nos representa una dispersión muy amplia en nuestra data**

```{r}
VDCnew <- VDCnew %>% filter(Tcambiocontraseña >= 0 & Tcambiocontraseña <=2000)
```

Luego de haber aplicado el filtro sacamos los siguientes resultados....

```{r}
r(mean(VDCnew$Tcambiocontraseña,na.rm = T))
r(median(VDCnew$Tcambiocontraseña,na.rm = T))
r(var(VDCnew$Tcambiocontraseña,na.rm = T)) 
r(sd(VDCnew$Tcambiocontraseña,na.rm = T))
```

Si bien no ha habido un cambio significativo en cuanto a la varianza ,
sin embargo en el caso de la media o promedio pasó de 485.13 a 93.09, lo
cual representa un cambio significativo. Asimismo, en cuanto a la
desviación estándar pasó de 6271.69 a 192.04, lo cual indica una menor
dispersión entre los datos.

```{r}
sqrt(36878.18)
```

### **Cuenta hackeada:**

hallaremos la moda de la variable Cuenta hackeada....

```{r}
VDCnew%>% count(Cuentahackeada) %>% arrange(desc(n))
```

Como resultado nos dió que...

-   `moda es: no`
-   `numero de veces que se repite el número: 202`

```{r}
Hackeos<-table(VDCnew$Cuentahackeada)
barp<-barplot( Hackeos,main="Gráfico Nrº15:Hackeo de contraseñas de cuentas",col=c("skyblue","red"),xlab = "hackeo o no Hackeo a usuarios", ylab = "Cantidad de usuarios",ylim=c(0,249) )
text(barp, Hackeos + 0.5, labels = Hackeos)
```

Observamos que 202 personas no han sido hackeadas, mientras que 47
personas si han sido hackeadas.

Dentro de los principales factores que influyen para que una cuenta de
red social sea hackeada o no, son los siguientes:

-   El uso de contraseñas débiles o predecibles es uno de los
    principales factores que facilitan el hackeo de una cuenta.
-   Utilizar la misma contraseña en múltiples cuentas aumenta el riesgo
    a ser hackeado.

Ello nos lleva a pensar que las 47 personas que han sido hackeadas
presentaban algunos de estos dos factores mencionados.

### **Número de notificaciones:**

```{r}
r(mean(VDCnew$Numnotificaciones,na.rm = T))
r(median(VDCnew$Numnotificaciones,na.rm = T))
r(var(VDCnew$Numnotificaciones,na.rm = T)) 
r(sd(VDCnew$Numnotificaciones,na.rm = T))
```

hallaremos la moda de la variable Numnotificanes....

```{r}
VDCnew%>% count(Numnotificaciones) %>% arrange(desc(n))
```

Como resultado nos dió que...

-   `moda es: 10`
-   `numero de veces que se repite el número: 48`

**observamos el comportamiento de la variable número de notificaciones**

```{r}
VDCnew %>% count(Numnotificaciones) %>% arrange(-Numnotificaciones)
```

```{r}
hist(VDCnew$Numnotificaciones, xlim = c(0, 30), breaks = 300, main= "GRÁFICO Nr16º:Histograma sobre el número de notificaciones",xlab = "Número de notificaciones", ylab = "Frecuencia", col= "blue")
```

Estos nos lleva a inferir que al estar más pendientes de sus
notificaciones, por ende pueden reaccionar más rápido al momento de ser
hackeados, ya que si por a o b motivos hackearan tu cuenta o se presenta
alguna anomalía extraña en alguna de tus cuentas de redes sociales en su
mayoría google te manda un mensaje avisandote o advirtiendote ello.

Con en su mayoría de veces, me refiero a que, el principal objetivo del
hacker es evitar que google y la persona que es hackeada se den cuenta
de ello, por ende va intentar hackearte sin ser registrado.
