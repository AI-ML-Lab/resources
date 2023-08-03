![Dynamic JSON Badge](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2FAI-ML-Lab%2Fresources%2Fmain%2Fproperties.json&query=%24.repo.ac_llm%5B0%5D.version&logo=bitbucket&label=version&labelColor=1A3B47) ![Dynamic JSON Badge](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2FAI-ML-Lab%2Fresources%2Fmain%2Fproperties.json&query=%24.repo.ac_llm%5B%3F(%40.version%20%3D%3D%20'0.1.0')%5D.usos&label=usos%20en%20proyecto&labelColor=1A3B47)  [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1dydDd2nne-_fl8w0cA1DbLtjEvM3hICJ?usp=sharing)  ![contributors](https://img.shields.io/badge/contributors-4-79C5B4) ![Dynamic JSON Badge](https://img.shields.io/website/http/ailyn.link) ![language](https://img.shields.io/badge/language-python-blue) [![Email me](https://img.shields.io/badge/Email%20me-1A3B47)](mailto:eejimenez@minsait.com)


<p align="center">
    <img src="images/ailab.png">



## Aplicaciones

Las aplicaciones que este acelerador ha impulsado son asistentes inteligentes que pueden datos estructurados y APIs sintetizando la información.

## **Casos de uso particulares**
     

![MIA](images/mia.png){width=30 height=30} **Asistente para planeación de viajes y reservaciones** [![try me](https://img.shields.io/badge/Try%20me-Whatsapp-brightgreen?logo=whatsapp)](https://api.whatsapp.com/send/?phone=5215573747795&text&type=phone_number&app_absent=0) [![repo](https://img.shields.io/badge/repositorio-blue?logo=bitbucket)](https://bitbucket.indra.es/projects/GT_PLAIMX/repos/de_mia-langchain) 

![aeromexico](images/aeromexico-logo.png){width=30 height=30} **Recuperación de información de pasajeros** [![repo](https://img.shields.io/badge/repositorio-blue?logo=bitbucket)](https://bitbucket.indra.es/projects/GT_PLAIMX/repos/pr_aeromexico-pronostico/browse)

## Benchmark

### Performance

<p align="center">
    <img src="images/benchmark.png">

## Modelo elegido para acelerar

**Llama2**

## Licenciamiento

Los modelos de Llama están disponibles bajo una licencia de open source que puede ser utilizada para proyectos comerciales:


## Integraciones

Se probaron los siguientes frameworks para integrar moidelos de lenguaje:

Se eligió integrarlo con langchain debido a la documnentación y facilidad de integración

## Escalabilidad

Dado que los Lllms los podemos pensar en dos sentidos de integración ahondaremos enn las posibilidades de escalar ambos escenarios.

En el primero hacemos un uso de la API de OpenAI con los siguientes rate limits:

![rate limits](images/apenaiquotas.png)

para los modelos más antiguos tenemos las siguientes equivalencias de tokens:

| type    | 1TPM                  |
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

La demo de MIA está montada en flask en una instancia de **EC2** que apunta a un dominio en **route53** con un certificado SSL de **ACM** ya que la API de whatsapp necesita que la información que va al webhook viaje a través de una conexión https.

Sin embargo algunas alternativas de escalabilidad puede ser un despliegue con **AWS CDK** y **FastAPI** como la siguiente

<p align="center">
    <img src="images/arquitectura_aws-cdk.png">


## Seguridad

El modelo Llama2 con sus pesos puede descargarse en local por lo que es posible aislar el componente de lenguaje del tráfico de Open-Web facilitando ajustarse a los lineamientos de ciberseguridad del cliente. 
No se han detectado vulnerabilidades comunes en la librería de langchain aunque si ineficiencias en el uso de los tokens ya que para hacer uso de la memoria hace un almacenamiento recursivo que usa como contexto y en conversaciones largas puede afectar seriamente el funcionamiento y los recursos de cómputo disponibles

### Research & References

Llama 2

> :heavy_check_mark: Se han descargado los modelos llama7b y el fine tuning de llama2 7b-chat así como el modelo Llama2 70b-chat es posible revisar mayor información en la [página oficial](https://ai.meta.com/llama/)
  

## Contenedor

## API

## Demos
Se ha generado una demo que incluye un asistente inteligente para viajes que es capaz de consultar APIs en tiempo real y recomendar en función de los resultados obtenidos
  

  El backend de cada aplicación se encuentra en el repo **de_mia-langchain**
  
  Para interactuar con el asistente está disponible en whatsapp

## **Detalles de la aceleración**

### Tiempo de desarrollo 

2 meses

### Tiempo ahorrado en creación de demos

1 mes

#### Artículos

...



<p align="center">
    <img src="images/bottom.png">

## Árbol de repositorio
```
│   Readme.md
│
├───images
│       ailab.png
│       apenaiquotas.png
│       arquitectura_aws-cdk.png
│       benchmark.png
│       bottom.png
│       mia.png
│
└───notebooks
        Fine_tune_a_language_model.ipynb
        llm metrics.ipynb
```