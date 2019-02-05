---
title: 'Inicio rápido: Uso de Visual Studio para crear su primera aplicación Node.js'
description: En este tutorial rápido, se crea una aplicación Node.js en Visual Studio.
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-nodejs
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f11396527208862428483744bc1ac3b02583f4c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955497"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Inicio rápido: Uso de Visual Studio para crear su primera aplicación Node.js

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, con una duración de entre 5 y 10 minutos, creará una sencilla aplicación web de Node.js. Si todavía no ha instalado Visual Studio 2017, vaya a la página [Descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, creará un proyecto de aplicación web de Node.js.

1. Si todavía no tiene instalado el entorno de ejecución de Node.js, instale la versión LTS desde el sitio web de [Node.js](https://nodejs.org/en/download/).

    En general, Visual Studio detecta automáticamente el entorno de ejecución de Node.js instalado. Si no detecta un runtime instalado, puede configurar el proyecto para que haga referencia al runtime instalado en la página de propiedades (después de crear un proyecto, haga clic con el botón derecho en el nodo del proyecto y elija **Propiedades**).

1. Abra Visual Studio 2017.

1. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **JavaScript** y después seleccione **Node.js**. En el panel central, elija **Aplicación web en blanco de Node.js** y después haga clic en **Aceptar**.

     Si no ve la plantilla de proyecto **Aplicación web en blanco de Node.js**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de Node.js** y, después, haga clic en **Modificar**.

     ![Carga de trabajo Node.js en el instalador de Visual Studio](../ide/media/quickstart-nodejs-workload.png)

    Después de elegir la plantilla **aplicación web de Node.js en blanco** y de hacer clic en **Aceptar**, Visual Studio crea la solución y abre el proyecto. *server.js* se abre en el editor en el panel izquierdo.

## <a name="explore-the-ide"></a>Explorar el IDE

1. Eche un vistazo al panel de la derecha del **Explorador de soluciones**.

   ![Explorador de soluciones](../ide/media/quickstart-nodejs-solution-explorer.png)

   - El proyecto está resaltado en negrita. Tiene el nombre que le asignó en el cuadro de diálogo **Nuevo proyecto**. En el disco, este proyecto se representa mediante un archivo *.njsproj* en la carpeta del proyecto.

   - En el nivel superior se encuentra una solución, que de forma predeterminada tiene el mismo nombre que el proyecto. Una solución, representada por un archivo *.sln* en el disco, es un contenedor para uno o más proyectos relacionados.

   - En el nodo npm se muestran todos los paquetes npm instalados. Puede hacer clic con el botón derecho en el nodo npm para buscar e instalar paquetes npm mediante un cuadro de diálogo.

1. Si quiere instalar paquetes npm o comandos de Node.js desde un símbolo del sistema, haga clic con el botón derecho en el nodo del proyecto y seleccione **Abrir símbolo del sistema aquí**.

   ![Símbolo del sistema de Node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. En el archivo *server.js* en el editor (panel de la izquierda), elija `http.createServer` y, después, presione **F12** o seleccione **Ir a definición** en el menú contextual (clic con el botón derecho). Este comando le lleva a la definición de la función `createServer` en *index.d.ts*.

   ![Menú contextual Ir a definición](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Vuelva a *server.js*. Después, coloque el cursor al final de la cadena en esta línea de código, `res.end('Hello World\n');`, y modifíquela para que tenga el aspecto siguiente:

    `res.end('Hello World\n' + res.connection.`

    Donde escribe `connection.`, IntelliSense proporciona opciones para autocompletar la entrada de código.

   ![Autocompletar de IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Seleccione **localPort** y, después, escriba `);` para completar la instrucción para que tenga el aspecto siguiente:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Presione **Ctrl**+**F5** (o seleccione **Depurar > Iniciar sin depurar**) para ejecutar la aplicación. La aplicación se abre en un explorador.

1. En la ventana del explorador, verá "Hello World" más el número de puerto local.

1. Cierre el explorador web.

Enhorabuena, ha completado este Inicio rápido en el que ha empezado a usar el IDE de Visual Studio y Node.js. Si quiere profundizar más en sus funcionalidades, continúe con el tutorial que encontrará en la sección **Tutoriales** de la tabla de contenido.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Deploy the app to Linux App Service](../javascript/publish-nodejs-app-azure.md) (Implementar la aplicación en App Service de Linux)

- [Tutorial para Node.js y Express](../javascript/tutorial-nodejs.md)
- [Tutorial para Node.js y React](../javascript/tutorial-nodejs-with-react-and-jsx.md)