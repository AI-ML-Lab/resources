![Dynamic JSON Badge](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2FAI-ML-Lab%2Fresources%2Fmain%2Fproperties.json&query=%24.repo.ac_llm%5B0%5D.version&logo=bitbucket&label=version&labelColor=1A3B47) ![version from json](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2FAI-ML-Lab%2Fresources%2Fmain%2Fproperties.json&query=%24.repo.ac_llm%5B%3F(%40.version%20%3D%3D%20'0.1.0')%5D.usos&label=usos%20en%20proyecto&labelColor=1A3B47) ![contributors](https://img.shields.io/badge/contributors-4-79C5B4?&labelColor=1A3B47) ![website](https://img.shields.io/website/http/ailyn.link?&labelColor=1A3B47&label=demo) [![Email me](https://img.shields.io/badge/Email%20me-1A3B47)](mailto:eejimenez@minsait.com) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1dydDd2nne-_fl8w0cA1DbLtjEvM3hICJ?usp=sharing) ![language](https://img.shields.io/badge/language-python-blue)
[![Download as PDF Button](https://img.shields.io/badge/Download%20%20pdf-EF3939?style=flat&logo=adobeacrobatreader&logoColor=white&color=black&labelColor=ec1c24)](https://mdtopdf.up.railway.app/convertPdf?url=https://raw.githubusercontent.com/AI-ML-Lab/resources/main/Readme.md)
<p align="center">
<img src="images/wh.png"width=20%>
<p align="center" href=>
    <img src="images/m_dimensiones.gif"width=7%>
    <img src="images/m_lab.png" width=30%>
<p align="center">
<img src="images/wh.png"width=10%>

![banner](images/m_banner-acllm.png)

<a name="toc"></a>


[![benchmark](images/card_benchmark.png)](#bench) [![seguridad](images/card_seguridad.png)](#sec) [![licencias](images/card_licencias.png)](#lic)[![integraciones](images/card_integraciones.png)](#int) [![costos](images/card_costos.png)](#cost) [![referencias](images/card_referencias.png)](#ref) [![referencias](images/card_tiempo.png)](#acel)

<a name="ap"></a>
## Aplicaciones

Las aplicaciones que este acelerador ha impulsado son asistentes inteligentes que pueden datos estructurados y APIs sintetizando la información.

## **Casos de uso particulares**
     

![MIA](images/ap_mia.png){width=30 height=30} **Asistente para planeación de viajes y reservaciones** [![try me](https://img.shields.io/badge/Try%20me-Whatsapp-brightgreen?logo=whatsapp)](https://api.whatsapp.com/send/?phone=5215573747795&text&type=phone_number&app_absent=0) [![repo](https://img.shields.io/badge/repositorio-blue?logo=bitbucket)](https://bitbucket.indra.es/projects/GT_PLAIMX/repos/de_mia-langchain) 

![aeromexico](images/ap_aeromexico.png){width=30 height=30} **Recuperación de información de pasajeros** [![repo](https://img.shields.io/badge/repositorio-blue?logo=bitbucket)](https://bitbucket.indra.es/projects/GT_PLAIMX/repos/pr_aeromexico-pronostico/browse)

<a name="bench"></a>
## Benchmark
[:arrow_up:](#toc)

Si bien no existe una metodología de comparación de LLMs dominante o probada existen algunos referentes en la indsutria que nos ayudan a tener una idea del performance general que llevan los modelos que se van generando evaluandolos en diferentes tareas. Para esto el que mantiene más actividad por ser una evaluación automática es [AlpacaEval](https://github.com/tatsu-lab/alpaca_eval/tree/main) y [MosaicML](https://www.mosaicml.com/llm-evaluation) puedes ver su [score](https://docs.google.com/spreadsheets/d/e/2PACX-1vSAwA8-DdEgGHlbX1XkP7KoYWQD2HzKDGsID33MypM17FsjVw5YmT4ceUK-ryfH4jL9jBW8u1DTGWuS/pubhtml#) en tiempo real.

<p align="center">
    <img src="images/ref_mosaic-eval.png" width=40%>
    <img src="images/ref_benchmark.png" width=30%>

### Performance
Sin embargo podemos evaluar lo siguiente a grandes rasgos:

- **Conocimiento del Mundo:** capacidad para responder preguntas sobre una amplia variedad de temas con exactitud.

- **Sentido Común:** capacidad de realizar tareas de razonamiento básico e inferencias utilizando conocimiento del sentido común.

- **Comprensión del Lenguaje:** comprensión de los modelos en idiomas, traducciones y resolución de anáforas.

- **Resolución de Problemas Simbólicos:** resolución de diversas tareas como aritmética, lógica y algoritmos.

- **Comprensión de Lectura:** Precisión de respuestas a preguntas basadas en textos proporcionados.

- **Programación:** Evaluación de la comprensión y generación de código funcional por parte de los modelos.

En función del caso de uso lo más recomendable es usar métricas personalizadas que incluyan la proporción de aciertos al realizar la tarea predefinida en el template,o la tasa de alucinaciones que son generadas o incluso independientemente de la respuesta del modelo y sus posibles alucinaciones el número de veces que se completó la tarea satisfactoriamente usando un modelo de evaluación con otro llm o con una calificación humana que sirva de reforzamiento.

Un ejemplo de caso de uso es, si la tarea es generar una query que permita hacer una consulta sobre un nombre o un lugar en particular el número de fallas que se registraron al hacer esas querys


## Modelo elegido para acelerar

**Llama2** 🦙

<a name="lic"></a>
## Licenciamiento
[:arrow_up:](#toc)

Los modelos de Llama están disponibles bajo una licencia de open source que puede ser utilizada para proyectos comerciales:

<a name="int"></a>
## Integraciones
[:arrow_up:](#toc)

Algunos frameworks disponbiles para trabajar con LLMs son:

| Proyecto        | Descripción                                                                                                 |
|-----------------|-------------------------------------------------------------------------------------------------------------|
| [Alpaca Farm ](https://github.com/tatsu-lab/alpaca_farm/)    | AlpacaFarm es un framework de reforzamiento humana. Contiene código para simular retroalimentación de preferencias, evaluación automatizada y algoritmos de aprendizaje por refuerzo como PPO.                                                                                                                             |
| [Flax](https://flax.readthedocs.io/en/latest/)            | Flax es una biblioteca de redes neuronales para JAX que proporciona operaciones de diferenciación y vectorización en python con el que se han construido modelos de lenguaje visión y multimodales como Palm                                                                                                           |
| [GGML](https://github.com/ggerganov/ggml)            | GGML es framwork para cuantizar LLMs y hacerlos más ligeros. Bibliotecas populares basadas en GGML incluyen llama.cpp y whisper.cpp.                                                                                               |
| [Hugging Face](https://huggingface.co/models?other=LLM)    | Ofrece una amplia biblioteca de Transformers y Demos de LLMs para probar la mayoría de ellos.                                                                                                          |
| [Lamini](https://github.com/lamini-ai/lamini)          |Permite el ajuste fino, RLHF y optimizaciones para que el LLM autohospedado funcione de manera eficiente.                                                                                                                     |
| [LangChain](https://python.langchain.com/docs/get_started/introduction.html)       | LangChain proporciona módulos para modelos, estímulos, índices, cadenas y agentes, con la capacidad de "encadenar" estos módulos entre sí.                                                                                                                           |
| [LlamaIndex](https://github.com/jerryjliu/llama_index)      | Permite integrar datos privados/personalizados con conectores de datos, índices/gráficos compatibles con LLM y una interfaz de consulta sobre los datos.                                                                                                                                     |
| [LMFlow](https://github.com/OptimalScale/LMFlow/blob/main/readme/README_es.md)          | Framework de integración y ajuste de LLM y visión orientado a tareas. Soporta estructuras comunes como LLaMA y GPT-2.                                                                                                                                         |
| [MLC LLM](https://github.com/mlc-ai/mlc-llm)         | MLC LLM permite que se desplieguen LLMs nativamente en hardware y aplicaciones como en iOS, Android, Apple Silicon, AMD, Intel, NVIDIA y WebGPU.                                                             |


Dependiendo de la aplicación podemos optar por diferentes plataformas y arquitecturas sin embargo podemos encontrar algunos patrones en la construcción de aplicaciones con LLMs que podemos clasificar como en el siguiente diagrama

<p align="center">
    <img src="images/ref_patterns.png" width=50%>

- Evals: métricas de performance
- [RAG](https://learn.microsoft.com/en-us/azure/machine-learning/concept-retrieval-augmented-generation?view=azureml-api-2): (Retrieval Augmented Generation) agregar información reciente
- Fine-tuning: mejorar en tareas específicas
- Caching: almacenamiento para reducir costos y latencia
- Guardrails: estrategias de contensión para mejorar la calidad de las salidas
- Defensive UX: Anticipar y manejar posibles errores desde el UX
- Collect user feedback: Generar un sistema de recomendación

Hasta ahora sólo se ha probado la integración con langchain por su facilidad para hacer estrategias de caché, ux defensivo y filtros de calidad, también debido a la documentación y facilidad de integración temprana sin embargo a 6 meses de la presentación de chatGPT ya hay herramientas de bajo costo para hacer fine tuning. ESto puede traer los siguientes beneficios:

- **Rendimiento y control**: mejorando el rendimiento de un modelo base listo para usar e incluso superar a un LLM de terceros. También proporciona un mayor control sobre el comportamiento del LLM, lo que resulta en un sistema o producto más robusto. En general, el fine-tuning nos permite crear productos que se diferenciadores.
- **Modularización**: El fine-tuning de una sola tarea nos permite utilizar un ejército de modelos más pequeños que se especializan cada uno en sus propias tareas. como moderación de contenido, extracción, resumen, etc. Además, dado que cada modelo solo tiene que centrarse en un conjunto de tareas limitado, hay menos preocupación de que el fine-tuning de un modelo en una tarea reduce el rendimiento en otras tareas.
- **Reducción de dependencias**: Al alojar nuestros propios modelos, podemos reducir las preocupaciones legales sobre los datos de propiedad (por ejemplo, PII, documentos internos y código) que se exponen a las API externas y evita las restricciones que vienen con los LLM de terceros, como el límite de velocidad, los altos costos o los filtros de seguridad demasiado restrictivos. 

Este es el esquema básico de construcción de aplicaciones en caché
<p align="center">
    <img src="images/ref_gptcache.jpg" width=50%>

Sin embargopara mejorar la precisión del modelo tenemos algunas opciones

<a name="esc"></a>
## Escalabilidad
[:arrow_up:](#toc)

Dado que los Llms los podemos pensar en dos sentidos de integración ahondaremos enn las posibilidades de escalar ambos escenarios.

En el primero hacemos un uso de la API de OpenAI con los siguientes rate limits:

<p align = "center">
    <img src="images/ref_ratelimit-openai.png"width=30%>

para los modelos más antiguos tenemos las siguientes equivalencias de tokens:

| Type    | 1TPM                  |
|---------|-----------------------|
| davinci | 1 token per minute    |
| curie   | 25 tokens per minute  |
| babbage | 100 tokens per minute |
| ada     | 200 tokens per minute |

Estas limitaciones son a nivel organización y no a nivel usuario o key por lo que para un proyecto que requiera llevarse a productivo considerando conversaciones coocurrentes sería necesario utilizar varios modelos para evitar saturar los rate limits con pocos usuarios. Un escenario de ejemplo podría considerarse el siguiente:

Para una consulta en el asistente **MIA** se utilizan 3 requests a la API de OpenAI:

1. Una para determinar el comportamiento esperado y enrutar al agente necesario.
2. Otra para refrasear el input original para devolver un input que pueda ser comprendido por la API de Maps
3. Una tercera que dado el contexto devuelto por la API y el contexto de la conversación responda adecuadamente a la pregunta

> Esto es significa que para responder una sola pregunta utiliza entre 500 y 1000 tokens dependiendo de la longitud del contexto. Por lo tanto una interacción común con MIA que puede requerir varias consultas o preguntas usa entre 500 hasta 10,000 tokens y unas 30 requests por usuario. Es claro que dado que los tiempos de latencia y escritura de los usuarios finales el número de consultas por minuto puede variar pero si tomáramos una sola consulta por usuario al mismo tiempo llegaríamos al límite con 500 usuarios en el escenario más favorable


$700tokens \times 500users = 350,000TPM$

En este escenario hay dos posibilidades para facilitar su escalabilidad, la primera es utilizar una variedad de modelos para finalidades distintas así podríamos aprovechar el rate limit por modelo, el siguiente sería utilizar un modelo propio como Llama2 y una tercera opción sería encolar los usuairos simnultaneos para poder distribuir el número de llamadas
>:warning: La integración con Composer o algún pipeline basado en DAGs no se recomienda en ninguno de los dos casos como una implementación punta a punta sino sólamente para el proceso de reentrenamiento ya que al hacer un escalamiento dinámico horizontal la carga de los modelos y en caso de requerirlo el entrenamiento se haría en cada pod de procesamiento lo cuál implicaría un costo de entrenamiento duplicado y tiempos más largos de inferencia. Es preferible en todo caso para esta tarea un escalado vertical siempre y cuando se cuente con un modelo propio cargado en local


### Arquitecturas

La demo de MIA está montada en flask en una instancia de **EC2** que apunta a un dominio en **route53** con un certificado SSL de **ACM** ya que la API de whatsapp necesita que la información que va al webhook viaje a través de una conexión https. Para escalar esta demo no sólo tenemos rate limits de consumo en las APIs sino limitantes de tráfico en una instancia **EC2**. Las pruebas que se han generado con Apache Benchmark nos dicen que un servidor de ec2 puede manejar 250 llamadas concurrentes con un tiempo promedio de respuesta de 86 milisegundos sin embargo deja de responder ante 450 llamadas concurrentes.



<p align = "center"><strong>Comparativa de arquitecturas</strong>
<p align = "center">
    <img src="images/arq_demo-mia.png"width=20%>
    <img src="images/wv.png"width=5%>
    <img src="images/arq_elb.png" width=30%>

<p align = "center">
    <img src="images/screen_loadtest-ec2.png"width=29%>
    <img src="images/wv.png"width=5%>
    <img src="images/screen_loadtest-elb.png" width=30%>


Al colocar un balanceador de carga observamos que las métricas de respuesta se conservan sin embargo con dos instancias se pueden manejar hasta 750 llamadas concurrentes por el balanceador de carga.

Esto es muy parecido a la propuesta de una arquitectura de beanstalk toma como ejemplo de buena arquitectura para una aplicación de flask en su [documentación](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create-deploy-python-flask.html) 

<p align="center">
    <img src="images/arq_beanstalk.png">

Sin embargo algunas alternativas de escalabilidad y portabilidad con un servicio de IaC puede ser un despliegue con **AWS CDK** y **FastAPI** como la de abajo que también explica detalladamente aws en sus ejemplos de [well architecture](https://aws.amazon.com/es/blogs/machine-learning/deploy-a-serverless-ml-inference-endpoint-of-large-language-models-using-fastapi-aws-lambda-and-aws-cdk/). Esta ademas de ser muy portable tiene la bondad de que cada conversación levanta una única función lambdas que tiene sirve de enrutador para un modelo largo de lenguaje hacia las consultas a diferentes APIs y cumple con requerir poca RAM y poco tiempo de procesamiento por llamada. haciendo que la escalabilidad sea mayor por diseño y más económico en costos de servidor

<p align="center">
    <img src="images/arq_aws-cdk.png">

La elección de la arquitectura a utilizar será en función de las necesidades de escalabilidad, familiaridad con la infraestructura y tiempo de implementación y configuración necesarias

<a name="sec"></a>
## Seguridad
[:arrow_up:](#toc)

El modelo Llama2 con sus pesos puede descargarse en local por lo que es posible aislar el componente de lenguaje del tráfico de Open-Web facilitando ajustarse a los lineamientos de ciberseguridad del cliente. 
No se han detectado vulnerabilidades comunes en la librería de langchain aunque si ineficiencias en el uso de los tokens ya que para hacer uso de la memoria hace un almacenamiento recursivo que usa como contexto y en conversaciones largas puede afectar seriamente el funcionamiento y los recursos de cómputo disponibles

### Research & References

Llama 2

> :heavy_check_mark: Se han descargado los modelos llama7b y el fine tuning de llama2 7b-chat así como el modelo Llama2 70b-chat es posible revisar mayor información en la [página oficial](https://ai.meta.com/llama/)
  
<a name="cost"></a>
## Costo de implementación
[:arrow_up:](#toc)

## Contenedor

## API
<a name="demo"></a>
## Demos
[:arrow_up:](#toc)

Se ha generado una demo que incluye un asistente inteligente para viajes que es capaz de consultar APIs en tiempo real y recomendar en función de los resultados obtenidos
  

  El backend de cada aplicación se encuentra en el repo **de_mia-langchain**
  
  Para interactuar con el asistente está disponible en whatsapp
<a name="acel"></a>
## Detalles de la aceleración
[:arrow_up:](#toc)

### Tiempo de desarrollo 

2 meses

### Tiempo ahorrado en creación de demos

1 mes

<a name="ref"></a>
#### Artículos
[:arrow_up:](#toc)

[Sharepoint](https://indra365.sharepoint.com/:f:/r/sites/Grp_T_Hub_AAI_LatAm-AILab/Documentos%20compartidos/Art%C3%ADculos?csf=1&web=1&e=dPLezJ)



<p align="center">
    <img src="images/m_bottom.png"
    width=95%>

<a name="repo"></a>
## Árbol de repositorio
[:arrow_up:](#toc)
```
│   image.png
│   Readme.md
│
├───images
│       ap_aeromexico.png
│       ap_mia.png
│       arq_aws-cdk.png
│       arq_beanstalk.png
│       arq_demo-mia.png
│       arq_elb.png
│       card_benchmark.png
│       card_costos.png
│       card_integraciones.png
│       card_licencias.png
│       card_referencias.png
│       card_seguridad.png
│       card_tiempo.png
│       m_ailab.png
│       m_banner-acllm.png
│       m_bottom.png
│       m_dimensiones.gif
│       m_lab.png
│       ref_benchmark.png
│       ref_gptcache.jpg
│       ref_mosaic-eval.png
│       ref_patterns.png
│       ref_ratelimit-openai.png
│       screen_loadtest-ec2.png
│       screen_loadtest-elb.png
│       wh.png
│       wv.png
│
└───notebooks
        Fine_tune_a_language_model.ipynb
        llm metrics.ipynb
```
