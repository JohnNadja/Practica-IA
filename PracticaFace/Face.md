# Práctica de Cognitive Services con Face
![Facelogo](/images/Face.png)

En esta práctica se utilizaremos el servicio de Azure [Face](https://docs.microsoft.com/es-mx/azure/cognitive-services/face/overview) para reconocer rostros. Es una API que nos permitirá de forma sencilla el proceso de reconocimiento facial. En este caso, será para evaluar la posible edad que tendrá una persona.

----
# Requisitos
 - Ingresar al sitio de [Azure Machine Learning Studio](https://ml.azure.com/home) con la cuenta de Azure que se creó en el paso anterior del índice principal.


----
# Instrucciones
Una vez realizado únicamente el paso [1](/PracticaMLAuto/MLAuto.md#1) de esa práctica (o reutilizar la instancia misma en caso de no haber eliminado ésta), se procederá a realizar lo siguiente.

1. Se creará un nuevo **Notebook**. Esto se encuentra en el panel izquierdo.
    - Pulsamos el ícono de **+** para crear un nuevo archivo tipo *.ipynb*.
        | Parámetro | Valor |
        | --- | --- |
        | **Nombre del archivo** | Colorar el nombre que del archivo nuevo. Ejemplo: **DeteccionEdad.ipynb** |
        | **Tipo de archivo** | **Notebook** (.ipynb) |
    
    - Pulsar el botón de **Crear** notebook.
    ![FaceNotebook](/PracticaFace/Faceimages/FaceNotebook.gif)

2. Dentro del documento, se escribirá el siguiente código:
    ```python
    # Consumo de la FACE API de Azure para obtener información de rostros
    # Para más información, consulta: https://docs.microsoft.com/es-mx/rest/api/face/
    import json, os, requests, pprint
    from IPython.core.display import Image, display


    # Obtener el API KEY de la aplicación
    subscription_key = "AQUÍ_PONES_TU_CLAVE_DEL_RECURSO_DE_AZURE"

    # Obtener el endpoint de la aplicación
    face_api_url = "AQUÍ_PONES_TU_URL_DESTINO_DEL_RECURSO_DE_AZURE" + '/face/v1.0/detect'

    image_url = 'AQUÍ_PONES_TU_IMAGEN'
    # Imagen de prueba: https://raw.githubusercontent.com/Microsoft/Cognitive-Face-Windows/master/Data/detection1.jpg

    # Headers necesarios para que funcione la aplicación
    headers = {'Ocp-Apim-Subscription-Key': subscription_key}

    # Parametros que se utilizan en la llamada de la API
    params = {
        'returnFaceId': 'true',
        'returnFaceAttributes': 'age,gender,headPose,smile,facialHair,glasses,emotion'
    }

    # Aquí se hace la petición al servicio de FACE API de Azure
    response = requests.post(
        face_api_url, params=params,
        headers=headers, json={"url": image_url}
    )

    # Muestras la imagen 
    display(Image(url = image_url, width = 500, unconfined = True))

    # Aquí obtienes tu edad
    print("Edad " + str(response.json()[0]['faceAttributes']['age']))
    # Aquí obtienes tu genero
    print("Genero " + str(response.json()[0]['faceAttributes']['gender']))
    # Aquí obtienes si usas lentes o no
    print("¿Lentes?: " + str(response.json()[0]['faceAttributes']['glasses']))

    # Aquí oobtienes el listado de emociones
    emociones = response.json()[0]['faceAttributes']['emotion']

    # Aquí obtenemos la emoción predominante de acuerdo a la probabilidad que nos arroja FACE API
    listaEmociones = []
    for e in emociones.keys() :
        listaEmociones.append(e)

    listaProbabilidades = []
    for e in emociones.values() :
        listaProbabilidades.append(e)
    m = max(listaProbabilidades)
    indexMax = [i for i, j in enumerate(listaProbabilidades) if j == m]

    # Imprimimos la emoción predominante
    print("Emoción predominante: " + str(listaEmociones[indexMax[0]]))
    ```	

    ![FaceCode](/PracticaFace/Faceimages/FaceCode.gif)
    - Éste código tomará una imagen (de una persona) de una URL y obtendrá la edad, genero, si usa lentes o no, y la emoción predominante.

3. Se obtendrá la URL de una imagen de una persona. Por ejemplo:
    - https://daman.co.id/10-male-models-you-should-follow-on-instagram/
    ![InstagramPhoto](https://daman.co.id/10-male-models-you-should-follow-on-instagram/)

    - En el código, se debe cambiar la URL de la imagen por la URL de la imagen que se desea obtener. Para ser esepcíficos, debe de ser en `image_url = 'URL_IMAGEN'` (incluyendo las comillas).
    ![InstaPhoto](/PracticaFace/Faceimages/InstaPhoto.png)

4. Sin embargo, no se puede aún ejecutar ya que se requiere ***una llave y punto de conexión*** del servicio de ***FACE API*** de Azure. Para ello, se debe acceder al [Portal de Azure](https://portal.azure.com/), y seguir las siguientes instrucciones:
    - Buscar el recurso **Face API** de Azure y seleccionar que **Crear**.
        | Parámetro | Valor |
        | --- | --- |
        | Grupo de recursos | Seleccionar el grupo de recursos que es igual al inicio de ésta práctica. |
        | Nombre | Asignar un nombre al recurso. |
        | Plan de tarifa | Seleccionar el plan de tarifa gratuito. | 
    
    - Se **Revisa y crea** para terminar con la creación del recurso.
    ![FaceAPI](/PracticaFace/Faceimages/FaceAPI.gif)


5. Una vez teniendo el servicio, se obtendrá la llave de conexión. Se debe acceder al recurso creado y, desde el panel izquierdo se busca la sección **Claves y puntos de acceso**.  
    - Se copia la primera llave de acceso y después se ingresa dicha llave en el campo: 
    `subscription_key = "AQUÍ_PONES_TU_CLAVE_DEL_RECURSO_DE_AZURE"`
    ![Claves](/PracticaFace/Faceimages/Claves.gif)
    - En en recurso, se busca (y copia) la clave de **Extremo** y se pegan en el campo: 
    `face_api_url = "URL_DE_FACE_API"`
    ![extremo](/PracticaFace/Faceimages/extremo.gif)


6. Finalmente, se debe ejecutar el código [>>] para mostrar la información de la imagen de acuerdo con lo que la IA ha obtenido.

*Se puede colocar cualquier URL de imagen en la variable `image_url` para saber qué puede arrojar de resultado.*



##### Ahora contamos con una manera de realizar reconocimiento facial en Azure con *Cognitive Services y Machine Learning*.

---- 
# **⚠Importante⚠** 
### Recordar que, si no se requiere más del servicio, se puede eliminar pulsando el botón **Detener** después de haber seleccionado la *instancia de proceso* que, se encuentra en **Proceso** del panel izquierdo.
O bien, eliminar el grupo de recursos dentro del [Portal de Azure](https://portal.azure.com/) si no se requiere todo el contenido de dicho grupo.

###### <sub>[Volver al índice principal de prácticas](/README.md)<sub>

## Hasta aquí la finalización de la práctica.