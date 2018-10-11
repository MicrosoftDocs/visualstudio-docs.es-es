---
title: 'Inicio rápido: Usar Visual Studio para crear la primera aplicación Vue.js'
description: En este inicio rápido se crea una aplicación Vue.js en Visual Studio mediante Herramientas de Node.js para Visual Studio
ms.date: 09/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-nodejs
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: b4e08b0ad058566bdd74522b94e0010d5cdc2f91
ms.sourcegitcommit: 000cdd1e95dd02e99a7c7c1a34c2f8fba6a632af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2018
ms.locfileid: "47168362"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Inicio rápido: Usar Visual Studio para crear la primera aplicación Vue.js

En esta introducción de entre cinco y diez minutos al entorno de desarrollo integrado (IDE) de Visual Studio, se crea una sencilla aplicación web Vue.js. Si todavía no ha instalado Visual Studio 2017, vaya a la página [Descargas de Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalarlo de forma gratuita.

> [!IMPORTANT]
> En este artículo se necesita la plantilla Vue.js, que está disponible a partir de Visual Studio 2017 versión 15.8.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar se crea un proyecto de aplicación web Vue.js.

1. Si todavía no tiene instalado el entorno de ejecución de Node.js, instale la versión LTS desde el sitio web de [Node.js](https://nodejs.org/en/download/).

    En general, Visual Studio detecta automáticamente el entorno de ejecución de Node.js instalado. Si no detecta un runtime instalado, puede configurar el proyecto para que haga referencia al runtime instalado en la página de propiedades (después de crear un proyecto, haga clic con el botón derecho en el nodo del proyecto y elija **Propiedades**).

1. Abra Visual Studio 2017.

1. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto**, en **JavaScript** > **Node.js** o **TypeScript** > **Node.js**, elija **Aplicación web de Vue.js básico** y luego escriba un nombre de proyecto y haga clic en **Aceptar**.

     ![Plantilla Vue.js](../javascript/media/vuejs-template.png)

    Visual Studio crea el nuevo proyecto. El nuevo proyecto se abre en el Explorador de soluciones (panel derecho).

     Si no ve la plantilla de proyecto **Aplicación web de Vue.js básico**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de Node.js** y, después, haga clic en **Modificar**.

     ![Carga de trabajo Node.js en el instalador de Visual Studio](../ide/media/quickstart-nodejs-workload.png)

    Visual Studio crea y la nueva solución y abre el proyecto.

1. Compruebe el progreso de la instalación de los paquetes de npm necesarios para la aplicación en la ventana Resultados (panel inferior).

1. En el Explorador de soluciones, abra el nodo **npm** y asegúrese de que todos los paquetes de npm que aparecen estén instalados.

    Si falta alguno (icono de signo de exclamación), haga clic con el botón derecho en el nodo **npm** y elija **Instalar los paquetes de NPM que faltan**.

## <a name="explore-the-ide"></a>Explorar el IDE

1. Eche un vistazo al panel de la derecha del **Explorador de soluciones**.

     ![Solución Vue.js](../javascript/media/vuejs-solution.png)

  - El proyecto está resaltado en negrita. Tiene el nombre que le asignó en el cuadro de diálogo **Nuevo proyecto**. En el disco, este proyecto se representa mediante un archivo .*njsproj* en la carpeta del proyecto.

  - En el nivel superior se encuentra una solución, que de forma predeterminada tiene el mismo nombre que el proyecto. Una solución, representada por un archivo .*sln* en el disco, es un contenedor de uno o más proyectos relacionados.

  - El nodo **npm** muestra todos los paquetes de npm instalados. Puede hacer clic con el botón derecho en el nodo npm para buscar e instalar paquetes npm mediante un cuadro de diálogo.

1. Si quiere instalar paquetes de npm o ejecutar comandos de Node.js desde un símbolo del sistema, haga clic con el botón derecho en el nodo del proyecto y elija **Abrir símbolo del sistema aquí**.

## <a name="add-a-vue-file-to-the-project"></a>Agregar un archivo .vue al proyecto

1. En el Explorador de soluciones, haga clic con el botón derecho en cualquier carpeta, como la carpeta *src*, y luego elija **Agregar** > **Nuevo elemento**.

1. Seleccione **Componente de archivo único de Vue para JavaScript** o **Componente de archivo único de Vue para TypeScript** y luego haga clic en **Agregar**.

    Visual Studio agrega el nuevo archivo al proyecto.

## <a name="build-the-project"></a>Compilar el proyecto

1. (Solo proyecto de TypeScript) En Visual Studio, elija **Compilar** > **Limpiar solución**.

1. Luego elija **Compilar** > **Compilar solución** para compilar el proyecto. Consulte la ventana **Resultados** para ver los resultados de la compilación.

    La plantilla de proyecto Vue.js usa el script de npm `build` al configurar un evento posterior a la compilación. Si quiere modificar este valor, abra el archivo de proyecto (*\<projectname\>.njsproj*) desde el Explorador de Windows y busque esta línea de código:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Presione **Ctrl**+**F5** (o seleccione **Depurar > Iniciar sin depurar**) para ejecutar la aplicación.

   En la consola, se ve un mensaje *Iniciando servidor de desarrollo*.

   Luego la aplicación se abre en un explorador.

   ![Aplicación Vue.js en ejecución en el explorador](../javascript/media/vuejs-running-app.png)

1. Cierre el explorador web.

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre el uso del IDE de Visual Studio con Vue.js. Si quiere profundizar más en sus capacidades, continúe con el tutorial que encontrará en la sección **Tutoriales** de la tabla de contenido.

## <a name="next-steps"></a>Pasos siguientes

- Repasar el [Tutorial para Node.js y Express](../nodejs/tutorial-nodejs.md)
- Repasar el [Tutorial para Node.js y React](../nodejs/tutorial-nodejs-with-react-and-jsx.md)
- [Deploy the app to Linux App Service](../javascript/publish-nodejs-app-azure.md) (Implementar la aplicación en App Service de Linux)