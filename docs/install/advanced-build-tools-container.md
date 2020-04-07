---
title: Ejemplo avanzado de contenedores
description: ''
ms.date: 03/25/2020
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 92d0e984d4ccf595af2821dff9c02d069b16404d
ms.sourcegitcommit: dfa9476b69851c28b684ece66980bee735fef8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2020
ms.locfileid: "80273847"
---
# <a name="advanced-example-for-containers"></a>Ejemplo avanzado de contenedores

::: moniker range="vs-2017"

En el Dockerfile de ejemplo de [Instalar Build Tools en un contenedor](build-tools-container.md) siempre se usa la imagen [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) basada en la imagen más reciente de microsoft/windowsservercore y el instalador de Visual Studio Build Tools más reciente. Si publica esta imagen en un [Registro de Docker](https://azure.microsoft.com/services/container-registry) para que otros usuarios la extraigan, es posible que esta imagen sea válida para muchos escenarios. En cambio, en la práctica, es más habitual especificar qué imagen base se usa, qué archivos binarios se descargan y qué versiones de la herramienta se instalan.

::: moniker-end

::: moniker range="vs-2019"

En el Dockerfile de ejemplo de [Instalar Build Tools en un contenedor](build-tools-container.md) siempre se usa la imagen [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) basada en la imagen más reciente de microsoft/windowsservercore y el instalador de Visual Studio Build Tools más reciente. Si publica esta imagen en un [Registro de Docker](https://azure.microsoft.com/services/container-registry) para que otros usuarios la extraigan, es posible que esta imagen sea válida para muchos escenarios. En cambio, en la práctica, es más habitual especificar qué imagen base se usa, qué archivos binarios se descargan y qué versiones de la herramienta se instalan.

::: moniker-end

En el siguiente Dockerfile de ejemplo se usa una etiqueta de versión específica de la imagen de microsoft/dotnet-framework. El uso de una etiqueta específica para una imagen base es muy común y hace que sea fácil recordar que la generación o reconstrucción de imágenes siempre tiene la misma base.

> [!NOTE]
> No se puede instalar Visual Studio en microsoft/windowsservercore:10.0.14393.1593 ni en ninguna imagen basada en él, ya que tiene problemas conocidos al iniciar el instalador en un contenedor. Para obtener más información, vea [Problemas conocidos de contenedores](build-tools-container-issues.md).

En el ejemplo siguiente se descarga la versión más reciente de Build Tools. Si quiere usar una versión anterior de Build Tools que pueda instalar en un contenedor más adelante, primero debe [crear](create-an-offline-installation-of-visual-studio.md) y [mantener](update-a-network-installation-of-visual-studio.md) un diseño.

## <a name="install-script"></a>Instalar el script

Para recopilar registros cuando se produce un error de instalación, cree un script por lotes denominado "Install.cmd" en el directorio de trabajo con el siguiente contenido:

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Dockerfile

En el directorio de trabajo, cree el "Dockerfile" con el siguiente contenido:

::: moniker range="vs-2017"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:3eaa3ba18f45e6561f32d8dd927045413f1dd043d7d29fb581f5cb3c6f7d7481
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

   > [!WARNING]
   > Visual Studio 2017 versión 15.8 o cualquier versión anterior (de cualquier producto) no se instalará correctamente en mcr\.microsoft\.com\/windows\/servercore:1809 o posterior. No se mostrará ningún error.
   >
   > Para obtener más información, vea [Problemas conocidos de contenedores](build-tools-container-issues.md).

::: moniker-end

::: moniker range="vs-2019"

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:324e9ab7262331ebb16a4100d0fb1cfb804395a766e3bb1806c62989d1fc1326
ARG FROM_IMAGE=mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019
FROM ${FROM_IMAGE}

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/16/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --add Microsoft.VisualStudio.Workload.AzureBuildTools `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Define the entry point for the Docker container.
# This entry point starts the developer command prompt and launches the PowerShell shell.
ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

::: moniker-end

Ejecute el siguiente comando para compilar la imagen en el directorio de trabajo actual:

::: moniker range="vs-2017"

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

::: moniker-end

::: moniker range="vs-2019"

```shell
docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
```

::: moniker-end

Si quiere, puede pasar uno o ambos argumentos `FROM_IMAGE` o `CHANNEL_URL` mediante el conmutador de la línea de comandos `--build-arg` para especificar otra imagen base o la ubicación de un diseño interno para mantener una imagen fija.

   > [!TIP]
   > Para obtener una lista de las cargas de trabajo y los componentes, vea el [Directorio de componentes de Visual Studio Build Tools](workload-component-id-vs-build-tools.md).
   >

## <a name="diagnosing-install-failures"></a>Diagnosticar errores de instalación

En este ejemplo se descargan herramientas específicas y se valida que coincidan los valores hash. También se descarga la versión más reciente de Visual Studio y la utilidad de recopilación de registros de .NET para que, si se produce un error de instalación, pueda copiar los registros en el equipo host para analizar el error.

::: moniker range="vs-2017"

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

::: moniker range="vs-2019"

```shell
> docker build -t buildtools2019:16.0.28714.193 -t buildtools2019:latest -m 2GB .
Sending build context to Docker daemon

...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

::: moniker-end

Después de que termine de ejecutarse la última línea, abra "%TEMP%\vslogs.zip" en el equipo o envíe un problema en el sitio web de la [comunidad de desarrolladores](https://developercommunity.visualstudio.com).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Build Tools en un contenedor](build-tools-container.md)
* [Problemas conocidos de contenedores](build-tools-container-issues.md)
* [Identificadores de componente y carga de trabajo de Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
