---
title: "Creación de la acción de datos"
chapter: false
weight: 10
---

## Creación de la acción de datos

Para el taller, no podemos esperar que todos tengan acceso al mismo sistema de terceros para retirar nuestra lista dinámica, por lo que creamos una API simulada para que todos la usen. Esta API recuperará una lista del historial de transacciones de una persona ficticia. No especificará ninguna entrada; la acción de datos simplemente llegará al extremo de la API y devolverá el mismo historial de transacciones para cada consulta.

Necesitaremos importar esta acción de datos a su instancia de Genesys Cloud CX para que pueda consultar el historial de transacciones en su instancia. Siga los pasos a continuación para importar la acción de datos:

1. Navegue a su consola de administración de Genesys Cloud CX y localice las integraciones
2. Crear una nueva integración del tipo de acciones de datos de servicios web
![Web Services Data Actions](/images/webServicesDataActions.jpg)
3. Asigne a la integración un nombre descriptivo. No necesita preocuparse por configurar las credenciales para esta integración porque solo estamos usando una API MOCK que no requiere credenciales.
4. Haga clic en el botón Acciones en Integraciones en Genesys Cloud CX Admin
5. Navegue a este repositorio de github y siga los pasos en el Léame (ReadMe) https://github.com/genesys-samples/DynamicListSlotDataAction 
6. Haga clic en Importar en la página Acciones y elija el archivo JSON que acaba de descargar. En la categoría de integración, elija la integración de Acción de datos de servicios web que acabamos de configurar
![Import Data Action](/images/importDataAction.jpg)
7. Después de importar la acción de datos, vaya a la herramienta de prueba y haga clic en Ejecutar acción. Debería obtener esta respuesta.
![Data Action Test](/images/dataActionTest.jpg)

Ahora está listo para llamar a esta acción de datos en un flujo de bot de Genesys.