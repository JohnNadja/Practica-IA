# Prácticas de Inteligencia Artificial con los servicios de Azure
![IA](/images/IA.png)

## Índice
### [Introducción](#introducción) 📖
### [Prerrequisitos](#prerrequisitos-para-las-prácticas) 📝
### [Prácticas con Machine Learning](#prácticas-con-machine-learning) 
### [Prácticas Cogninitive Services](#prácticas-cogninitive-services) 


### Introducción

La Inteligencia Artificial puede ser usada para diferentes fines, pero la mayoría de ellas se basa en la resolución de problemas. En esta ocasión se tendrá la oportunidad de practicar con los servicios de Azure para resolver problemas de la Inteligencia Artificial. Existen "***modelos***" que, en pocas palabras, son datos que pueden ser **[Prefabricados](#prefabricados)** (basado en la nube) para ser usados en cualquier aplicación dentro del ambiente Azure. También exiten modelos que pueden ser **Creados** a través de *Machine Learning* (se puede proporcionar los datos para modelar). Y por último se tienen los modelos **Bot** que, únicamente sirven para crear respuestas automáticas en servicios de *Preguntas y Respuestas*, *Chat de asistencia*, etc.

#### *Prefabricados*

Los modelos prefabricados en Azure contiene modelos como:
- **Transalator**: traductores de un idioma a otro.
- **Content Moderator**: moderador de contenido que se envía (por ejemplo, de una aplicación a otra).
- **[LUIS](https://docs.microsoft.com/es-mx/azure/cognitive-services/luis/what-is-luis)** (Language Understanding): sistema de reconocimiento de intenciones de una aplicación. Analiza texto para obtener infromación detallada del lenguaje natural.
- **Custom Vision** (visión computacional): sistema de reconocimiento de imágenes y/o videos.
- **Anomaly Detector**: detector de anomalías de algún patrón.
- **Face**: reconocimiento de rostros, género, edad, etc.

***Estos modelos son usados en Cognitive Services de Azure***. Algunos pueden ser personalizados, pero otros no.

#### *Creados*

Este tipo de modelos requieren de personalización para ser usados. Es decir, requiere de muchos datos para poder crear un modelo lo más preciso posible para tener resultados aceptables en cuanto la problématica lo requiera para ser resuelta. La Inteligencia Artificial es una herramienta que creará reglas para poder ir acercándose a una respuesta valida.
- Machine Learning Automation: sistema de automatización de Machine Learning.
- Diseñador: sistema de Machine Learning para poder *pulir* datos y tener mejores resultados.

*Para esta ocasión, se usarán algunos de los servicios más utilizados en Azure para Inteligencia Artificial.*

----

### Prerequisitos para las prácticas
 - Tener una cuenta de Azure para realizar la práctica en su [*Portal*](https://portal.azure.com/#home) (si aún no se cuenta con alguna, se puede hacer el registro en el siguiente [*enlace*](https://azure.microsoft.com/es-mx/free/)). 
 - Contar con una suscripción activa de Azure para poder realizar la práctica (en el enlace anterior se muestra como se puede hacer).



### Prácticas con Machine Learning
![ML](/images/Machine-Learning.png)

- [Machine Learning Automatizado](/PracticaMLAuto/MLAuto.md) ![MLS](/images/Machine-Learning-Studio.svg)

### Prácticas con Cognitive Services
![Cognitive Services](/images/cognitive-Services.png)

- [Face](/PracticaFace/Face.md)
- [Custom Vision](/PracticaCV/CV.md)
- [Bot Service](/PracticaBot/Bot.md)
