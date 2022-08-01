# Práctica de Custom Vision de Azure
![CVlogo](/images/Custom-Vision.png)

Esta práctica consiste en crear un modelo de visión computacional para reconocer imágenes y/o videos.
Se entrenará este modelo con un conjunto de imágenes que se encuentran en una carpeta. Se usará el servicio de [Custom Vision de Azure](https://azure.microsoft.com/es-mx/services/cognitive-services/custom-vision-service/) para entrenar el modelo.

# Requisitos
- Ingresar al sitio de [Custom Vision de Azure](https://www.customvision.ai/) con la cuenta de Azure que se creó en el paso anterior del índice principal.
- Descargar de 30 a 100 imágenes (entre mayor sea la cantidad, más preciso se podrá hacer el reconocimiento) de alguna temática, por ejemplo: ***El universo*** (galaxias, nebulosas, planetas y **otros**). De preferencia, guardarlas en una carpeta individual el tipo de imagen que se guarde, por ejemplo: `galaxias`, `nebulosas`, `planetas` y `otros`.


# Instrucciones
1. Ingresar con una cuenta de Azure al sitio de Custom Vision de Azure.

2. Se crea un **New Project**.
    | Parámetro | Valor |
    | --- | --- |
    | Nombre del proyecto | Colorar el nombre que del proyecto nuevo. Ejemplo: **detect-mas** |
    | Suscripción | La suscripción activa de la cuenta de Azure. |
    | Grupo de recursos | El grupo de recursos que se le asignará este nuevo servicio tipo Cognitive Services. Si no se cuenta con alguno, se puede crear ahí mismo. |
    | Tipo | Cognitive Services |
    | Ubicación | Seleccionar la ubicación del recurso. |
    | Nivel de precio | Si es primera vez que se crea un proyecto, seleccionar el nivel **F0** (es el nivel gratuito); de no ser así, entonces se selecciona **S0**.|
    
    - Se acepta la creación del proyecto.
    ![CVRecurso](/PracticaCV/CVimages/CVRecurso.gif)


3. Después de realizar los primeros parámetros del proyecto, se actualizará la ventana donde se seleccionará el recurso (que se acabó de crear).
    | Parámetro | Valor |
    | --- | --- |
    | Tipo de proyecto | En esta ocasión es **Clasificación**. |
    | Tipos de clasificación | **Multiclase (Multiclass)** es cuando se subirán varias imágenes de diferentes tipos; o **Multietiqueta (Multilabel)** que srive para encontrar objetos dentro de imágenes. Se selecciona **Multiclase** por ésta vez. |
    | Dominio[*](#) | Se refiere l tipo de imágenes que serán procesadas para el reconocimiento de acuerdo con . En este caso, se selecciona **General(A2)**. |

    - Se presionará el botón de **Crear proyecto**.
    ![CVNewProject](/PracticaCV/CVimages/CVNewProject.gif)

4. Una vez creado, se añadirán las imagenes que se hayan descargado (que se mencionan en los [requisitos](#requisitos)). De acuerdo con las imagenes que se fueron guardando en varias carpetas vayan subiendo, se tendrá que colocar una etiqueta o *tag* para poder clasificarlas. Por ejemplo, si se suben imágenes de galaxias, se tendrá que colocar una etiqueta de **galaxias**.	
    - Esto se repetirá para cada conjunto de imágenes que se suban (a excpeción de las imagenes que se guardaron en la carpeta *otros*).
![CVupload](/PracticaCV/CVimages/CVupload.gif)
    
5. Tenemos un proyecto casi completo (75%), esto es porque necesitamos darle a el modelo imágenes *que no sean **referentes** a akguna de las imágenes que se colocaron* Ejemplo: estrellas. Es por ello que se necesitaba de la carpeta *otros*.
    - Al subir las imagenes, se tendrá que seleccionar la etiquta **negativo**.
    ![CVuploadneg](/PracticaCV/CVimages/CVuploadneg.gif)

6. Una vez que se hayan subido todas las imagenes, se tendrá que presionar el botón de **Entrenar modelo** o **Train**. Es decir, ***Custom vision*** estará **"estudiando"** las imagenes que se subieron para que, cuando se suba una nueva imagen, pueda ser reconocida.
    - Se elecciona la opción de **Entrenamiento rapido** y se espera a que se termine.
    ![CVtrain](/PracticaCV/CVimages/CVtrain.gif)

***Este proceso tarda varios minutos para estar listo***.

7. Se muestran estadísticas de los resultados del entrenamiento.
    | Estadística | Descripción |
    | --- | --- |
    | Precisión | La precisión del modelo al ser entrenado. |
    | Recuento (Recall) | El recuento del modelo al ser entrenado. | De la cantidad de pruebas realizadas, se obtiene un resultado correcto. |
    | AP | Resume la precisón con el recuento de las imágenes que se subieron. | 

    - Se selecciona **Prueba rápida** (Quick Test) y se sube une imagen para para observar los resultados del entrenamiento.
        - [**Test 1**](https://services.meteored.com/img/article/ultima-semana-de-abril-la-lluvia-de-estrellas-liridas-llegan-1649863489714_1024.jpg) ![Test 1](https://services.meteored.com/img/article/ultima-semana-de-abril-la-lluvia-de-estrellas-liridas-llegan-1649863489714_1024.jpg)

        - [**Test 2**](https://curiosfera-ciencia.com/wp-content/uploads/2020/09/estrellas-caracteristicas.jpg) ![Test 2](https://curiosfera-ciencia.com/wp-content/uploads/2020/09/estrellas-caracteristicas.jpg)
    
    ![CVtest](/PracticaCV/CVimages/CVtest.gif)

    - Se observan diferentes resultados que van de acuerdo con el entrenamiento.



#### Ahora se cuenta con una forma de *predecir* y/o clasificar imagenes con ayuda de Azure Cognitive Services Custom Vision.


---- 
# **⚠Importante⚠** 
### Recordar que, si no se requiere más del servicio, se puede eliminar pulsando el botón **Detener** después de haber seleccionado la *instancia de proceso* que, se encuentra en **Proceso** del panel izquierdo.
O bien, eliminar el grupo de recursos dentro del [Portal de Azure](https://portal.azure.com/) si no se requiere todo el contenido de dicho grupo.

###### <sub>[Volver al índice principal de prácticas](/README.md)<sub>

## Hasta aquí la finalización de la práctica.


-----


###### *
| Dominio | Descripción |
| --- | --- |
|General (A2) | Modelo de predicción general más reciente en su segunda generación. |
General (A1) | Modelo de predicción general más reciente en su primera generación. |
| General | Modelo de predicción simple |
| Comida (Food) | Modelo de predicción para comida o elementos comestibles. |
| Puntos de Referencia (landmarks) | Modelo de predicción para puntos de referencia como monumentos, estatuas, etc. |
| Ventas de productos (Retail) | Modelo de predicción para ventas de productos. |
| Compactos | MOdelo que descarga las imágenes para procesar en una aplicación móvil y optimizar memoria. |

<sup>[Fuente](https://docs.microsoft.com/es-mx/azure/cognitive-services/custom-vision-service/select-domain#image-classification)<sub>

