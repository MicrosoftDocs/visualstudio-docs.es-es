---
title: 'Inicio rápido: Creación de la primera aplicación Vue.js'
description: En este inicio rápido se crea una aplicación Vue.js en Visual Studio mediante Herramientas de Node.js para Visual Studio
ms.custom: ''
ms.date: 10/31/2019
ms.topic: quickstart
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ad2892ab7c605ba25902ac2c4c24e68236a5d740
ms.sourcegitcommit: 00e16b9afe6b22ba0591e4d0d92690544e6d4357
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2021
ms.locfileid: "105616979"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Inicio rápido: Uso de Visual Studio para crear la primera aplicación Vue.js

En esta introducción de entre cinco y diez minutos al entorno de desarrollo integrado (IDE) de Visual Studio, se crea una sencilla aplicación web Vue.js.

> [!IMPORTANT]
> En este artículo se necesita la plantilla Vue.js, que está disponible a partir de Visual Studio 2017 versión 15.8.

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado Visual Studio y la carga de trabajo de desarrollo de Node.js.

    ::: moniker range=">=vs-2019"
    Si todavía no ha instalado Visual Studio 2019, vaya a la página [Descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/) para instalarlo de forma gratuita.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Si todavía no ha instalado Visual Studio 2017, vaya a la página [Descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/) para instalarlo de forma gratuita.
    ::: moniker-end

    Si tiene que instalar la carga de trabajo pero ya tiene Visual Studio, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de Node.js** y, después, haga clic en **Modificar**.

    ![Carga de trabajo Node.js en el instalador de Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Debe tener instalado el runtime de Node.js.

    Si no lo tiene instalado, se recomienda instalar la versión de LTS desde el sitio web de [Node.js](https://nodejs.org/en/download/) para ofrecer una mejor compatibilidad con los marcos y las bibliotecas externos. Node.js se ha compilado para arquitecturas de 32 y 64 bits. Las herramientas de Node.js en Visual Studio, incluidas en la carga de trabajo de Node.js, admiten ambas versiones. Solo se requiere una y el instalador de Node.js solo admite que se instale una a la vez.
    
    En general, Visual Studio detecta automáticamente el entorno de ejecución de Node.js instalado. Si no detecta un entorno de ejecución instalado, puede configurar el proyecto para que haga referencia al entorno de ejecución instalado en la página de propiedades (después de crear un proyecto, haga clic con el botón derecho en el nodo del proyecto, elija **Propiedades** y establezca la **ruta de acceso de Node.exe**). Puede usar una instalación global de Node.js o puede especificar la ruta de acceso a un intérprete local en cada uno de los proyectos de Node.js. 

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar se crea un proyecto de aplicación web Vue.js.

1. Si todavía no tiene instalado el entorno de ejecución de Node.js, instale la versión LTS desde el sitio web de [Node.js](https://nodejs.org/en/download/).

    Para más información, consulte la sección de requisitos previos.

1. Abra Visual Studio.

1. Cree un nuevo proyecto.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **Vue.js básico**, elija **Aplicación web de Vue.js básico** (JavaScript o TypeScript). En el cuadro de diálogo que se muestra, escriba el nombre **basic-vuejs** y después elija **Crear**.

    ![Plantilla Vue.js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, expanda **JavaScript** o **TypeScript** y elija **Node.js**. En el panel central, elija **Aplicación web Basic Vue.js**, escriba el nombre **basic-vuejs** y después haga clic en **Aceptar**.

    ![Plantilla Vue.js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Si no ve la plantilla de proyecto **Aplicación web de Vue.js básico**, debe agregar la carga de trabajo **Desarrollo de Node.js**. Para instrucciones detalladas, consulte los [Requisitos previos](#prerequisites).

    Visual Studio crea el nuevo proyecto. El nuevo proyecto se abre en el Explorador de soluciones (panel derecho).

1. Compruebe el progreso de la instalación de los paquetes de npm necesarios para la aplicación en la ventana Resultados (panel inferior).

1. En el Explorador de soluciones, abra el nodo **npm** y asegúrese de que todos los paquetes de npm que aparecen estén instalados.

    Si falta alguno (icono de signo de exclamación), haga clic con el botón derecho en el nodo **npm** y elija **Instalar los paquetes de NPM que faltan**.

## <a name="explore-the-ide"></a>Explorar el IDE

1. Eche un vistazo al panel de la derecha del **Explorador de soluciones**.

     ![Solución Vue.js](../javascript/media/vuejs-solution.png)

   - El proyecto está resaltado en negrita. Tiene el nombre que le asignó en el cuadro de diálogo **Nuevo proyecto**. En el disco, este proyecto se representa mediante un archivo .*njsproj* en la carpeta del proyecto.

   - En el nivel superior se encuentra una solución, que de forma predeterminada tiene el mismo nombre que el proyecto. Una solución, representada por un archivo .*sln* en el disco, es un contenedor de uno o más proyectos relacionados.

   - El nodo **npm** muestra todos los paquetes de npm instalados. Puede hacer clic con el botón derecho en el nodo npm para buscar e instalar paquetes npm mediante un cuadro de diálogo.

2. Si quiere instalar paquetes de npm o ejecutar comandos de Node.js desde un símbolo del sistema, haga clic con el botón derecho en el nodo del proyecto y elija **Abrir símbolo del sistema aquí**.

## <a name="add-a-vue-file-to-the-project"></a>Agregar un archivo .vue al proyecto

1. En el Explorador de soluciones, haga clic con el botón derecho en cualquier carpeta, como la carpeta *src/components*, y luego elija **Agregar** > **Nuevo elemento**.

1. Seleccione **Componente de archivo único de Vue para JavaScript** o **Componente de archivo único de Vue para TypeScript** y luego haga clic en **Agregar**.

    Visual Studio agrega el nuevo archivo al proyecto.

## <a name="build-the-project"></a>Compilar el proyecto

::: moniker range=">=vs-2019"
1. Luego, elija **Compilar** > **Compilar solución** para compilar el proyecto.

1. Consulte la ventana **Resultados** para ver los resultados de la compilación y elija **Compilar** en la lista **Mostrar salida de**.
::: moniker-end
::: moniker range="vs-2017"
1. Solo para el proyecto de TypeScript, en Visual Studio, elija **Compilar** > **Limpiar solución**.

1. Luego, elija **Compilar** > **Compilar solución** para compilar el proyecto.

1. Consulte la ventana **Resultados** para ver los resultados de la compilación y elija **Compilar** en la lista **Mostrar salida de**.
::: moniker-end

En la plantilla de proyecto Vue.js de JavaScript (y las versiones anteriores de la plantilla de TypeScript) se usa el script `build` de npm mediante la configuración de un evento posterior a la compilación. Si quiere modificar este valor, abra el archivo del proyecto ( *\<projectname\>.njsproj*) desde el Explorador de Windows y busque esta línea de código:

```xml
<PostBuildEvent>npm run build</PostBuildEvent>
```

## <a name="run-the-application"></a>Ejecutar la aplicación

1. Presione **Ctrl**+**F5** (o seleccione **Depurar > Iniciar sin depurar**) para ejecutar la aplicación.

   En la consola, se ve un mensaje *Iniciando servidor de desarrollo*.

   Luego la aplicación se abre en un explorador.
   
   Si no ve la aplicación en ejecución, actualice la página.

   ![Aplicación Vue.js en ejecución en el explorador](../javascript/media/vuejs-running-app.png)

1. Cierre el explorador web.

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre el uso del IDE de Visual Studio con Vue.js. Si quiere profundizar más en sus funcionalidades, continúe con el tutorial que encontrará en la sección **Tutoriales** de la tabla de contenido.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Creación de una aplicación Vue.js](create-application-with-vuejs.md)

> [!div class="nextstepaction"]
> [Deploy the app to Linux App Service](../javascript/publish-nodejs-app-azure.md) (Implementar la aplicación en App Service de Linux)