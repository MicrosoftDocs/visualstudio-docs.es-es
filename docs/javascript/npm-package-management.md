---
title: Administrar paquetes de npm
description: Visual Studio ayuda a administrar paquetes mediante el administrador de paquetes de Node.js (npm)
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: fed525f62466d096aa7868cc57c7fd7c75bf46f8
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2020
ms.locfileid: "91781032"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Administrar paquetes de npm en Visual Studio

npm permite instalar y administrar paquetes para su uso en las aplicaciones de Node.js. Visual Studio facilita la interacción con npm y la emisión de comandos de npm a través de la interfaz de usuario o directamente. Si no está familiarizado con npm y quiere obtener más información, vaya a la [documentación de npm](https://docs.npmjs.com/).

La integración de Visual Studio con npm es diferente en función del tipo de proyecto.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Abrir carpeta (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm espera la carpeta *node_modules* y *package.json* en la raíz del proyecto. Si la estructura de carpetas de la aplicación es diferente, debe cambiarla para poder administrar paquetes de npm con Visual Studio.

## <a name="nodejs-projects"></a>Proyectos Node.js

Para los proyectos de Node.js, puede realizar las tareas siguientes:
* [Instalar paquetes desde el Explorador de soluciones](#npmInstallWindow)
* [Administrar paquetes instalados desde el Explorador de soluciones](#solutionExplorer)
* [Usar el comando `.npm` en la ventana interactiva de Node.js](#interactive)

Estas características funcionan conjuntamente y se sincronizan con el sistema del proyecto y el archivo *package.json* del proyecto.

### <a name="prerequisites"></a>Requisitos previos

Para agregar compatibilidad con npm al proyecto, necesita tener instalados el entorno de ejecución de Node.js y la carga de trabajo **Desarrollo de Node.js**. Para conocer los pasos detallados, consulte [Crear un proyecto de Node.js](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json).

> [!NOTE]
> Para los proyectos de Node.js existentes, use la plantilla de solución **A partir del código existente de Node.js** o el tipo de proyecto [Abrir carpeta (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) a fin de permitir npm en el proyecto.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> Instalación de paquetes desde el Explorador de soluciones (Node.js)

En el caso de los proyectos Node.js, la manera más sencilla de instalar paquetes de npm es a través de la ventana de instalación de paquetes de npm. Para acceder a esta ventana, haga clic con el botón derecho en el nodo **npm** del proyecto y seleccione **Instalar nuevos paquetes de NPM**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Instalación del nuevo paquete de npm desde el Explorador de soluciones" border="true":::

En esta ventana puede buscar un paquete, especificar opciones e instalar.

![Búsqueda del paquete de npm](../javascript/media/search-package.png)

* **Tipo de dependencia**: elija entre paquetes **Estándar**, **Desarrollo** y **Opcional**. Estándar especifica que el paquete es una dependencia en tiempo de ejecución, mientras que Desarrollo especifica que el paquete solo es necesario durante el desarrollo.
* **Agregar a package.json** (recomendado). Esta opción configurable está en desuso.
* **Versión seleccionada**: seleccione la versión del paquete que quiere instalar.
* **Otros argumentos de NPM**: especifique otros argumentos estándar de npm. Por ejemplo, puede escribir un valor de versión como `@~0.8` para instalar una versión determinada que no esté disponible en la lista de versiones.

Se puede ver el progreso de la instalación en la salida de **npm** de la ventana **Resultados**. Esto puede llevar algo de tiempo.

![Salida de npm](../javascript/media/npm-output.png)

> [!TIP]
> Puede buscar paquetes con ámbito si antepone el ámbito que le interesa a la consulta de búsqueda, por ejemplo, escriba `@types/mocha` para buscar archivos de definición de TypeScript para Mocha. Además, al instalar las definiciones de tipos de TypeScript, se puede especificar la versión de TypeScript de destino agregando `@ts2.6` al campo del argumento de npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Administración de paquetes instalados en el Explorador de soluciones (Node.js)

Los paquetes de npm se muestran en el Explorador de soluciones. Las entradas del nodo **npm** imitan las dependencias del archivo *package.json*.

![Búsqueda del paquete de npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Estado del paquete

* ![Paquete instalado](../javascript/media/installed-npm.png) - Instalado y en la lista de package.json
* ![Paquete extraño](../javascript/media/extraneous-npm.png): instalado, pero sin aparecer de forma explícita en package.json
* ![Paquete que falta](../javascript/media/missing-npm.png) - No instalado, pero en la lista de package.json

::: moniker range=">=vs-2019"
Haga clic con el botón derecho en el nodo **npm** para realizar una de las siguientes acciones:

* **Instalar nuevos paquetes de npm**: abre la interfaz de usuario para instalar nuevos paquetes.
* **Instalar los paquetes de npm**: ejecuta el comando de instalación de npm para instalar todos los paquetes enumerados en *package.json* (ejecuta `npm install`).
* **Actualizar los paquetes de npm**: actualiza los paquetes a las versiones más recientes, según el rango de Versionamiento Semántico (SemVer) que se haya especificado en *package.json*. (ejecuta `npm update --save`). Los rangos de SemVer se especifican normalmente mediante "~" o "^". Para obtener más información, consulte [Configuración de package.json](../javascript/configure-packages-with-package-json.md).

Haga clic con el botón derecho en el nodo de un paquete para realizar una de las siguientes acciones:

* **Instalar los paquetes de npm**: ejecuta el comando de instalación de npm para instalar la versión del paquete enumerada en *package.json* (ejecuta `npm install`).
* **Actualizar los paquetes de npm**: actualiza los paquetes a la versión más reciente, según el rango de SemVer que se haya especificado en *package.json*. (ejecuta `npm update --save`). Los rangos de SemVer se especifican normalmente mediante "~" o "^".
* **Desinstalar los paquetes de npm**: desinstala el paquete y lo quita de *package.json* (ejecuta `npm uninstall --save`).
::: moniker-end
::: moniker range="vs-2017"
Haga clic con el botón derecho en el nodo de un paquete o en el nodo **npm** para realizar una de las siguientes acciones:
* **Instalar los paquetes que faltan** que aparecen en *package.json*
* **Actualizar paquetes de npm** a la versión más reciente
* **Desinstalar un paquete** y quitarlo de *package.json*
::: moniker-end

>[!NOTE]
> Para obtener ayuda para resolver problemas con paquetes de npm, consulte [Solución de problemas](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Uso del comando .npm en la ventana interactiva de Node.js (Node.js)

También puede usar el comando `.npm` en la ventana interactiva de Node.js para ejecutar comandos de npm. Para abrir la ventana, haga clic con el botón derecho en el Explorador de soluciones y elija **Abrir la ventana interactiva de Node.js**.

En la ventana, puede usar comandos como los siguientes para instalar un paquete:

`.npm install azure@4.2.3`

 > [!Tip]
 > De forma predeterminada, npm se ejecuta en el directorio de inicio del proyecto. Si tiene varios proyectos en la solución, especifique el nombre o la ruta de acceso del proyecto entre paréntesis.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Si el proyecto no contiene un archivo package.json, use `.npm init -y` para crear un archivo package.json con entradas predeterminadas.

 ## <a name="aspnet-core-projects"></a>Proyectos de ASP.NET Core

En el caso de proyectos como los de ASP.NET Core, se puede integrar la compatibilidad con npm en el proyecto y usar npm para instalar paquetes.
* [Incorporación de compatibilidad con npm a un proyecto](#npmAdd)
* [Instalación de paquetes mediante package.json](#npmInstallPackage)

>[!NOTE]
> En el caso de los proyectos de ASP.NET Core, también se puede usar el [Administrador de bibliotecas](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) o yarn, en lugar de npm, para instalar los archivos JavaScript y CSS del lado cliente.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Incorporación de compatibilidad con npm a un proyecto (ASP.NET Core)

Si el proyecto aún no incluye un archivo *package.json*, se puede agregar compatibilidad para habilitar npm incorporando un archivo *package.json* al proyecto.

1. Si no tiene Node.js instalado, le recomendamos instalar la versión de LTS desde el sitio web de [Node.js](https://nodejs.org/en/download/) para ofrecer una mejor compatibilidad con los marcos y las bibliotecas externos.

   npm requiere Node.js.

1. Para agregar el archivo *package.json*, haga clic con el botón derecho en el proyecto en el Explorador de soluciones y elija **Agregar** > **Nuevo elemento**. Elija el **Archivo de configuración de npm**, use el nombre predeterminado y haga clic en **Agregar**.

   ![Incorporación de package.json al proyecto](../javascript/media/npm-add-package-json.png)

   Si no ve el archivo de configuración de npm en la lista, las herramientas de desarrollo de Node.js no están instaladas. Puede usar el Instalador de Visual Studio para agregar la carga de trabajo **Desarrollo de Node.js**. A continuación, repita el paso anterior.

1. Incluya uno o más paquetes de npm en las secciones `dependencies` o `devDependencies` de *package.json*. Por ejemplo, se podría agregar lo siguiente al archivo:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Cuando se guarda el archivo, Visual Studio agrega el paquete en el nodo **Dependencias/npm** del Explorador de soluciones. Si no se ve el nodo, haga clic con el botón derecho en **package.json** y elija **Restaurar paquetes**.

>[!NOTE]
> En algunos escenarios, es posible que el Explorador de soluciones no muestre el estado correcto de los paquetes de npm instalados. Para más información, consulte [Solución de problemas](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Instalación de paquetes mediante package.json (ASP.NET Core)

En el caso de los proyectos con npm incluido, se pueden configurar paquetes de npm mediante `package.json`. Haga clic con el botón derecho en el nodo de npm en el Explorador de soluciones y elija **Abrir package.json**.

![Búsqueda del paquete de npm](../javascript/media/npm-add-package.png)

IntelliSense en *package.json* ayuda a seleccionar una versión determinada de un paquete de npm.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Instalación del nuevo paquete de npm desde el Explorador de soluciones" border="true":::

Cuando se guarda el archivo, Visual Studio agrega el paquete en el nodo **Dependencias/npm** del Explorador de soluciones. Si no se ve el nodo, haga clic con el botón derecho en **package.json** y elija **Restaurar paquetes**.

La instalación de un paquete puede tardar varios minutos. Para comprobar el progreso de la instalación del paquete, cambie a la salida de **npm** en la ventana **Resultados**.

![Salida de npm](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Solución de problemas con paquetes de npm

* npm requiere Node.js. Si no lo tiene instalado, le recomendamos instalar la versión de LTS desde el sitio web de [Node.js](https://nodejs.org/en/download/) para ofrecer una mejor compatibilidad con los marcos y las bibliotecas externos.

* Para los proyectos de Node.js, deberá tener instalada la carga de trabajo **Desarrollo de Node.js** con el fin de obtener compatibilidad con npm.

* En algunos escenarios, es posible que el Explorador de soluciones no muestre el estado correcto de los paquetes de npm instalados. Esto se debe a un error conocido que se describe [aquí](https://github.com/aspnet/Tooling/issues/479). Por ejemplo, es posible que el paquete aparezca como no instalado cuando sí que lo está. En la mayoría de los casos, se puede actualizar el Explorador de soluciones eliminando *package.json*, reiniciando Visual Studio y agregando de nuevo el archivo *package.json*, tal como se ha descrito anteriormente en este artículo. También puede usar la ventana de salida de npm para comprobar el estado de instalación al instalar paquetes.

* Si ve algún error al compilar la aplicación o al transpilar el código TypeScript, compruebe las incompatibilidades del paquete de npm como posible fuente de errores. Para poder identificar los errores, compruebe la ventana de salida de npm al instalar los paquetes, tal y como se describe anteriormente en este artículo. Por ejemplo, si una o varias de las versiones del paquete de npm están en desuso y generan un error, deberá instalar una versión más reciente para corregir los errores. Para obtener información sobre cómo usar *package.json* para controlar las versiones del paquete de npm, consulte [package.json configuration](../javascript/configure-packages-with-package-json.md) (Configuración de package.json).
