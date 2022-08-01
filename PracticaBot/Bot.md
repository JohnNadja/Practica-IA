# Práctica sobre creación de un Bot para conversaciones de texto.
![Bot Service logo](/images/Bot-service.png)

Durante la siguiente práctica se usará un servicio de *Preguntas y Respuestas* (Chat de asistencia) para crear un Bot que responda a preguntas de texto. Éstos (Bots) pueden ser usados principalmente para interactuar con usuarios de una aplicación, de una tienda o sitio web que tengan preguntas frecuentes o de alta demanda por atención al cliente.

----
# Requisitos
 - Ingresar al sitio de [QnA Maker](https://www.qnamaker.ai/) con la cuenta de Azure que se creó en el paso anterior del índice principal.

----
# Instrucciones
Una vez ingresado al sitio (con la cuenta de Azure) que se menciona en requisitos (QnA Maker), se procederá a realizar lo siguiente.
1. Seleccionamos la opción "Crear una base de conocimiento" (Create a knowledge base). Hará que se despliegue una lista de pasos.
    - Paso 1: Crear un QnA Service de *Cognitive Services* (nos redirige a la página del Portal de Azure). Dentro. se procede a llenar los datos requeridos.
        - Datos básicos:
            | Parámetro | Valor |
            | ---------- | ----- |
            | Grupo de recursos | Seleccionar el grupo de recursos donde se desea tener el QnA Maker Service. Si no se cuenta con alguno, se puede crear en ese momento. |
            | Nombre | Nombre del QnA Maker Service. |
            | Plan de tarifa | Seleccionar el plan de tarifa que se desea utilizar. Si se puede, usar la opción **Gratis**, pero habrá limitaciones en compraración con **Estándar**. En esta ocasión de la práctica se selecciona *"Estándar¨*.|
            | Plan de tarifa de Azure Search | Seleccionar el plan de tarifa que se desea utilizar. Si se puede, usar la opción **Gratis**, pero habrá limitaciones en compraración con otros. En esta ocasión de la práctica se selecciona *"Básico B¨*.|

        - Pulsar el botón de *Revisar y Crear*, seguido de **Crear**
        ![QnA1](/PracticaBot/Botimages/QnA1.gif)

        - Esperar a que se cargue la página de Qna Maker, a veces se tarda un poco.

    - Paso 2: Si aun no aparece nada en este paso, se debe pulsar el botón **Actualizar (Refresch)**. Una vez listo, se procede a llenar los datos.
        | Parámetro | Valor |
        | ---------- | ----- |
        | Suscripción | Seleccionar la suscripción activa. |
        | QnA Service | Seleccionar el QnA Maker Service creado previamente. |
        | Idioma | Seleccionar el idioma que se desea utilizar el QnA Maker (Ése será el idioma para todas las pregutnas y respuestas que tendrá el bot.) Uns vez creado el bot con dicho idioma, ya no podrá ser modificado. |

        ![QnA2](/PracticaBot/Botimages/QnA2.png)

    - Paso 3: Se le coloca el nombre al bot,
    - Paso 4: Seleccionamos el tipo de **Chit chat** (como personalidad del bot), Usaremos el modo *Ninguno* (no se tendrá personalidad).
    - Paso 5: Se crea la base de conocimiento.
    ![QnA345](/PracticaBot/Botimages/QnA345.gif)

2. Dentro de la base de conocimiento y con el botón de **Añadir par QnA**, se empezará a crear las preguntas y respuestas. Se realiza por medio de el ingreso de texto en el campo de pregunta y respuesta.
    Ejemplo:
    | Lado de la pregunta (izquierdo) | Respuesta (derecha)|
    | ------------------------------ | -------------- |
    ¿Cómo se llama el bot? | **Nombre del bot*. - (También se pueden adjuntanr tablas, imágenes, URL's, dar formato, entre otros complementos a la respuesta)|

    - Se pueden crear múltiples preguntas y respuestas. Aunque, si hay preguntas similares, se pueden adaptar preguntas similares para concatenar a una sola respuesta genérica.
    ![QnApyr](/PracticaBot/Botimages/QnApyr.gif)


3. Una vez creadas las preguntas y respuestas, se procede **Guardar y Entrenar (Save and train)**.

4. Una vez entrenado, se pueden realizar **Pruebas (tests)** para verificar que el bot funciona correctamente (Pueden agregarse preguntas y respuestas después de haber sido entrenado y siempre pulsar el botón de *Guardar y Entrenar*).
    - Si se quiere revisar el procentaje de acierto del bot, se puede hacer mediante el botón de *Inspeccionar* en las preguntas y se visualizará el puntaje de acierto.

    ![QnAsave](/PracticaBot/Botimages/QnAsave.gif)

5. Una vez que el bot presente buenas pruebas, se procede a **Publicar (publish)**. Hay dos opciones:
    - Se puede publicar el bot en una página de Facebook, Twitter, etc, usando el URL del cuadro de teto.
    - Crear un bot con ***Azure Bot Service***[**]() pulsando el botón de *Crear bot (Create bot).
        - Se procede a editar los datos.
            | Parámetro | Valor |
            | ---------- | ----- |
            |Elegir plan de tarifa | Seleccionar el plan de tarifa que se desea utilizar. Si se puede, usar la opción **Gratis**, pero habrá limitaciones en compraración con **Estándar**.|
            | [EXTRA] Idioma del SDK[*](https://www.redhat.com/es/topics/cloud-native-apps/what-is-SDK#:~:text=Un%20kit%20de%20desarrollo%20de%20software%20(SDK)%20es%20un%20conjunto,o%20un%20lenguaje%20de%20programaci%C3%B3n.) | Seleccionar el idioma que se desea utilizar el SDK (El idioma del bot si se descargará[*] y editar su código fuente para subirlo a otra plataforma con Azure).|

            - Se valida con el botón de *Crear*
            ![QNABotService](/PracticaBot/Botimages/QNABotService.gif)

6. Cuando se complete la creación, se puede ver el bot en la página de Azure Bot Service. Dentro del servicio, se selecciona la sección **Probar en el Chat en web** que se encuentra en el panel izquierdo.

7. Continuando en el recurso de ***Azure Bot Service***, se procede a ir a la sección **Canales**. Aqui, dependiendo de la plataforma, se realizarán los pasos para preparar el bot hacia la plataforma de destino.



---- 
# **⚠Importante⚠** 
### Recordar que, si no se requiere más del servicio, se puede eliminar pulsando el botón **Detener** después de haber seleccionado la *instancia de proceso* que, se encuentra en **Proceso** del panel izquierdo.
O bien, eliminar el grupo de recursos dentro del [Portal de Azure](https://portal.azure.com/) si no se requiere todo el contenido de dicho grupo.

###### <sub>[Volver al índice principal de prácticas](/README.md)<sub>

## Hasta aquí la finalización de la práctica.


-----


###### *
Para descargar el código fuente del bot, se debe ir a la sección **Información general** del recurso de ***Azure Bot Service*** y presionar el botón de *Descargar código fuente del bot*. ***Se tiene que esperar a que el recurso se haya creado correctamente.***

###### **
Por cada cambio realizado en **QnA MAker**, se debe guardar y entrenar antes de crear el servicio de *Azure Bot Service* ya que, por cada cambio, se creará un nuevo código diferente para la creación del bot.