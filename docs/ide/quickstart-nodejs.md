---
title: Creación de la primera aplicación Node.js
ms.custom:
- vs-acquisition
- SEO-VS-2020
description: En este tutorial rápido, se crea una aplicación Node.js en Visual Studio.
ms.date: 03/25/2021
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0c44bfcfe1e7f07f83ca2b7dbb8b0604f5efe5f1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386168"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>Inicio rápido: Creación de la primera aplicación Node.js con Visual Studio

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, con una duración de entre 5 y 10 minutos, creará una sencilla aplicación web de Node.js.

## <a name="prerequisites"></a>Prerrequisitos

Antes de comenzar, instale Visual Studio y configure el entorno de Node.js.

### <a name="install-visual-studio"></a>Instalar Visual Studio

::: moniker range=">=vs-2019"
Si todavía no ha instalado Visual Studio 2019, vaya a la página [Descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.
::: moniker-end
::: moniker range="vs-2017"
Si todavía no ha instalado Visual Studio 2017, vaya a la página [Descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.
::: moniker-end

### <a name="set-up-your-nodejs-environment"></a>Configuración del entorno de Node.js

Visual Studio puede ayudar a configurar el entorno, incluida la instalación de herramientas comunes con el desarrollo de Node.js.

1. En Visual Studio, vaya a **Herramientas** > **Obtener herramientas y características**.

1. En la Instalador de Visual Studio, elija la carga de trabajo **Desarrollo de Node.js** y seleccione **Modificar** para descargarla e instalarla.

    ![Carga de trabajo de Node.js en el Instalador de Visual Studio](../ide/media/quickstart-nodejs-workload.png)

1. Instale la versión LTS del [entorno de ejecución de Node.js](https://nodejs.org/en/download/). Se recomienda la versión LTS para obtener la mejor compatibilidad con bibliotecas y marcos externos.

    Aunque Node.js se ha creado para arquitecturas de 32 y 64 bits, el instalador de Node.js solo admite una versión instalada a la vez.

1. Si Visual Studio no detecta el entorno de ejecución instalado (normalmente lo hace), configure el proyecto para que le haga referencia:

   1. Después de [crear el proyecto](#create-your-app-project), haga clic con el botón derecho en el nodo del proyecto.

   1. Seleccione **Propiedades** y establezca la **Ruta de acceso de Node.exe**. Puede usar una instalación global de Node.js, o bien especificar la ruta de acceso a un intérprete local en cada uno de los proyectos de Node.js.

## <a name="create-your-app-project"></a>Creación del proyecto de aplicación

1. Si todavía no lo ha hecho, instale la versión LTS del [entorno de ejecución de Node.js](https://nodejs.org/en/download/). Para más información, consulte la sección los [requisitos previos](#prerequisites).

1. Abra Visual Studio.

1. Cree un nuevo proyecto.

    ::: moniker range=">=vs-2019"

    1. Presione **Esc** para cerrar la ventana de inicio.

    1. Presione **Ctrl + Q** para abrir el cuadro de búsqueda y escriba **Node.js**.

    1. Elija **Aplicación web en blanco de Node.js (JavaScript)** . En el cuadro de diálogo, seleccione **Crear**.

    ::: moniker-end

    ::: moniker range="vs-2017"
    1. En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.

    1. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **JavaScript** y elija **Node.js**.

    1. En el panel central, elija **Aplicación web en blanco de Node.js** y seleccione **Aceptar**.

    ::: moniker-end
    
    Si no ve la plantilla de proyecto **Aplicación web en blanco de Node.js**, debe agregar la carga de trabajo **Desarrollo de Node.js**. Para obtener instrucciones detalladas, vea los [requisitos previos](#prerequisites).

    Visual Studio crea y abre el proyecto. El archivo *server.js* del proyecto se abre en el editor de la izquierda.

## <a name="explore-the-ide"></a>Explorar el IDE

1. En el panel de la derecha, observe el **Explorador de soluciones**.

   ![Explorador de soluciones](../ide/media/quickstart-nodejs-solution-explorer.png)

   - El proyecto se resalta en negrita con el nombre proporcionado al configurarlo. En el disco, este proyecto se representa mediante un archivo *.njsproj* en la carpeta del proyecto.

   - En el nivel superior se encuentra una solución, que de forma predeterminada tiene el mismo nombre que el proyecto. Una solución, representada por un archivo *.sln* en el disco, es un contenedor para uno o más proyectos relacionados.

   - En el nodo **npm** se muestran todos los paquetes npm instalados. Puede hacer clic con el botón derecho en el nodo npm para buscar e instalar paquetes npm mediante un cuadro de diálogo.

1. Si quiere instalar paquetes npm o comandos de Node.js desde un símbolo del sistema, haga clic con el botón derecho en el nodo del proyecto y seleccione **Abrir símbolo del sistema aquí**.

   ![Símbolo del sistema de Node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. Si quiere probar la navegación al código fuente, desde el archivo *server.js* abierto, seleccione **http.createServer** y presione **F12** o elija **Ir a definición** en el menú contextual (clic con el botón derecho). Este comando le lleva a la definición de la función `createServer` en *http.d.ts*.

   ![Menú contextual Ir a definición](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Vuelva a *server.js* y busque esta línea de código: `res.end('Hello World\n');`. Modifique el código de esta forma:

    `res.end('Hello World\n' + res.connection.`

    Al escribir **connection.** , IntelliSense proporciona opciones para autocompletar la entrada de código.

   ![Autocompletar de IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Elija **localPort** y escriba **);** para completar la instrucción:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-app"></a>Ejecución de la aplicación

1. Presione **Ctrl+F5** (o seleccione **Depurar** > **Iniciar sin depurar**) para ejecutar la aplicación. 
 
   La aplicación se abre en un explorador.

1. En el explorador, compruebe que ve un mensaje "Hola mundo" y el número de puerto local.

Enhorabuena. Ha creado una aplicación Node.js sencilla con Visual Studio. Para profundizar más, continúe en la sección **Tutoriales** de la tabla de contenido.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Deploy the app to Linux App Service](../javascript/publish-nodejs-app-azure.md) (Implementar la aplicación en App Service de Linux)

> [!div class="nextstepaction"]
> [Tutorial para Node.js y Express](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Tutorial para Node.js y React](../javascript/tutorial-nodejs-with-react-and-jsx.md)
