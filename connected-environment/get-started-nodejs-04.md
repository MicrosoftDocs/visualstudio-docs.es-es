---
title: 'Crear un entorno de desarrollo de Node.js con contenedores usando Kubernetes en la nube - Paso 4: Depurar un contenedor en Kubernetes | Microsoft Docs'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desarrollo rápido de Kubernetes con contenedores y microservicios en Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, contenedores
manager: douge
ms.openlocfilehash: 2d1ec5fe0436b394083a247faa4519505aa21ceb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introducción a Connected Environment con Node.js

Paso anterior: [Crear un contenedor de Node.js en Kubernetes](get-started-nodejs-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>Seleccionar la configuración de depuración de VSCE
1. Para abrir la vista Depurar, haga clic en el icono Depurar de la **barra de actividades** en el lateral de VS Code.
1. Seleccione **Iniciar programa (VSCE)** como configuración de depuración activa.

![](media/debug-configuration-nodejs.png)

> [!Note]
> Si no ve ningún comando de Connected Environment en la paleta de comandos, confirme que tiene [instalada la extensión de VS Code para Connected Environment](get-started-nodejs-01.md#get-kubernetes-debugging-for-vs-code).

## <a name="debug-the-container-in-kubernetes"></a>Depurar el contenedor en Kubernetes
Presione **F5** para depurar el código en Kubernetes.

Al igual que sucede con el comando `up`, el código se sincroniza con el entorno de desarrollo al iniciar la depuración y se genera e implementa un contenedor en Kubernetes. En esta ocasión, el depurador está asociado al contenedor remoto, por supuesto.

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

Establezca un punto de interrupción en un archivo de código del lado servidor, por ejemplo, dentro de `app.get('/api'...` en `server.js`. Actualice la página del explorador o presione el botón "Say It Again". Debería poder seleccionar el punto de interrupción y recorrer el código.

Tendrá acceso completo a la información de depuración tal y como lo haría si el código se ejecutara localmente, como las pilas de llamadas, las variables locales, la información de excepciones, etc.

## <a name="edit-code-and-refresh-the-debug-session"></a>Editar el código y actualizar la sesión de depuración
Con el depurador activo, realice una modificación de código; por ejemplo, vamos a cambiar otra vez el mensaje de saludo:

```javascript
app.get('/api', function (req, res) {
    res.send('**** Hello from webfrontend running in Azure! ****');
});
```

Guarde el archivo y, en el **panel Acciones de depuración**, haga clic en el botón **Actualizar**. 

![](media/debug-action-refresh-nodejs.png)

En lugar de volver a generarse e implementarse una nueva imagen de contenedor cada vez que se realicen modificaciones del código (lo que suele conllevar mucho tiempo), Connected Environment reiniciará el proceso de Node.js entre las sesiones de depuración para lograr un bucle de edición y depuración más rápido.

Actualice la aplicación web en el explorador, o presione el botón*Say It Again*. Debería ver el mensaje personalizado en la interfaz de usuario.


## <a name="use-nodemon-to-develop-even-faster"></a>Usar NodeMon para desarrollar aún más rápidamente
*Nodemon* es una conocida herramienta que los desarrolladores de Node.js usan para desarrollar rápidamente. En lugar de reiniciar manualmente el proceso de Node cada vez que se realice una modificación de código del lado servidor, lo que los programadores hacen a menudo es configurar el proyecto de Node de forma que *nodemon* supervise los cambios de archivo y reinicie automáticamente el proceso de servidor. Según esta forma de trabajar, el desarrollador simplemente actualiza el explorador después de realizar una modificación de código.

La finalidad de Connected Environment reside en que se puedan usar los mismos flujos de trabajo de desarrollo productivos que se emplean al desarrollar de forma local. Para ilustrar esto, el proyecto de ejemplo `webfrontend` se ha configurado para usar *nodemon* (está configurado como una dependencia de desarrollo en `package.json`).

Intente lo siguiente:
1. Detenga el depurador de VS Code.
1. Haga clic en el icono Depurar de la **barra de actividades** en el lateral de VS Code. 
1. Seleccione **Asociar (VSCE)** como configuración de depuración activa.
1. Presione F5.

En esta configuración, el contenedor está definido para iniciar *nodemon*. Así, cuando se realicen modificaciones de código de servidor, *nodemon* reiniciará automáticamente el proceso de Node, al igual que ocurre cuando se desarrolla localmente. 
1. Modifique el mensaje de saludo en `server.js` y guarde el archivo.
1. Actualice el explorador o haga clic en el botón *Say It Again* para ver los cambios aplicados.

**Ya dispone de un método para iterar rápidamente por el código y depurar directamente en Kubernetes.** Veamos ahora cómo se puede crear un segundo contenedor y llamarlo.

> [!div class="nextstepaction"]
> [Llamar a un servicio que se ejecuta en un contenedor aparte](get-started-nodejs-05.md)

