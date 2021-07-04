---
title: Introducción a Docker
description: Aprenda a agregar Docker a los proyectos en Visual Studio para Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.topic: how-to
ms.openlocfilehash: 4ddb15c8bc5bf90663c5431d2379af61b43e73a6
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043099"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>Introducción a Docker en Visual Studio para Mac

Con Visual Studio para Mac, puede crear, depurar y ejecutar fácilmente aplicaciones ASP.NET Core en contenedores y publicarlas en Azure.

## <a name="prerequisites"></a>Requisitos previos

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio para Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>Instalación y configuración

Para instalar Docker, revise y siga la información de [Instalación de Docker Desktop para Mac](https://docs.docker.com/docker-for-mac/install/).

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>Creación de una aplicación web ASP.NET Core y adición de compatibilidad con Docker

1. Para crear una nueva solución, vaya a **File > New Solution** (Archivo > Nueva solución).
1. En **.NET Core > App** (.NET Core > Aplicación), elija la plantilla **Web Application** (Aplicación web): ![Creación de una nueva aplicación ASP.NET](media/docker-quickstart-1.png)
1. Seleccione la plataforma de destino. En este ejemplo, usaremos .NET Core 2.2: ![Establecimiento de una plataforma de destino](media/docker-quickstart-2.png)
1. Escriba los detalles del proyecto, como el nombre (_DockerDemo_, en este ejemplo). El proyecto creado contiene todos los elementos básicos que necesita para crear y ejecutar un sitio web de ASP.NET Core.
1. En la ventana de la solución, haga clic con el botón derecho en el proyecto DockerDemo y seleccione **Agregar > Agregar compatibilidad con Docker**: ![Adición de compatibilidad con Docker](media/docker-quickstart-3.png)

Visual Studio para Mac agregará automáticamente un nuevo proyecto a la solución denominado **docker-compose** y agregará un archivo **Dockerfile** al proyecto existente.

![Archivos de compatibilidad generados con Docker](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Información general sobre el archivo Dockerfile

Un archivo Dockerfile es la receta para crear una imagen de Docker final. Vea [Dockerfile reference (Referencia de Dockerfile)](https://docs.docker.com/engine/reference/builder/) para obtener una descripción de los comandos que contiene.

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore "DockerDemo/DockerDemo.csproj"
COPY . .
WORKDIR "/src/DockerDemo"
RUN dotnet build "DockerDemo.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "DockerDemo.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

El elemento *Dockerfile* anterior se basa en la imagen [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) e incluye instrucciones para modificar la imagen base mediante la creación del proyecto y la adición al contenedor.

> [!NOTE]
> El valor predeterminado del archivo Dockerfile creado por Visual Studio para Mac expone el puerto 80 para el tráfico HTTP. Para habilitar el tráfico HTTPS, agregue `Expose 443` al archivo Dockerfile.

## <a name="debugging"></a>Depuración

Seleccione el proyecto `docker-compose` como proyecto de inicio e inicie la depuración (**Run > Start Debugging** [Ejecutar > Iniciar depuración]). Esto creará, implementará e iniciará el proyecto ASP.NET en un contenedor.

> [!TIP]
> En la primera ejecución después de instalar Docker Desktop, es posible que reciba el siguiente error al intentar depurar: `Cannot start service dockerdemo: Mounts denied`
>
> Agregue `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` a la pestaña File Sharing (Uso compartido de archivos) de Docker Desktop:
>
> ![Adición de la carpeta NuGetFallbackFolder a File Sharing (Uso compartido de archivos)](media/docker-quickstart-5.png)

Cuando se completa la creación, se iniciará la aplicación en Safari:

![Proyecto de Docker predeterminado que se ejecuta en Safari](media/docker-quickstart-6.png)

Tenga en cuenta que el contenedor estará escuchando en un puerto, `http://localhost:32768` por ejemplo, y este puerto puede variar.

Para ver la lista de los contenedores en ejecución, use el comando `docker ps` en Terminal.

Tenga en cuenta la retransmisión de puertos en la siguiente captura de pantalla (bajo **PORTS** [Puertos]). Esto muestra que el contenedor escucha en el puerto que vimos antes en Safari y retransmite solicitudes al servidor web interno en el puerto 80 (como se define en el archivo Dockerfile). Desde la perspectiva de la aplicación, está escuchando en el puerto 80:

![Lista de contenedores de Docker](media/docker-quickstart-7.png)
