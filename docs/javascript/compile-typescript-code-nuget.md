---
title: Compilar y generar código TypeScript con NuGet
description: Obtenga información sobre cómo agregar compatibilidad con TypeScript a sus proyectos de Visual Studio mediante el paquete NuGet.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 929c17c9cbd2a0987bebca02c70b3b751c19fc9a
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846822"
---
# <a name="compile-typescript-code-aspnet-core"></a>Compilar código TypeScript (ASP.NET Core)

Puede agregar compatibilidad con TypeScript a los proyectos mediante TypeScript SDK, que está disponible de forma predeterminada en el instalador de Visual Studio o mediante el paquete NuGet. Para los proyectos desarrollados en Visual Studio 2019, le animamos a usar NuGet de TypeScript para una mayor portabilidad entre distintas plataformas y entornos.

En el caso de los proyectos de ASP.NET Core, un uso habitual del paquete NuGet es compilar TypeScript mediante la CLI de .NET Core. A menos que se edite manualmente el archivo del proyecto para importar destinos de compilación desde una instalación TypeScript SDK, el paquete NuGet es la única manera de habilitar la compilación de TypeScript mediante comandos de la CLI de .NET Core, como `dotnet build` y `dotnet publish`. Además, para la [integración de MSBuild](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) con ASP.NET Core y TypeScript, elija el paquete NuGet antes que el paquete npm.

## <a name="add-typescript-support-with-nuget"></a>Agregar compatibilidad con TypeScript con NuGet

[El paquete NuGet de TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) agrega compatibilidad con TypeScript. Cuando se instala el paquete NuGet de TypeScript 3.2 o posterior en el proyecto, se carga la versión correspondiente del servicio de lenguaje TypeScript en el editor.

Si se instala Visual Studio, Visual Studio seleccionará automáticamente el proceso node.exe que incluye. Si no tiene instalado Node.js, se recomienda que instale la versión LTS desde el sitio web de [Node.js](https://nodejs.org/en/download/).

1. Abra el proyecto de ASP.NET Core en Visual Studio.

1. en el Explorador de soluciones (panel derecho). Haga clic con el botón derecho en el nodo de proyecto y elija **Administrar paquetes NuGet**. En la pestaña **Examinar**, busque **Microsoft.TypeScript.MSBuild** y, a continuación, haga clic en **Instalar** a la derecha para instalar el paquete.

   ![Adición del paquete NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio agrega el paquete NuGet en el nodo **Dependencias** del Explorador de soluciones. La referencia de paquete siguiente se agrega a su archivo *.csproj.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Haga clic con el botón derecho en el nodo de proyecto y elija **Agregar > Nuevo elemento**. Elija el **archivo de configuración JSON de TypeScript** y, a continuación, haga clic en **Agregar**.

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
       "outDir": "wwwroot/js"
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

### <a name="build-the-application"></a>Compilar la aplicación

1. Agregue archivos TypeScript ( *.ts*) o TypeScript JSX ( *.tsx*) al proyecto y, a continuación, agregue código de TypeScript. Para obtener un ejemplo sencillo de TypeScript, use lo siguiente:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. Si usa un proyecto anterior de estilo que no es de SDK, siga las instrucciones incluidas en [Eliminación de importaciones predeterminadas](#remove-default-imports) antes de la compilación.

1. Elija **Compilar > Compilar solución**.

   Aunque la aplicación se compila automáticamente cuando la ejecuta, queremos fijarnos en algo que ocurre durante el proceso de compilación:

   Si ha generado mapas de origen, abra la carpeta especificada en la opción *outDir* y encontrará los archivos *.js generados junto con los archivos *js.map generados.

   Los archivos de asignación de origen son necesarios para la depuración.

1. Si desea compilar cada vez que guarda el proyecto, use la opción *compileOnSave* en *.tsconfig.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Para ver un ejemplo del uso de gulp con el ejecutor de tareas para compilar la aplicación, consulte [ASP.NET Core y TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

Si experimenta algún problema que provoque que Visual Studio use una versión de Node.js o una herramienta de terceros distinta de la versión esperada, puede que tenga que establecer la ruta de acceso para que Visual Studio la use. Elija **Herramientas** > **Opciones**. En **Proyectos y soluciones**, elija **Administración de paquetes web** > **Herramientas web externas**.

### <a name="run-the-application"></a>Ejecutar la aplicación

Para obtener instrucciones para ejecutar la aplicación después de compilarla, vea [Creación de la primera aplicación Node.js](/visualstudio/ide/quickstart-nodejs?toc=%2Fvisualstudio%2Fjavascript%2Ftoc.json#run-the-application).

### <a name="nuget-package-structure-details"></a>Detalles de la estructura de paquetes NuGet

`Microsoft.TypeScript.MSBuild.nupkg` contiene dos carpetas principales:

- Carpeta *build*

    En esta carpeta hay dos archivos.
    Ambos son puntos de entrada: para el archivo de destino de TypeScript principal y el archivo de propiedades, respectivamente.

    1. *Microsoft.TypeScript.MSBuild.targets*

        Este archivo establece variables que especifican la plataforma en tiempo de ejecución, como una ruta de acceso a *TypeScript.Tasks.dll*, antes de importar *Microsoft.TypeScript.targets* desde la carpeta *tools*.

    2. *Microsoft.TypeScript.MSBuild.props*

        Este archivo importa *Microsoft.TypeScript.Default.props* desde la carpeta *tools* y establece propiedades que indican que la compilación se ha iniciado a través de NuGet.

- Carpeta *tools*

    Las versiones de paquete anteriores a 2.3 solo contienen una carpeta tsc. *Microsoft.TypeScript.targets* y *TypeScript.Tasks.dll* se encuentran en el nivel raíz.

    En las versiones de paquete 2.3 y posteriores, el nivel raíz contiene `Microsoft.TypeScript.targets` y `Microsoft.TypeScript.Default.props`. Para obtener más detalles sobre estos archivos, consulte [Configuración de MSBuild](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html).

    Además, la carpeta contiene tres subcarpetas:

    1. *net45*

        Esta carpeta contiene `TypeScript.Tasks.dll` y otros archivos DLL de los que depende.
        Al compilar un proyecto en una plataforma de Windows, MSBuild usa los archivos DLL de esta carpeta.

    2. *netstandard1.3*

        Esta carpeta contiene otra versión de `TypeScript.Tasks.dll`, que se usa al compilar proyectos en una máquina que no es Windows.

    3. *tsc*

        Esta carpeta contiene `tsc.js`, `tsserver.js` y todos los archivos de dependencia necesarios para su ejecución como scripts de nodo.

        > [!NOTE]
        > Si se instala Visual Studio, se seleccionará automáticamente el proceso *node.exe* que incluye. De lo contrario, Node.js debe instalarse en la máquina.

        Las versiones anteriores a 3.1 contenían un archivo ejecutable `tsc.exe` para ejecutar la compilación. En la versión 3.1, este se quitó en favor del uso de `node.exe`.

### <a name="remove-default-imports"></a>Eliminación de las importaciones predeterminadas

En proyectos de ASP.NET Core anteriores que usan el [formato de estilo que no es de SDK](https://docs.microsoft.com/nuget/resources/check-project-format), puede que tenga que quitar algunos elementos de archivo del proyecto.

Si se usa el paquete NuGet para la compatibilidad con MSBuild de un proyecto, el archivo del proyecto no debe importar `Microsoft.TypeScript.Default.props` ni `Microsoft.TypeScript.targets`. Los archivos los importa el paquete NuGet, por lo que incluirlos por separado podría provocar un comportamiento no intencionado.

1. Haga clic con el botón derecho en el proyecto y elija **Descargar proyecto**.

1. Haga clic con el botón derecho en el proyecto y elija **Editar \<*project file name*\>** .

   El archivo del proyecto se abre.

1. Quite las referencias a `Microsoft.TypeScript.Default.props` y `Microsoft.TypeScript.targets`.

   Las importaciones que se van a quitar tienen un aspecto similar al siguiente:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
