# Práctica de Machine Learning Automatizado
![MLlogo](/images/Machine-Learning.png)


----
# Requisitos
 - Ingresar al sitio de [Azure Machine Learning Studio](https://ml.azure.com/home) con la cuenta de Azure que se creó en el paso anterior del índice principal.
 - Usar el siguiente Dataset: https://aka.ms/bike-rentals. **No se debe descargar**.


# Instrucciones
###### 1

1. Se creará un área de trabajo:
    | Parámetro | Valor |
    | --- | --- |
    | Nombre | Nombre del área de trabajo. No debe llevar espacios. Ejemplo: my-ML-workspace|
    | Suscripción | Suscripción de Azure que se creó en el paso anterior|
    | Grupo de recursos | Seleccionar el grupo de recursos en el que se encontrará el área de trabajo. Si no se cuenta con alguna, se puede crear ahí mismo.  |
    | Región | Seleccionar la región en la que se encontrará el área de trabajo.|

    ![MLWorkspace](/PracticaMLAuto/MLAimages/MLWorkspace.gif)
    
    - Esperar a que se cree después de haber presionado el botón **Crear**.


2. Accediendo al ***Área de trabajo***, nos despliega un panel izquierdo con diferentes **Recursos** para crear y administrar. 
    - Por ejemplo, en **Almacenes de datos** podemos crear un almacén de datos, un almacén de modelos y un almacén de experimentos. Igualmente se puede importar desde un *Blob Storage*. Esto es fundamental para *nutrir* a la Inteligencia Artificial.

3. Se creará una nueva **Instancia de Proceso** (máquina virtual para ejecutar el proceso de predicción). Esto se encuentra en ***Proceso*** del panel izquierdo.
    | Parámetro | Valor |
    | --- | --- |
    | Nombre del proceso | Nombre de la instancia de proceso. Ejemplo: noesvirtualmachine|
    | Tipo de máquina virtual | Existen dos tipos: **CPU** y **GPU**. GPU es más rápido que CPU, pero su costo es más alto. Se uesrá por esta vez *CPU*.|
    | Tamaño| Seleccionar el tamaño de la máquina virtual que esté disponible.|

    **Importante: la región se mantendrá para todos los recursos subsecuentes en esta práctica.**

    ![MLProceso](/PracticaMLAuto/MLAimages/MLProceso.gif)
    
    - Esperar a que se cree después de haber presionado el botón **Crear**.


4. Se creará un nuevo **Clúster de proceso** (mini máquinas virtuales para realizar Machine Learning). Esto se encuentra en ***Proceso*** del panel izquierdo.
    | Parámetro | Valor |
    | --- | --- |
    | Nivel de máquina virtual | Seleccionar **Dedicado**.|
    | Tipo de máquina virtual | Seleccionar **CPU**.|
    | Tamaño| Seleccionar el tamaño de la máquina virtual que esté disponible.|

    - Pulsar el botón **Siguiente** para proceder a *Configurar avanzada* el clúster.
        | Parámetro | Valor |
        | --- | --- |
        | Nombre del proceso | Nombre del clúster. Ejemplo: mycluster.|
        | Número de nodos máximo| Seleccionar el número de nodos máximo de acuerdo con los *Núcelos de la máquina virtual*.|
    
    - Pulsar el botón **Crear**.
    ![MLCluster](/PracticaMLAuto/MLAimages/MLCluster.gif)


5. En esta práctica, se importarán los datos de un archivo web ([Dataset](#requisitos)) de **ventas de bicicletas**. Se irá al apartado **Datos** del panel izquierdo y después seleccionar **Crear** ➡ **De archivos web**.
    - Información básica:
        | Parámetro | Valor |
        | --- | --- |
        | Dirección URL | Dirección URL del archivo web a trabajar|
        | Nombre | Nombre del archivo. Ejemplo: bike-rentals|
        | Descripción | Descripción del archivo. Ejemplo: Dataset de ventas de bicicletas|

    - Pulsar el botón **Siguiente** para avanzar a *Configuración y vista previa*:
        | Parámetro | Valor |
        | --- | --- |
        | Formato | Seleccionar el formato **Delimitado**.|
        | Delimitador | Seleccionar el delimitador **Coma**.|
        | Codificación | Seleccionar la codificación **UTF-8**.|
        | Encabezado | Seleccionar **Sólo el primer archivo**.|
        | Omisión de filas | Seleccionar **No omitir filas**.|
    
    - Pulsar el botón **Siguiente** para avanzar a *Esquema*:
        Mantendremos todas las opciones *encendidas*, **excepto** la opción **Path**.
    - Pulsar el botón **Siguiente** y **Confirmar**

    ![MLDataset](/PracticaMLAuto/MLAimages/MLDataset.gif)

6. Se irá a **ML automatizado** del panel izquierdo y seleccionar **Crear** ➡ **ML automatizado**.
    - Se selecciona el recurso de datos que se creó en el paso anterior y pulsar el botón **Siguiente**.
    - En *Configurar trabajo*:
        | Parámetro | Valor |
        | --- | --- |
        | Nombre del experimento | Seleccionar *Crear* y proceder con la asginación de un nombre del experimento nuevo. Ej.: bikePredict. |
        | Columna destino | Son las *estiquetas* que se desean predecir. Ejemplo: rentals.|
        | Seleccionr tipo de proceso| Seleccionar **Clúster de proceso**.|
        | Seleccionar clúster | Seleccionar el clúster que se creó en el paso anterior.|
    
    - Pulsar el botón **Siguiente** para avanzar a *Seleccionar la tarea y la configuración*:
        - Seleccinar la tarea **Regresión**[*](https://docs.microsoft.com/es-mx/azure/machine-learning/algorithm-cheat-sheet#download-machine-learning-algorithm-cheat-sheet) porque se busca predecir las rentas de bicis para cierto evento futuro.

    - Pulsar el botón **Siguiente** para avanzar a *Validar y probar*:
        | Parámetro | Valor |
        | --- | --- |
        Tipo de validación | Seleccionar **Automático**.|
        Recursos de datos de prueba | (Para esta práctica)Seleccionar **No se requieren recursos de datos de prueba**.|
    
    - Se pulsa el botón **Crear**.
    ![MLAutomatizado](/PracticaMLAuto/MLAimages/MLAutomatizado.gif)

***Este proceso tarda varios minutos para estar listo***.

7.  En **Experimento**, (se encuentra en **ML automatizado** del panel izquierdo), se selecciona el experimento que se creó y dentro de la nueva ventana se busca el parámetro **Nombre para mostrar** para que muestre la información del experimento.
    - Se busca el parámetro **Algoritmo** (en la sección *Resumen del mejor modelo*).
    ![MLexperimento](/PracticaMLAuto/MLAimages/MLexperimento.gif) 

8. en **Métricas** se puede observar, ya sea en "Gráfico" o "Tablas", los datos obtenidos del experimento con las predicciones. Se seleccionan todos los campos y se observa en el último gráfico la predicción de las rentas de bicis en contra de la cantidad de veces que se realizó.
![MLmetrica](/PracticaMLAuto/MLAimages/MLmetrica.gif)

9. Se pulsará el botón *Implementar* seguido de *Servicio web*.
    | Parámetro | Valor |
    | --- | --- |
    | Nombre | Nombre del servicio. Ejemplo: bikePredict|
    | Descripción | (Opcional) Descripción del servicio. Ejemplo: Servicio de predicción de rentas de bicis|
    | Tipo de proceso | Puede ser **Azure Kubernetes Service** para un proyecto grande, o **Instancia de conetenedor de Azure** para pruebas (que es justo lo que se realizará).|
    | Habilitar autenticación | Seleccionar **Sí**.|
    
    - Se pulsará el botón **Implentar**.
    ![MLimplementar](/PracticaMLAuto/MLAimages/MLimplementar.gif)

    - Esto generará una API para ser consumida. ***Esto llega a tomar varios minutos***.

10. Para visualizar la API, en el panel izquierdo se selecciona **Puntos de conexión**.
    - Se selecciona el servicio que se creó en el paso anterior y mostrará los detalles de la API. 
    - Se busca la opción **Consumr** y aparecerá la información básica para su consumo en diferentes lenguajes de programación (C#, Python y R).

11. Se pueden hacer pruebas de la API en la opción **Pruebas**.
    - Se edita el código de la API y se añade el código de prueba (se pueden editar los datos numéricos para obtener diferentes pruebas).
        ```
        {
        "Inputs": {
            "data": [
            {
                "day": 9,
                "mnth": 6,
                "year": 2022,
                "season": 1,
                "holiday": 0,
                "weekday": 5,
                "workingday": 1,
                "weathersit": 0,
                "temp": 0.313333,
                "atemp": 0.339004,
                "hum": 0.005833,
                "windspeed": 0.160446
            }
            ]
        },
        "GlobalParameters": 0.0
        }
        ```
    - Se pulsa el botón **Prueba** y se observará un resultado de la canitdad de bicicletas para rentar en el día.
    ![MLprueba](/PracticaMLAuto/MLAimages/MLprueba.gif)

12. Se puede copiar el código de la API en el lenguaje Pyhton para poder ser consumido en otras plataformas que usen Python.

##### Ahora contamos con una manera de crear predicciones en Azure con Machine Learning y consumiendo su API.


---- 
# **⚠Importante⚠** 
### Recordar que, si no se requiere más del servicio de Machine Learning, se puede eliminar pulsando el botón **Detener** después de haber seleccionado la *instancia de proceso* que, se encuentra en **Proceso** del panel izquierdo.
O bien, eliminar el grupo de recursos dentro del [Portal de Azure](https://portal.azure.com/) si no se requiere todo el contenido de dicho grupo.

###### <sub>[Volver al índice principal de prácticas](/README.md)<sub>

## Hasta aquí la finalización de la práctica.