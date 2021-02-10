---
title: Compilar y generar código TypeScript con npm
description: Aprenda a agregar compatibilidad con TypeScript a sus proyectos de Visual Studio mediante el administrador de paquetes de nodos (npm).
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 966b08a912a7bab59998daf39590a6fd46920eb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969534"
---
# <a name="compile-typescript-code-nodejs"></a>Compilar código TypeScript (Node.js)

Puede agregar compatibilidad con TypeScript a los proyectos mediante TypeScript SDK, que está disponible de forma predeterminada en el instalador de Visual Studio o mediante npm. Para los proyectos desarrollados en Visual Studio 2019, le animamos a usar los paquetes npm de TypeScript para una mayor portabilidad entre distintas plataformas y entornos.

En el caso de los proyectos de ASP.NET Core, se recomienda que use el [paquete NuGet](../javascript/compile-typescript-code-nuget.md) en su lugar.

## <a name="add-typescript-support-using-npm"></a>Agregar compatibilidad con TypeScript con npm

El [paquete npm de TypeScript](https://www.npmjs.com/package/typescript) agrega compatibilidad con TypeScript. Cuando se instala el paquete npm de TypeScript 2.1 o posterior en el proyecto, se carga la versión correspondiente del servicio de lenguaje TypeScript en el editor.

1. [Siga las instrucciones](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json) para instalar la carga de trabajo de desarrollo de Node.js y el runtime de Node.js.

   Para obtener la integración más sencilla con Visual Studio, cree el proyecto mediante una de las plantillas de TypeScript de Node.js, como la plantilla Aplicación web en blanco de Node.js. De lo contrario, use una plantilla de JavaScript de Node.js incluida con Visual Studio y siga las instrucciones que se indican aquí, o bien use un proyecto [Abrir carpeta](../javascript/develop-javascript-code-without-solutions-projects.md).

1. Si el proyecto aún no lo incluye, instale el [paquete npm de TypeScript](https://www.npmjs.com/package/typescript).

   En el Explorador de soluciones (panel derecho), abra *package.json* en la raíz del proyecto. Los paquetes enumerados corresponden a los paquetes del nodo npm del Explorador de soluciones. Para más información, vea [Administrar paquetes de npm](../javascript/npm-package-management.md).

   En el caso de un proyecto de Node.js, puede instalar el paquete de npm de TypeScript mediante la línea de comandos o el IDE. Para realizar la instalación mediante el IDE, haga clic con el botón derecho en el nodo npm del Explorador de soluciones, elija **Instalar nuevos paquetes de npm**, busque **TypeScript** e instale el paquete.

   Active la opción **npm** de la ventana **Resultados** para ver el progreso de la instalación del paquete. El paquete instalado se muestra en el nodo **npm** del Explorador de soluciones.

1. Si el proyecto aún no lo incluye, agregue un archivo *.tsconfig* a la raíz del proyecto. Para agregar el archivo, haga clic con el botón derecho en el nodo de proyecto y elija **Agregar > Nuevo elemento**. Elija el **archivo de configuración JSON de TypeScript** y, a continuación, haga clic en **Agregar**.

   Visual Studio agrega el archivo *tsconfig.json* a la raíz del proyecto. Puede usar este archivo para [configurar opciones](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) para el compilador de TypeScript.

1. Abra *tsconfig.json* y actualícelo para establecer las opciones del compilador que desee.

   A continuación se muestra un ejemplo de un archivo *tsconfig.json* simple.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "dist"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   En este ejemplo:
   - *include* indica al compilador dónde encontrar archivos de TypeScript (*.ts).
   - La opción *outDir* especifica la carpeta de salida para los archivos JavaScript sin formato que el compilador de TypeScript transpila.
   - La opción *sourceMap* indica si el compilador genera archivos *sourceMap*.

   La configuración anterior proporciona solo una introducción básica a la configuración de TypeScript. Para obtener información sobre otras opciones, consulte [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="build-the-application"></a>Compilar la aplicación

1. Agregue archivos TypeScript ( *.ts*) o TypeScript JSX ( *.tsx*) al proyecto y, a continuación, agregue código de TypeScript. Para obtener un ejemplo sencillo de TypeScript, use lo siguiente:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. En *package.json*, agregue compatibilidad con los comandos de limpieza y compilación de Visual Studio mediante los siguientes scripts.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   Si debe realizar la compilación mediante una herramienta de terceros como webpack, puede agregar un script de compilación de línea de comandos al archivo *package.json*:

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   Para ver un ejemplo de cómo usar webpack con React y un archivo de configuración de webpack, consulte [Crear una aplicación web con Node.js y React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

   Para ver un ejemplo de cómo usar Vue.js con TypeScript, consulte [Crear una aplicación Vue.js](/javascript/create-application-with-vuejs).

1. Si debe configurar opciones como la página de inicio, la ruta de acceso al runtime de Node.js, el puerto de la aplicación o los argumentos de tiempo de ejecución, haga clic con el botón derecho en el nodo de proyecto del Explorador de soluciones y elija **Propiedades**.

   >[!NOTE]
   > Al configurar herramientas de terceros, los proyectos de Node.js no usan las rutas de acceso configuradas en **Herramientas** > **Opciones** > **Proyectos y soluciones** > **Administración de paquetes web** > **Herramientas web externas**. Esta configuración se utiliza para otros tipos de proyectos.

1. Elija **Compilar > Compilar solución**.

   Aunque la aplicación se compila automáticamente cuando la ejecuta, queremos fijarnos en algo que ocurre durante el proceso de compilación:

   Si ha generado mapas de origen, abra la carpeta especificada en la opción *outDir* y encontrará los archivos \*.js generados junto con los archivos \*js.map generados.

   Los archivos de asignación de origen son necesarios para la [depuración](../javascript/debug-nodejs.md).

### <a name="run-the-application"></a>Ejecutar la aplicación

Para obtener instrucciones para ejecutar la aplicación después de compilarla, vea [Creación de la primera aplicación Node.js](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json#run-the-application).

## <a name="automate-build-tasks"></a>Automatizar las tareas de compilación

Puede usar el Explorador del ejecutor de tareas en Visual Studio para ayudar a automatizar las tareas para herramientas de terceros como npm y webpack.

- [Ejecutor de tareas de NPM](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner): agrega compatibilidad con los scripts npm definidos en *package.json*. Admite yarn.
- [Ejecutor de tareas de webpack](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner): agrega compatibilidad con webpack.