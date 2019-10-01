---
title: Propiedades de compilación de las herramientas de contenedor de Visual Studio
author: ghogen
description: Información general del proceso de compilación en las herramientas de contenedor
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 4bc6cb4221d85bd43b98b2ac36c34c919937960b
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2019
ms.locfileid: "71126062"
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

En la tabla siguiente se muestran las propiedades de MSBuild disponibles para proyectos de contenedor.

| Nombre de la propiedad | DESCRIPCIÓN | Valor predeterminado  |
|---------------|-------------|----------------|
| DockerfileFile | Describe el archivo Dockerfile predeterminado que se usará para compilar o ejecutar el contenedor del proyecto. También puede ser una ruta de acceso. | Dockerfile |
| DockerfileTag | La etiqueta que se usará al compilar la imagen de Docker. En la depuración, se anexa un ":dev" a la etiqueta. | Nombre del ensamblado después de quitar caracteres no alfanuméricos con las siguientes reglas: <br/> Si la etiqueta resultante es numérica, "Image" se inserta como prefijo (por ejemplo, image2314) <br/> Si la etiqueta resultante es una cadena vacía, se usa "Image" como etiqueta. |
| DockerContext | El contexto predeterminado que se usa al compilar la imagen de Docker. | Establecido por Visual Studio. |
| ContainerDevelopmentMode | Controla si la optimización de "compilación en host" (depuración en "modo rápido") está habilitada.  Los valores permitidos son **Rápido** y **Normal**. | Rápido |
| DockerDefaultTargetOS | El sistema operativo de destino predeterminado que se usa al compilar la imagen de Docker. | Establecido por Visual Studio. |
| DockerImageLabels | El conjunto predeterminado de etiquetas aplicadas a la imagen de Docker. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |
| ContainerVsDbgPath | La ruta de acceso para el depurador de VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |
| DockerfileBuildArguments | Los argumentos adicionales pasados al comando de compilación de Docker. | No es aplicable. |
| DockerfileRunArguments | Los argumentos adicionales pasados al comando de ejecución de Docker. | No es aplicable. |
| DockerfileRunEnvironmentFiles | Lista delimitada por punto y coma de archivos de entorno aplicada durante la ejecución de Docker. | No es aplicable. |
| DockerfileFastModeStage | La fase de Dockerfile (es decir, el destino) que se va a usar al compilar la imagen en modo de depuración. | Primera fase encontrada en el archivo Dockerfile (base) |
| DockerDebuggeeProgram | Durante la depuración, se indica al depurador que inicie este archivo ejecutable. | Para proyectos de .NET Core: dotnet, ASP.NET, proyectos de .NET Framework: No es aplicable (siempre se usa IIS) |
| DockerDebuggeeArguments | Durante la depuración, se indica al depurador que pase estos argumentos al ejecutable iniciado. | No aplicable a proyectos de .NET Framework de ASP.NET |
| DockerDebuggeeWorkingDirectory | Durante la depuración, se indica al depurador que use esta ruta de acceso como directorio de trabajo. | C:\app (Windows) o /app (Linux) |
| DockerDebuggeeKillProgram | Este comando se usa para terminar el proceso en ejecución en un contenedor. | No aplicable a proyectos de .NET Framework de ASP.NET |

## <a name="next-steps"></a>Pasos siguientes

Para obtener información sobre las propiedades de MSBuild en general, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Vea también

[Propiedades de compilación de Docker Compose ](docker-compose-properties.md)

[Configuración de inicio de las herramientas de contenedor](container-launch-settings.md)

[Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
