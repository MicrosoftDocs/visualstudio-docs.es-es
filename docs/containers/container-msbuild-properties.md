---
title: Propiedades de compilación de las herramientas de contenedor de Visual Studio
author: ghogen
description: Información general del proceso de compilación en las herramientas de contenedor
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 3caa8a76f461515c0d2265590383861b6e10d0a1
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472669"
---
# <a name="container-tools-build-properties"></a>Propiedades de compilación de las herramientas de contenedor

Puede personalizar el modo en que Visual Studio compila los proyectos de contenedor estableciendo las propiedades que MSBuild usa para compilar el proyecto. Por ejemplo, puede cambiar el nombre del archivo Dockerfile, especificar etiquetas para las imágenes, proporcionar argumentos adicionales pasados a los comandos de Docker y controlar si Visual Studio realiza ciertas optimizaciones de rendimiento, como la creación fuera del entorno de contenedor. También puede establecer propiedades de depuración, como el nombre del archivo ejecutable que se va a iniciar y los argumentos de la línea de comandos que se van a proporcionar.

Para establecer el valor de una propiedad, edite el archivo del proyecto. Por ejemplo, supongamos que el archivo Dockerfile se denomina *MyDockerfile*. Puede establecer la propiedad `DockerfileFile` en el archivo del proyecto como se indica a continuación.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Puede agregar el valor de la propiedad a un elemento `PropertyGroup` existente o, si no hay ninguno, crear un nuevo elemento `PropertyGroup`.

En la tabla siguiente se muestran las propiedades de MSBuild disponibles para proyectos de contenedor. La versión del paquete NuGet se aplica a [Microsoft.VisualStudio.Azure.Containers.Tools.Targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Nombre de la propiedad | Descripción | Valor predeterminado  | Versión del paquete NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Controla si la optimización de "compilación en host" (depuración en "modo rápido") está habilitada.  Los valores permitidos son **Rápido** y **Normal**. | Rápido |1.0.1872750 o más reciente|
| ContainerVsDbgPath | La ruta de acceso para el depurador de VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 o más reciente|
| DockerDebuggeeArguments | Durante la depuración, se indica al depurador que pase estos argumentos al ejecutable iniciado. | No aplicable a proyectos de .NET Framework de ASP.NET |1.7.8 o más reciente|
| DockerDebuggeeProgram | Durante la depuración, se indica al depurador que inicie este archivo ejecutable. | Para proyectos de .NET Core: dotnet, ASP.NET, proyectos de .NET Framework: No es aplicable (siempre se usa IIS) |1.7.8 o más reciente|
| DockerDebuggeeKillProgram | Este comando se usa para terminar el proceso en ejecución en un contenedor. | No aplicable a proyectos de .NET Framework de ASP.NET |1.7.8 o más reciente|
| DockerDebuggeeWorkingDirectory | Durante la depuración, se indica al depurador que use esta ruta de acceso como directorio de trabajo. | C:\app (Windows) o /app (Linux) |1.7.8 o más reciente|
| DockerDefaultTargetOS | El sistema operativo de destino predeterminado que se usa al compilar la imagen de Docker. | Establecido por Visual Studio. |1.0.1985401 o más reciente|
| DockerImageLabels | El conjunto predeterminado de etiquetas aplicadas a la imagen de Docker. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |1.5.4 o más reciente|
| DockerFastModeProjectMountDirectory|En el **modo rápido**, esta propiedad controla dónde se monta el volumen del directorio de salida del proyecto en el contenedor en ejecución.|C:\app (Windows) o /app (Linux)|1.9.2 o más reciente|
| DockerfileBuildArguments | Los argumentos adicionales pasados al comando de compilación de Docker. | No es aplicable. |1.0.1872750 o más reciente|
| DockerfileContext | Contexto predeterminado que se usa al compilar la imagen de Docker, como una ruta de acceso relativa a Dockerfile. | Establecido por Visual Studio. |1.0.1872750 o más reciente|
| DockerfileFastModeStage | La fase de Dockerfile (es decir, el destino) que se va a usar al compilar la imagen en modo de depuración. | Primera fase encontrada en el archivo Dockerfile (base) |
| DockerfileFile | Describe el archivo Dockerfile predeterminado que se usará para compilar o ejecutar el contenedor del proyecto. También puede ser una ruta de acceso. | Dockerfile |1.0.1872750 o más reciente|
| DockerfileRunArguments | Los argumentos adicionales pasados al comando de ejecución de Docker. | No es aplicable. |1.0.1872750 o más reciente|
| DockerfileRunEnvironmentFiles | Lista delimitada por punto y coma de archivos de entorno aplicada durante la ejecución de Docker. | No es aplicable. |1.0.1872750 o más reciente|
| DockerfileTag | La etiqueta que se usará al compilar la imagen de Docker. En la depuración, se anexa un ":dev" a la etiqueta. | Nombre del ensamblado después de quitar caracteres no alfanuméricos con las siguientes reglas: <br/> Si la etiqueta resultante es numérica, "Image" se inserta como prefijo (por ejemplo, image2314) <br/> Si la etiqueta resultante es una cadena vacía, se usa "Image" como etiqueta. |1.0.1872750 o más reciente|

## <a name="next-steps"></a>Pasos siguientes

Para obtener información sobre las propiedades de MSBuild en general, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Vea también

[Propiedades de compilación de Docker Compose ](docker-compose-properties.md)

[Configuración de inicio de las herramientas de contenedor](container-launch-settings.md)

[Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
