---
title: "Creación de la configuración e implementación de Web Messenger para pruebas"
chapter: false
weight: 40
---

## Creación de la configuración e implementación de Web Messenger para pruebas

Con el bot y el flujo de mensajes creados, estamos listos para crear una configuración e implementación de Messenger. Si ya tiene esto creado y le gustaría usarlo, siéntase libre de simplemente apuntar su Implementación de Web Messenger al flujo de mensajes entrantes de architect que acabamos de crear.

### Cofiguración de Web Messenger 
La configuración de web messenger es donde definiremos la visibilidad, la apariencia y otros elementos de configuración diversos sobre cómo se comportará el messenger.

Dentro de la aplicación principal de Genesys Cloud, vaya a Admin > Configuraciones de Messenger y cree una nueva.

Si bien hay muchas opciones de configuración, solo proporcionaremos un nombre y seleccionaremos nuestro idioma predeterminado (desplazándonos hasta la parte inferior de la pestaña de apariencia) para este taller, como se ve a continuación:

![Call Bot Flow](/images/Messageconfigname.PNG)

![Call Bot Flow2](/images/messageconfiglanguage.PNG)

Para obtener una explicación de las opciones de configuración adicionales, puede revisar este artículo del centro de recursos - https://help.mypurecloud.com/articles/configure-messenger/

Ahora puede Guardar nueva versión.

### Despliegue de Web Messenger 

Dentro de la aplicación principal de Genesys Cloud, vaya a Admin > Implementaciones de Messenger y cree una nueva.

La implementación es donde uniremos nuestra configuración de messenger con nuestro flujo de mensajes (y, en última instancia, nuestro flujo de bot).

1. Asigne un nombre a su configuración
2. Habilite el estado del messenger
3. Seleccione su configuración (buscará la configuración de mensajería web que acabamos de crear)
4. Permitir en todos los dominios (esto simplificará las pruebas)
5. Seleccione su flujo de architect de mensajes entrantes (inbound message architect flow)

Después de configurar estas opciones, su implementación debería verse así:

![Message Deployment](/images/messagedeployment.PNG)