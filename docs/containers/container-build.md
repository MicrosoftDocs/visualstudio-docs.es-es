---
title: Información general sobre compilación en las herramientas de contenedor de Visual Studio
author: ghogen
description: Información general del proceso de compilación en las herramientas de contenedor
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: edc4674e2468124ecb46b25a1411043ed4b66a2a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253114"
---
# <a name="building-containerized-apps-using-visual-studio-or-the-command-line"></a>Compilar aplicaciones en contenedores con Visual Studio o la línea de comandos

Tanto si va a compilar desde el IDE de Visual Studio como si va a configurar una compilación de línea de comandos, debe conocer la forma en que las compilaciones de Visual Studio usan el archivo Dockerfile para compilar los proyectos.  Por motivos de rendimiento, Visual Studio sigue un proceso especial para las aplicaciones en contenedores. Entender cómo Visual Studio compila los proyectos es particularmente importante al personalizar el proceso de compilación modificando el archivo Dockerfile.

Cuando Visual Studio compila un proyecto que no usa contenedores de Docker, invoca a MSBuild en el equipo local y genera los archivos de salida en una carpeta (normalmente `bin`) dentro de la carpeta de local de la solución. Sin embargo, en un proyecto en contenedores el proceso de compilación tiene en cuenta las instrucciones del archivo Dockerfile para compilar la aplicación en contenedores. El archivo Dockerfile que usa Visual Studio se divide en varias fases. Este proceso se basa en la característica de *compilación de varias fases* de Docker.

## <a name="multistage-build"></a>Compilación de varias fases

La característica de compilación de varias fases hace más eficaz el proceso de compilación de contenedores y hace que los contenedores sean más pequeños, lo que les permite contener solo los bits que la aplicación necesita en tiempo de ejecución. La compilación de varias fases se usa para los proyectos de .NET Core, no para los proyectos de .NET Framework.

La compilación de varias fases permite crear imágenes de contenedor en fases que producen imágenes intermedias. Por ejemplo, considere un archivo Dockerfile típico generado por Visual Studio. La primera fase es `base`:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Las líneas en el archivo Dockerfile comienzan con la imagen Nanoserver del Registro de contenedor de Microsoft (mcr.microsoft.com) y crean una imagen intermedia `base` que expone los puertos 80 y 443, y establece el directorio de trabajo en `/app`.

La siguiente fase es `build`, que se muestra de la siguiente manera:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Puede ver que la fase `build` se inicia a partir de una imagen original diferente del registro (`sdk`, en vez de `aspnet`), en lugar de continuar desde la base.  La imagen `sdk` tiene todas las herramientas de compilación y, por esa razón, es mucho más grande que la imagen ASPNET, que solo contiene componentes en tiempo de ejecución. El motivo por el que se usa una imagen independiente queda claro cuando se examina el resto del archivo Dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

La fase final se inicia de nuevo desde `base` e incluye `COPY --from=publish` para copiar la salida publicada en la imagen final. Este proceso permite que la imagen final sea mucho más pequeña, ya que no tiene que incluir todas las herramientas de compilación que se encontraban en la imagen `sdk`.

## <a name="faster-builds-for-the-debug-configuration"></a>Compilaciones más rápidas para la configuración de depuración

Varias de las optimizaciones que realiza Visual Studio le ayudan con el rendimiento del proceso de compilación para proyectos en contenedores. Cuando inicia la depuración (F5), se vuelve a usar una imagen compilada previamente, si es posible. Si no desea volver a usar el contenedor anterior, puede usar los comandos **Rebuild** o **Clean** en Visual Studio para obligar a Visual Studio a usar un nuevo contenedor.

Además, para mejorar el rendimiento, el proceso de compilación de aplicaciones en contenedores no es tan sencillo como seguir los pasos descritos en el archivo Dockerfile. La compilación en un contenedor es mucho más lenta que la compilación en el equipo local.  Por lo tanto, al compilar en la configuración **Debug**, Visual Studio compila los proyectos en el equipo local y, a continuación, comparte la carpeta de salida con el contenedor mediante el montaje del volumen. Una compilación con esta optimización habilitada se denomina compilación en modo *rápido*.

En modo **rápido**, Visual Studio llama a `docker build` con un argumento que le indica a Docker que compile solo la fase `base`.  Visual Studio controla el resto del proceso sin tener en cuenta el contenido de Dockerfile. Por lo tanto, cuando modifique el archivo Dockerfile, como para personalizar el entorno del contenedor o instalar dependencias adicionales, debe colocar las modificaciones en la primera fase.  No se ejecutará ningún paso personalizado colocado en las fases `build`, `publish` o `final` del archivo Dockerfile.

Esta optimización del rendimiento solo se produce cuando compila en la configuración **Debug**. En la configuración **Release**, la compilación se produce en el contenedor tal y como se especifica en el archivo Dockerfile.

Si desea deshabilitar la optimización del rendimiento y compilar como se especifica en el archivo Dockerfile, establezca la propiedad **ContainerDevelopmentMode** en **Regular** en el archivo del proyecto de la siguiente manera:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Para restaurar la optimización del rendimiento, quite la propiedad del archivo de proyecto.

## <a name="building-from-the-command-line"></a>Compilar desde la línea de comandos

Puede usar `docker build` o `MSBuild` para compilar desde la línea de comandos.

### <a name="docker-build"></a>docker build

Para compilar una solución en contenedores desde la línea de comandos, normalmente puede usar el comando `docker build <context>` para cada proyecto de la solución. Proporcione el argumento *build context*. El *contexto de compilación* para un archivo Dockerfile es la carpeta del equipo local que se usa como carpeta de trabajo para generar la imagen. Por ejemplo, es la carpeta desde la que se copian los archivos cuando copia en el contenedor.  En los proyectos de .NET Core, use la carpeta que contiene el archivo de solución (.sln).  Expresado como una ruta de acceso relativa, este argumento suele ser ".." para un archivo Dockerfile en una carpeta del proyecto y el archivo de solución en su carpeta principal.  En el caso de los proyectos de .NET Framework, el contexto de compilación es la carpeta del proyecto, no la carpeta de la solución.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Los archivos Dockerfile creados por Visual Studio para proyectos de .NET Framework (y para proyectos de .NET Core creados con versiones de Visual Studio anteriores a Visual Studio 2017 Update 4) no son archivos Dockerfile de varias fases.  Los pasos de estos archivos Dockerfile no compilan el código.  En su lugar, cuando Visual Studio compila un archivo Dockerfile de .NET Framework, primero compila el proyecto con MSBuild.  Cuando esto se realiza correctamente, Visual Studio compila el archivo Dockerfile, que simplemente copia la salida de la compilación de MSBuild en la imagen de Docker resultante.  Dado que los pasos para compilar el código no se incluyen en el archivo Dockerfile, no se puede compilar archivos Dockerfile de .NET Framework con `docker build` desde la línea de comandos. Debe utilizar MSBuild para compilar estos proyectos.

Para compilar una imagen para un solo proyecto de contenedor de Docker, puede usar MSBuild con la opción de comando `/t:ContainerBuild`. Por ejemplo:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Verá una salida similar a la que ve en la ventana **Output** cuando compila la solución desde el IDE de Visual Studio. Use siempre `/p:Configuration=Release`, ya que en los casos en los que Visual Studio usa la optimización de la compilación de varias fases, los resultados que se generan al compilar la configuración **Debug** podrían no ser los que se esperan.

Si usa un proyecto de Docker Compose, use el comando para compilar imágenes:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre cómo personalizar aún más las compilaciones estableciendo propiedades de MSBuild adicionales en los archivos del proyecto. Consulte [Propiedades de MSBuild para proyectos en contenedores](container-msbuild-properties.md).

## <a name="see-also"></a>Vea también

[MSBuild](../msbuild/msbuild.md)
[Dockerfile en Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[Contenedores de Linux en Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
