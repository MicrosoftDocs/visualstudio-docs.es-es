---
title: Configuración de compilación de Docker Compose
author: ghogen
description: Obtenga información sobre cómo editar las propiedades de compilación de Docker Compose para personalizar el modo en que Visual Studio compila y ejecuta una aplicación de Docker Compose.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: b3744640aada798179c86cc60d2c8ce7b02ccfaa
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973484"
---
# <a name="docker-compose-build-properties"></a>Propiedades de compilación de Docker Compose

Además de las propiedades que controlan los proyectos individuales de Docker, descritas en [Propiedades de compilación de las herramientas de contenedor](container-msbuild-properties.md), también puede personalizar el modo en que Visual Studio compila los proyectos de Docker Compose si configura las propiedades de Docker Compose que MSBuild usa para compilar la solución. También puede controlar el modo en que el depurador de Visual Studio ejecuta las aplicaciones de Docker Compose estableciendo etiquetas de archivo en los archivos de configuración de Docker Compose.

## <a name="how-to-set-the-msbuild-properties"></a>Cómo establecer las propiedades de MSBuild

Para establecer el valor de una propiedad, edite el archivo del proyecto. En el caso de las propiedades de Docker Compose, este archivo del proyecto es el que tiene una extensión .dcproj, a menos que se indique lo contrario en la tabla de la sección siguiente. Por ejemplo, supongamos que desea especificar que se inicie el explorador al iniciar la depuración. Puede establecer la propiedad `DockerLaunchAction` en el archivo del proyecto .dcproj como se indica a continuación.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Puede agregar el valor de la propiedad a un elemento `PropertyGroup` existente o, si no hay ninguno, crear un nuevo elemento `PropertyGroup`.

## <a name="docker-compose-msbuild-properties"></a>Propiedades de MSBuild de Docker Compose

En la tabla siguiente se muestran las propiedades de MSBuild disponibles para proyectos de Docker Compose.

| Nombre de la propiedad | Ubicación | Descripción | Valor predeterminado  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Esta opción permite especificar archivos de composición adicionales en una lista delimitada por signos de punto y coma que se envía a docker-compose.exe para todos los comandos. Se permiten las rutas de acceso relativas del archivo de proyecto docker-compose (dcproj).|-|
|DockerComposeBaseFilePath|dcproj|Permite especificar la primera parte de los nombres de archivo de los archivos docker-compose, sin la extensión *.yml*. Por ejemplo: <br>1. DockerComposeBaseFilePath = null/undefined: use la ruta de acceso del archivo base *docker-compose*; los archivos se denominarán *docker-compose.yml* y *docker-compose.override.yml*.<br>2. DockerComposeBaseFilePath = *mydockercompose*: los archivos se denominarán *mydockercompose.yml* y *mydockercompose.override.yml*.<br> 3. DockerComposeBaseFilePath = *..\mydockercompose*: los archivos se subirán un nivel. |docker-compose|
|DockerComposeBuildArguments|dcproj|Especifica los parámetros adicionales que se van a pasar al comando `docker-compose build`. Por ejemplo, `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Especifica los parámetros adicionales que se van a pasar al comando `docker-compose down`. Por ejemplo, `--timeout 500`.|-|  
|DockerComposeProjectName| dcproj | Si se especifica, invalida el nombre del proyecto para un proyecto docker-compose. | "dockercompose" + hash generado automáticamente |
|DockerComposeProjectPath|csproj o vbproj|La ruta de acceso relativa al archivo del proyecto docker-compose (dcproj). Establezca esta propiedad al publicar el proyecto de servicio para buscar la configuración de compilación de la imagen asociada que se almacena en el archivo docker-compose.yml.|-|
|DockerComposeProjectsToIgnore|dcproj| Especifica los proyectos que las herramientas de docker-compose omitirán durante la depuración. Esta propiedad se puede usar para cualquier proyecto. Las rutas de acceso al archivo se pueden especificar de una de estas dos maneras: <br> 1. En relación con dcproj. Por ejemplo, `<DockerComposeProjectsToIgnore>path\to\AngularProject1.csproj</DockerComposeProjectsToIgnore>`. <br> 2. Rutas de acceso absolutas.<br> **Nota**: las rutas de acceso deben estar separadas por el carácter delimitador `;`.|-|
|DockerComposeUpArguments|dcproj|Especifica los parámetros adicionales que se van a pasar al comando `docker-compose up`. Por ejemplo, `--timeout 500`.|-|
|DockerDevelopmentMode| dcproj | Controla si el proyecto de usuario está integrado en el contenedor. Los valores **Rápido** o **Regular** permitidos controlan [qué fases están integradas](https://aka.ms/containerfastmode) en un Dockerfile. La configuración predeterminado tiene el modo rápido de forma predeterminada y, en caso contrario, el modo regular. | Rápido |
|DockerLaunchAction| dcproj | Especifica la acción de inicio que se va a realizar en F5 o Ctrl+F5.  Los valores permitidos son None, LaunchBrowser y LaunchWCFTestClient. | None |
|DockerLaunchBrowser| dcproj | Indica si se va a iniciar el explorador. Se omite si se especifica DockerLaunchAction. | False |
|DockerServiceName| dcproj| Si se especifican DockerLaunchAction o DockerLaunchBrowser, DockerServiceName especifica qué servicio al que se hace referencia en el archivo docker-compose se inicia.|-|
|DockerServiceUrl| dcproj | Esta dirección URL se usa al iniciar el explorador.  Los tokens de reemplazo válidos son "{ServiceIPAddress}", "{ServicePort}" y "{Scheme}".  Por ejemplo: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | El sistema operativo de destino que se usa al compilar la imagen de Docker.|-|

## <a name="example"></a>Ejemplo

Si establece `DockerComposeBaseFilePath` en una ruta de acceso relativa para cambiar la ubicación de los archivos de Docker Compose, también debe asegurarse de cambiar el contexto de compilación para que haga referencia a la carpeta de la solución. Por ejemplo, si el archivo de Docker Compose es una carpeta denominada *DockerComposeFiles*, el archivo debe tener establecido el contexto de compilación en ".." o "../..", en función de dónde esté respecto a la carpeta de la solución.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" Sdk="Microsoft.Docker.Sdk">
  <PropertyGroup Label="Globals">
    <ProjectVersion>2.1</ProjectVersion>
    <DockerTargetOS>Windows</DockerTargetOS>
    <ProjectGuid>154022c1-8014-4e9d-bd78-6ff46670ffa4</ProjectGuid>
    <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
    <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
    <DockerServiceName>webapplication1</DockerServiceName>
    <DockerComposeBaseFilePath>DockerComposeFiles\mydockercompose</DockerComposeBaseFilePath>
    <AdditionalComposeFilePaths>AdditionalComposeFiles\myadditionalcompose.yml</AdditionalComposeFilePaths>
  </PropertyGroup>
  <ItemGroup>
    <None Include="DockerComposeFiles\mydockercompose.override.yml">
      <DependentUpon>DockerComposeFiles\mydockercompose.yml</DependentUpon>
    </None>
    <None Include="DockerComposeFiles\mydockercompose.yml" />
    <None Include=".dockerignore" />
  </ItemGroup>
</Project>
```

El archivo *mydockercompose.yml* debe tener un aspecto similar al siguiente, además de tener el contexto de compilación establecido en la ruta de acceso relativa de la carpeta de la solución (en este caso, `..`).

```yml
version: '3.4'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    build:
      context: ..
      dockerfile: WebApplication1\Dockerfile
```

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments y DockerComposeUpArguments son nuevos en Visual Studio 2019 versión 16.3.

## <a name="overriding-visual-studios-docker-compose-configuration"></a>Invalidación de la configuración de Docker Compose en Visual Studio

Puede invalidar determinadas opciones de configuración si coloca un archivo denominado *docker-compose.vs.debug.yml* (para el modo **Rápido**) o *docker-compose.vs.release.yml* (para el modo **Regular**) en el mismo directorio que su archivo *docker-compose.yml*. 

>[!TIP] 
>Para averiguar los valores predeterminados de cualquiera de estas opciones, busque en *docker-compose.vs.debug.g.yml* o *docker-compose.vs.release.g.yml*.

### <a name="docker-compose-file-labels"></a>Etiquetas de archivo de Docker Compose

 En *docker-compose.vs.debug.yml* o *docker-compose.vs.release.yml*, puede definir etiquetas específicas de invalidación como se muestra a continuación:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Use comillas dobles alrededor de los valores, como en el ejemplo anterior, y use la barra diagonal inversa como carácter de escape para las barras diagonales inversas en las rutas de acceso.

|Un nombre de etiqueta|Descripción|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Los argumentos que se pasan al programa al iniciar la depuración. En el caso de las aplicaciones de .NET Core, estos argumentos normalmente son rutas de búsqueda adicionales para los paquetes NuGet, seguidas de la ruta de acceso al ensamblado de salida del proyecto.|
|com.microsoft.visualstudio.debuggee.program|El programa que se inicia al iniciar la depuración. En el caso de las aplicaciones de .NET Core, este valor suele ser **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|El directorio que se usa como directorio de inicio al iniciar la depuración. Este valor suele ser */app* para los contenedores de Linux o *C:\app* para los contenedores de Windows.|
|com.microsoft.visualstudio.debuggee.killprogram|Este comando se usa para detener el programa de depurado que se ejecuta dentro del contenedor (si es necesario).|

### <a name="customize-the-docker-build-process"></a>Personalización del proceso de compilación de Docker

Puede declarar qué fase se va a compilar en el Dockerfile mediante la opción `target` en la propiedad `build`. Esta invalidación solo se puede usar en *docker-compose.vs.debug.yml* o *docker-compose.vs.release.yml*. 

```yml
services:
  webapplication1:
    build:
      target: customStage
    labels:
      ...
```

### <a name="customize-the-app-startup-process"></a>Personalización del proceso de inicio de la aplicación

Puede ejecutar un comando o un script personalizado antes de iniciar la aplicación mediante el valor `entrypoint` y hacer que dependa de `DockerDevelopmentMode`. Por ejemplo, si tiene que configurar un certificado solo en modo **Rápido** mediante la ejecución de `update-ca-certificates`, pero no en modo **Regular**, podría agregar el código siguiente **solo** en *docker-compose.vs.debug.yml*:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

## <a name="next-steps"></a>Pasos siguientes

Para obtener información sobre las propiedades de MSBuild en general, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Vea también

[Propiedades de compilación de las herramientas de contenedor](container-msbuild-properties.md)

[Configuración de inicio de las herramientas de contenedor](container-launch-settings.md)

[Administración de perfiles de inicio para Docker Compose en Visual Studio](launch-profiles.md)

[Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
