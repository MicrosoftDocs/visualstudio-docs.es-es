---
title: 'Crear un entorno de desarrollo de Node.js con contenedores usando Kubernetes en la nube - Paso 3: Crear una aplicación web ASP.NET | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: 34e1f07e173ccba6aab561fb4795abbe938e0127
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introducción a Connected Environment con Node.js

Paso anterior: [Crear un entorno de desarrollo de Kubernetes en Azure](get-started-nodejs-02.md)

## <a name="create-a-nodejs-web-app"></a>Crear una aplicación web de Node.js
Descargue el código de GitHub; para ello, vaya a https://github.com/Azure/vsce y seleccione **Clonar o descargar** para descargar el repositorio de GitHub en su entorno local. El código de esta guía está en `vsce/samples/nodejs/getting-started/webfrontend`.

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>Actualizar un archivo de contenido
Connected Environment no se reduce exclusivamente a hacer que se ejecute código en Kubernetes: le permite ver rápidamente y de forma iterativa la forma en que los cambios de código surten efecto en un entorno de Kubernetes en la nube.

1. Busque el archivo `./public/index.html` y modifique el código HTML. Por ejemplo, cambie el color de fondo de la página a un tono azul:

```html
<body style="background-color: #95B9C7; margin-left:10px; margin-right:10px;">
```

2. Guarde el archivo. Más tarde, en la ventana de terminal, verá un mensaje que indica que se ha actualizado un archivo en el contenedor en ejecución.
1. Vaya al explorador y actualice la página. Debería ver la actualización de color.

¿Qué ocurre? Las modificaciones de archivos de contenido, como HTML y CSS, no requieren que el proceso de Node.js se reinicie, por lo que un comando `vsce up` activo sincronizará los archivos de contenido modificados de manera automática y directamente en el contenedor en ejecución en Azure, lo que constituye una forma rápida de ver las modificaciones de contenido.

### <a name="test-from-a-mobile-device"></a>Prueba desde un dispositivo móvil
Si abre la aplicación web en un dispositivo móvil, verá que la interfaz de usuario no aparece bien si el dispositivo es pequeño.

Para solucionar este problema, agregaremos la etiqueta META `viewport`:
1. Abra el archivo `./public/index.html`
1. Agregue una etiqueta META `viewport` al elemento `head` existente:

```html
<head>
    <!-- Add this line -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
```

1. Guarde el archivo.
1. Actualice el explorador del dispositivo. Ahora, la aplicación web debería aparecer correctamente. 

Este es un ejemplo de cómo algunos problemas no se detectan hasta que se realizan pruebas en los dispositivos en los que está previsto que se use una aplicación. Con VS Connected Environment, podrá iterar rápidamente por el código y validar los cambios en los dispositivos de destino.

## <a name="update-a-code-file"></a>Actualizar un archivo de código
Actualizar archivos de código del lado servidor requiere un poco más de trabajo, porque las aplicaciones Node.js deben reiniciarse.

1. En la ventana de terminal, presione `Ctrl+C` (para detener `vsce up`).
1. Abra el archivo de código `server.js` y edite el mensaje de saludo del servicio: 

```javascript
res.send('Hello from webfrontend running in Azure!');
```

3. Guarde el archivo.
1. Ejecute `vsce up` en la ventana de terminal. 

Esto vuelve a generar la imagen del contenedor e implementa de nuevo el gráfico de Helm. Vuelva a cargar la página del explorador para que los cambios de código surtan efecto.


Pero existe un *método todavía más rápido* para desarrollar código, que veremos en la siguiente sección. 
> [!div class="nextstepaction"]
> [Depurar un contenedor en Kubernetes](get-started-nodejs-04.md)
