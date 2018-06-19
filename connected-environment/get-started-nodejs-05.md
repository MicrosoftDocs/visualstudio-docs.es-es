---
title: 'Crear un entorno de desarrollo de Node.js con contenedores usando Kubernetes en la nube - Paso 5: Llamar a otro contenedor | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: 89565869feec746aff75327b59ee7d0b466f26c1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31887510"
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introducción a Connected Environment con Node.js

Paso anterior: [Depurar un contenedor en Kubernetes](get-started-nodejs-04.md)

En esta sección vamos a crear un segundo servicio (`mywebapi`) y haremos que `webfrontend` lo llame. Cada servicio se ejecutará en un contenedor diferente. Luego, depuraremos ambos contenedores.

![](media/multi-container.png)

## <a name="open-sample-code-for-mywebapi"></a>Abrir el código de ejemplo de *mywebapi*
Ya debería tener el código de ejemplo de `mywebapi` para esta guía en una carpeta denominada `vsce/samples`. Si no es así, vaya a https://github.com/Azure/vsce y seleccione **Clonar o descargar** para descargar el repositorio de GitHub. El código de esta sección está en `vsce/samples/nodejs/getting-started/mywebapi`.

## <a name="run-mywebapi"></a>Ejecutar *mywebapi*
1. Abra la carpeta `mywebapi` en una *ventana de VS Code aparte*.
1. Presione F5 y espere a que el servicio se compile e implemente. Sabrá que está listo cuando aparezca la barra de depuración de VS Code.
1. Anote la dirección URL del punto de conexión, que tendrá un aspecto parecido a http://localhost:\<númeroDePuerto\>. **Consejo: La barra de estado de VS Code mostrará una dirección URL interactiva.** Puede parecer que el contenedor se ejecuta localmente, pero en realidad se está ejecutando en nuestro entorno de desarrollo en Azure. La razón de usar la dirección de host local es que `mywebapi` no tiene definido ningún punto de conexión público y solo se puede tener acceso a ella desde dentro de la instancia de Kubernetes. Para mayor comodidad, y de cara a facilitar la interacción con el servicio privado desde el equipo local, Connected Environment crea un túnel SSH temporal hacia el contenedor que se ejecuta en Azure.
1. Cuando `mywebapi` esté listo, abra el explorador en la dirección de host local. Debería ver una respuesta del servicio `mywebapi` ("Hello from mywebapi").


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>Cursar una solicitud de *webfrontend* a *mywebapi*
Ahora, vamos a escribir código en `webfrontend` para cursar una solicitud en `mywebapi`.
1. Cambie a la ventana de VS Code de `webfrontend`.
1. Agregue estas líneas de código al principio de `server.js`:
```javascript
var request = require('request');
var propagateHeaders = require('./propagateHeaders');
```

3. *Reemplace* el código del controlador GET `/api`. Al procesar una solicitud, se realiza a su vez una llamada a `mywebapi` y, después, se devuelven los resultados de ambos servicios.

```javascript
app.get('/api', function (req, res) {
    request({
        uri: 'http://mywebapi',
        headers: propagateHeaders.from(req) // propagate headers to outgoing requests
    }, function (error, response, body) {
        res.send('Hello from webfrontend and ' + body);
    });
});
```

Observe cómo se usa la detección de servicios DNS de Kubernetes para hacer referencia al servicio como `http://mywebapi`. **El código en nuestro entorno de desarrollo se ejecuta de la misma manera en que lo haría en uno de producción**.

En el ejemplo de código anterior se usa un módulo auxiliar denominado `propagateHeaders`. Esta aplicación auxiliar se agregó a la carpeta de código cuando ejecutó `vsce init`. La función `propagateHeaders.from()` propaga encabezados específicos desde un objeto http.IncomingMessage existente a un objeto de encabezados de una solicitud saliente. Más adelante veremos cómo esto facilita una experiencia de desarrollo más productiva en escenarios de trabajo en equipo.


## <a name="debug-across-multiple-services"></a>Depurar en varios servicios
1. Llegado este punto, `mywebapi` debe seguir ejecutándose con el depurador asociado. Si no es así, presione la tecla F5 en el proyecto `mywebapi`.
1. Establezca un punto de interrupción en el controlador GET `/` predeterminado.
1. En el proyecto `webfrontend`, establezca un punto de interrupción justo antes del envío de una solicitud GET a `http://mywebapi`.
1. Presione la tecla F5 en el proyecto `webfrontend`.
1. Abra la aplicación web y recorra el código en ambos servicios. La aplicación web debería mostrar un mensaje donde se concatenan ambos servicios: "Hello from webfrontend" y "Hello from mywebapi".


¡Bien hecho! Ahora tenemos una aplicación con varios contenedores donde cada uno de ellos se puede desarrollar e implementar por separado.

> [!div class="nextstepaction"]
> [Nociones del desarrollo en equipo](get-started-nodejs-06.md)
