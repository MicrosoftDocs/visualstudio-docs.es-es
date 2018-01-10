---
title: "Introducción a Node.js en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs: JavaScript
ms.workload: nodejs
ms.openlocfilehash: 80822e4f323621a97beb453118d7e0836ae9ea92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-nodejs-in-visual-studio"></a>Introducción a Node.js en Visual Studio
En este tutorial para el desarrollo de Node.js con Visual Studio, creará una sencilla aplicación web de Node.js, agregará código, explorará algunas características del IDE y ejecutará la aplicación. Si todavía no tiene instalado Visual Studio, puede descargarlo de forma gratuita en [esta página](http://www.visualstudio.com).  

## <a name="create-a-project"></a>Crear un proyecto
En primer lugar, creará un proyecto de aplicación web de Node.js.

1. Abra Visual Studio 2017.  

2. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto...**  

3. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **JavaScript** y después seleccione **Node.js**. En el panel central, elija **Aplicación básica de Azure Node.js Express 4** y después haga clic en **Aceptar**.   

     Si no ve la plantilla de proyecto **Aplicación básica de Azure Node.js Express 4**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de Node.js** y, después, haga clic en **Modificar**. 

    Visual Studio crea la solución y abre el proyecto. El archivo de proyecto **app.js** se abre en el editor (panel de la izquierda). Si no está familiarizado con los proyectos y soluciones de Visual Studio, vea [Inicio rápido: Usar Visual Studio para crear su primera aplicación de Node.js](../ide/quickstart-nodejs.md).

## <a name="add-some-code"></a>Agregar algo de código

1. En el Explorador de soluciones (el panel de la derecha), abra la carpeta views y después index.pug.

1. Reemplace el contenido por el marcado siguiente.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

1. En la carpeta routes, abra index.js.

1. Agregue el código siguiente antes de llamar a `router.get`:

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

1. Reemplace la función `router.get` por el código siguiente:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

1. Después de `data`, escriba `: get` e IntelliSense mostrará la función getData. Seleccione `getData`.

    ![Usar IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png) 

1. Quite la coma (`,`) antes de `"data"` y verá el resaltado de sintaxis de color verde en la expresión. Mueva el puntero sobre el resaltado de sintaxis.

    ![Ver error de sintaxis](../nodejs/media/tutorial-nodejs-syntax-checking.png) 

    La última línea de este mensaje indica que el intérprete de JavaScript esperaba una coma (`,`).

1. Haga clic en la pestaña **Lista de errores**.

    Verá la advertencia y una descripción junto con el nombre de archivo y número de línea.

    ![Ver lista de errores](../nodejs/media/tutorial-nodejs-error-list.png)

1. Corrija el código agregando la coma (`,`) antes de `"data"`.

## <a name="set-a-breakpoint"></a>Establecer un punto de interrupción

1. En index.js, haga clic en el margen interno de la izquierda antes de la siguiente línea de código para establecer un punto de interrupción:

    `res.render('index', { title: 'Express', "data": getData() });`

    Los puntos de interrupción son la característica más básica y esencial para una depuración confiable. Un punto de interrupción indica dónde Visual Studio debe suspender la ejecución de código para poder echar un vistazo a los valores de las variables o al comportamiento de la memoria, o determinar si se está ejecutando o no una bifurcación de código. 

    ![Establecer un punto de interrupción](../nodejs/media/tutorial-nodejs-set-breakpoint.png) 

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Seleccione el destino de depuración en la barra de herramientas de depuración.

    ![Seleccionar el destino de depuración](../nodejs/media/tutorial-nodejs-deploy-target.png) 

1. Presione **Ctrl+F5** para ejecutar la aplicación.

    El depurador se detiene en el punto de interrupción definido. Ahora, puede inspeccionar el estado de la aplicación.

1. Mueva el cursor sobre `getData` para ver sus propiedades en una información sobre datos

    ![Inspeccionar variables](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. Presione **F5** para continuar.

    La aplicación se abre en un explorador.

    En la ventana del explorador, verá "Express" como el título y "Bienvenido a Express" en el primer párrafo.

1. Haga clic en los botones para mostrar diferentes imágenes.

1. Abra la ventana interactiva de Node.js seleccionando **Vista > Otras ventanas > Ventana interactiva de Node.js**.

   ![Abrir la ventana interactiva de Node.js](../nodejs/media/tutorial-nodejs-interactive-window.png)  

    La ventana interactiva es compatible con todo lo que puede hacer en el código incluido el uso de instrucciones `require()`. En el código de la captura de pantalla siguiente se define una variable y se muestra la ubicación del intérprete de Node.js.

   ![Ventana interactiva de Node.js](../nodejs/media/tutorial-nodejs-interactive-window-example.png)  

1. Cierre el explorador web.  

## <a name="publish-to-azure-app-service"></a>Publicación en Azure App Service

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y seleccione **Publicar**.

   ![Publicación en Azure App Service](../nodejs/media/tutorial-nodejs-publish-to-azure.png)  

1. Seleccione **Microsoft Azure App Service**.

    En el cuadro de diálogo **App Service**, puede iniciar sesión en la cuenta de Azure y conectarse a las suscripciones de Azure existentes.

1. Siga los pasos restantes para seleccionar una suscripción, elegir o crear un grupo de recursos, elegir o crear un plan de App Service y, después, siga los pasos cuando se le solicite para publicar en Azure. Para obtener instrucciones detalladas, vea [Publicación en el sitio web de Azure con Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. En la ventana **Salida** se muestra el progreso de la implementación en Azure.

    Después de una implementación correcta, la aplicación se abre en un explorador que se ejecuta en Azure App Service. Haga clic en un botón para mostrar una imagen.

   ![Aplicación que se ejecuta en Azure App Service](../nodejs/media/tutorial-nodejs-running-in-azure.png)  

Enhorabuena por completar este tutorial.

## <a name="next-steps"></a>Pasos siguientes 

- Obtener más información sobre [Herramientas de Node.js para Visual Studio](https://github.com/Microsoft/nodejstools/wiki)  
- Más información sobre el [IDE de Visual Studio](../ide/visual-studio-ide.md)  