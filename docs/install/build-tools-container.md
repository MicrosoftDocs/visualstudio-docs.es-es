---
title: Instalar Visual Studio Build Tools en un contenedor
titleSuffix: ''
description: Obtenga información sobre cómo instalar Visual Studio Build Tools en un contenedor de Windows para admitir los flujos de trabajo de integración continua y entrega continua (CI/CD).
ms.date: 03/25/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fd584a977900de83af454f26722d3e4ba2bd8ac8
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847668"
---
# <a name="install-build-tools-into-a-container"></a>Instalar Build Tools en un contenedor

Puede instalar Visual Studio Build Tools en un contenedor de Windows para admitir los flujos de trabajo de integración continua y entrega continua (CI/CD). Este artículo le guía a través de los cambios de configuración de Docker necesarios, así como de las [cargas de trabajo y componentes](workload-component-id-vs-build-tools.md) que puede instalar en un contenedor.

Los [contenedores](https://www.docker.com/what-container) son una excelente manera de empaquetar un sistema de compilación coherente que se puede usar no solo en un entorno de servidor de CI/CD sino también para entornos de desarrollo. Por ejemplo, puede montar el código fuente en un contenedor para que se compile en un entorno personalizado mientras continúa usando Visual Studio u otras herramientas para escribir el código. Si en el flujo de trabajo de CI/CD se usa la misma imagen de contenedor, puede estar seguro de que el código se compila de forma coherente. También puede usar contenedores por motivos de coherencia del tiempo de ejecución, lo que es común para microservicios que usan varios contenedores con un sistema de orquestación, pero queda fuera del ámbito de este artículo.

Si Visual Studio Build Tools no tiene lo que necesita para compilar el código fuente, estos mismos pasos se pueden usar para otros productos de Visual Studio. Pero tenga en cuenta que los contenedores de Windows no admiten una interfaz de usuario interactiva, por lo que todos los comandos se deben automatizar.

## <a name="before-you-begin"></a>Antes de empezar

A continuación se supone que tiene cierta familiaridad con [Docker](https://www.docker.com/what-docker). Si no está familiarizado con la ejecución de Docker en Windows, obtenga información sobre cómo [instalar y configurar el motor de Docker en Windows](/virtualization/windowscontainers/manage-docker/configure-docker-daemon).

La imagen base siguiente es un ejemplo y puede que no funcione para su sistema. Consulte [Compatibilidad de versiones de contenedor de Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) para determinar qué imagen base debe usar para su entorno.

## <a name="create-and-build-the-dockerfile"></a>Crear y compilar el Dockerfile

Guarde el Dockerfile de ejemplo siguiente en un archivo nuevo en el disco. Si el archivo se denomina simplemente "Dockerfile", se reconoce de forma predeterminada.

> [!WARNING]
> En este Dockerfile de ejemplo solo se excluyen los SDK de Windows anteriores que no se pueden instalar en contenedores. Las versiones anteriores hacen que el comando genere un error.

1. Abra un símbolo del sistema.

1. Cree un directorio (recomendado):

   ```shell
   mkdir C:\BuildTools
   ```

1. Cambie los directorios a este nuevo directorio:

   ```shell
   cd C:\BuildTools
   ```

1. Guarde el contenido siguiente en C:\BuildTools\Dockerfile.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.7.2-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN start /wait C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the Docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Para obtener una lista de las cargas de trabajo y los componentes, vea el [Directorio de componentes de Visual Studio Build Tools](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > Si basa la imagen directamente en microsoft/windowsservercore o mcr.microsoft.com/windows/servercore (consulte [Microsoft syndicates container catalog](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/) [catálogo del contenedor de sindicatos de Microsoft]), puede que .NET Framework no se instale correctamente y no se indique ningún error de instalación. Es posible que el código administrado no se ejecute una vez completada la instalación. En su lugar, base la imagen en [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) o en otra versión posterior. Tenga en cuenta también que es posible que las imágenes etiquetadas con la versión 4.7.2 o posterior usen PowerShell como valor predeterminado de `SHELL`, lo que hará que las instrucciones `RUN` y `ENTRYPOINT` produzcan un error.
   >
   > Visual Studio 2017 versión 15.8 o cualquier versión anterior (de cualquier producto) no se instalará correctamente en mcr.microsoft.com/windows/servercore:1809 o posterior. No se mostrará ningún error.
   >
   > Consulte [Compatibilidad de versiones de contenedor de Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) para ver qué versiones de sistema operativo del contenedor se admiten en qué versiones de sistema operativo del host, y [Problemas conocidos de contenedores](build-tools-container-issues.md) para ver los problemas conocidos.
   
   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Para obtener una lista de las cargas de trabajo y los componentes, vea el [Directorio de componentes de Visual Studio Build Tools](workload-component-id-vs-build-tools.md).
   >

   > [!WARNING]
   > Si basa la imagen directamente en microsoft/windowsservercore, puede que .NET Framework no se instale correctamente y no se indique ningún error de instalación. Es posible que el código administrado no se ejecute una vez completada la instalación. En su lugar, base la imagen en [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) o en otra versión posterior. Tenga en cuenta también que es posible que las imágenes etiquetadas con la versión 4.8 o posterior usen PowerShell como valor predeterminado de `SHELL`, lo que hará que las instrucciones `RUN` y `ENTRYPOINT` produzcan un error.
   >
   > Consulte [Compatibilidad de versiones de contenedor de Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) para ver qué versiones de sistema operativo del contenedor se admiten en qué versiones de sistema operativo del host, y [Problemas conocidos de contenedores](build-tools-container-issues.md) para ver los problemas conocidos.

   ::: moniker-end
   
   > [!NOTE]
   > El código de error `3010` se usa para indicar que un reinicio necesario se ha realizado correctamente; vea [Mensajes de error MsiExec.exe](/windows/win32/msi/error-codes) para obtener más información.

1. Ejecute el comando siguiente desde ese directorio.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Este comando compila el archivo Dockerfile en el directorio actual con 2 GB de memoria. El valor predeterminado de 1 GB no es suficiente cuando se instalan algunas cargas de trabajo; pero es posible que pueda compilar con solo 1 GB de memoria en función de los requisitos de compilación.

   La imagen final se etiqueta con "buildtools2017:latest" para que se pueda ejecutar fácilmente en un contenedor como "buildtools2017" ya que la etiqueta "latest" es el valor predeterminado si no se especifica ninguna etiqueta. Si quiere usar una versión específica de Visual Studio Build Tools 2017 en un [escenario más avanzado](advanced-build-tools-container.md), en su lugar se podría etiquetar el contenedor con un número de compilación de Visual Studio específico además de "latest", para que los contenedores puedan usar una versión determinada de forma coherente.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Este comando compila el archivo Dockerfile en el directorio actual con 2 GB de memoria. El valor predeterminado de 1 GB no es suficiente cuando se instalan algunas cargas de trabajo; pero es posible que pueda compilar con solo 1 GB de memoria en función de los requisitos de compilación.

   La imagen final se etiqueta con "buildtools2019:latest" para que se pueda ejecutar fácilmente en un contenedor como "buildtools2019" ya que la etiqueta "latest" es el valor predeterminado si no se especifica ninguna etiqueta. Si quiere usar una versión específica de Visual Studio Build Tools 2019 en un [escenario más avanzado](advanced-build-tools-container.md), en su lugar se podría etiquetar el contenedor con un número de compilación de Visual Studio específico además de "latest", para que los contenedores puedan usar una versión determinada de forma coherente.

   ::: moniker-end

## <a name="using-the-built-image"></a>Uso de la imagen compilada

Ahora que se ha creado una imagen, también se puede ejecutar en un contenedor para realizar compilaciones interactivas y automatizadas. En el ejemplo se usa el símbolo del sistema para desarrolladores, por lo que PATH y otras variables de entorno ya están configuradas.

1. Abra un símbolo del sistema.

1. Ejecute el contenedor para iniciar un entorno de PowerShell con todas las variables de entorno del desarrollador establecidas:

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

Para usar esta imagen con el flujo de trabajo de CI/CD, puede publicarla en su propia instancia de [Azure Container Registry](https://azure.microsoft.com/services/container-registry) o en otro [registro de Docker](https://docs.docker.com/registry/deploying) interno para que los servidores solo tengan que extraerla.

   > [!NOTE]
   > Si el contenedor de Docker genera algún error al iniciarse, es probable que haya un problema con la instalación de Visual Studio. Se puede actualizar Dockerfile para quitar el paso que llama al comando batch de Visual Studio. Esto permite iniciar el contenedor de Docker y leer los registros de errores de la instalación.
   >
   > En el archivo Dockerfile, quite los parámetros `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` y `&&` del comando `ENTRYPOINT`. Ahora, el comando debería ser `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]`. Después, recompile Dockerfile y ejecute el comando `run` para acceder a los archivos de contenedor. Para ubicar los registros de errores de instalación, vaya al directorio `$env:TEMP` y busque el archivo `dd_setup_<timestamp>_errors.log`.
   >
   > Después de identificar y corregir la incidencia de la instalación, se pueden volver a agregar los parámetros `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` y `&&` al comando `ENTRYPOINT` y recompilar Dockerfile.
   >
   > Para obtener más información, vea [Problemas conocidos de contenedores](build-tools-container-issues.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Ejemplo avanzado de contenedores](advanced-build-tools-container.md)
* [Problemas conocidos de contenedores](build-tools-container-issues.md)
* [Identificadores de componente y carga de trabajo de Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
