---
title: "Crear un caso de uso de disputa de transacción"
chapter: true
weight: 30
---

## Crear un caso de uso de disputa de transacción

Ahora ha llegado el momento de crear un flujo de bot utilizando una ranura de lista dinámica (dynamic list slot). Debido a que no podemos esperar que todos tengan acceso a la misma plataforma externa para extraer una serie de datos, creamos una API simulada que ayudará a lograr nuestro caso de uso.

El caso de uso que desarrollaremos hoy será para disputar una transacción en un banco. Piense en los 3 tipos de ranuras (slots) que cubrimos en la introducción: lista, lista dinámica y expresión regular. Sus transacciones más recientes son ciertamente una lista, pero son dinámicas porque son diferentes para cada persona y con frecuencia agrega nuevas transacciones a la lista (algunas personas más que otras). Entonces, esta es una oportunidad para usar un tipo de ranura de lista dinámica que extrae las transacciones más recientes a través de una llamada API y usa esa lista dinámica como la lista para el tipo de ranura.

Lo dividiremos en 5 pasos: 

1. Crear la acción de datos
2. Creación del flujo de bot de Genesys (Genesys Bot Flow) - *este es el enfoque de nuestro taller*
3. Crear el flujo de mensajes entrantes (inbound message flow)
4. Creación de la configuración e implementación de Web Messenger para pruebas
5. Pruebas