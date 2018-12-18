---
title: Instalar Visual Studio Build Tools en un contenedor
titleSuffix: ''
description: Obtenga información sobre cómo instalar Visual Studio Build Tools en un contenedor de Windows para admitir los flujos de trabajo de integración continua y entrega continua (CI/CD).
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37ce2fc60ac2a57baddf62e68a900349ed072f4d
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160093"
---
# <a name="install-build-tools-into-a-container"></a>Instalar Build Tools en un contenedor

Puede instalar Visual Studio Build Tools en un contenedor de Windows para admitir los flujos de trabajo de integración continua y entrega continua (CI/CD). Este artículo le guía a través de los cambios de configuración de Docker necesarios, así como de las [cargas de trabajo y componentes](workload-component-id-vs-build-tools.md) que puede instalar en un contenedor.

Los [contenedores](https://www.docker.com/what-container) son una excelente manera de empaquetar un sistema de compilación coherente que se puede usar no solo en un entorno de servidor de CI/CD sino también para entornos de desarrollo. Por ejemplo, puede montar el código fuente en un contenedor para que se compile en un entorno personalizado mientras continúa usando Visual Studio u otras herramientas para escribir el código. Si en el flujo de trabajo de CI/CD se usa la misma imagen de contenedor, puede estar seguro de que el código se compila de forma coherente. También puede usar contenedores por motivos de coherencia del tiempo de ejecución, lo que es común para microservicios que usan varios contenedores con un sistema de orquestación, pero queda fuera del ámbito de este artículo.

Si Visual Studio Build Tools no tiene lo que necesita para compilar el código fuente, estos mismos pasos se pueden usar para otros productos de Visual Studio. Pero tenga en cuenta que los contenedores de Windows no admiten una interfaz de usuario interactiva, por lo que todos los comandos se deben automatizar.

## <a name="overview"></a>Información general

Con [Docker](https://www.docker.com/what-docker) se crea una imagen desde la que se pueden crear contenedores para compilar el código fuente. El Dockerfile de ejemplo instala la versión más reciente de Visual Studio Build Tools 2017 y otros programas útiles que se usan a menudo para la compilación de código fuente. Puede modificar aún más su propio Dockerfile para incluir otras herramientas y scripts para ejecutar pruebas, publicar la salida de la compilación y mucho más.

Si ya ha instalado Docker para Windows, puede ir al paso 3.

## <a name="step-1-enable-hyper-v"></a>Paso 1. Habilitar Hyper-V

De forma predeterminada, Hyper-V no está habilitado. Debe estar habilitado para iniciar Docker para Windows, porque actualmente solo se admite el aislamiento de Hyper-V para Windows 10.

* [Habilitar Hyper-V en Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Habilitar Hyper-V en Windows Server 2016](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> La virtualización debe estar habilitada en el equipo. Normalmente está habilitada de forma predeterminada; pero si se produce un error de instalación de Hyper-V, vea la documentación del sistema para obtener información sobre cómo habilitar la virtualización.

## <a name="step-2-install-docker-for-windows"></a>Paso 2. Instalar Docker para Windows

Si usa Windows 10, puede [descargar e instalar Docker Community Edition](https://docs.docker.com/docker-for-windows/install). Si usa Windows Server 2016, siga las [instrucciones para instalar Docker Enterprise Edition](https://docs.docker.com/install/windows/docker-ee).

## <a name="step-3-switch-to-windows-containers"></a>Paso 3. Cambiar a contenedores de Windows

Solo se puede instalar Build Tools 2017 en Windows, lo que requiere [cambiar a contenedores de Windows](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers). Los contenedores de Windows en Windows 10 solo admiten el [aislamiento de Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container), mientras que los contenedores de Windows en Windows Server 2016 admiten el aislamiento de Hyper-V y de procesos.

## <a name="step-4-expand-maximum-container-disk-size"></a>Paso 4. Expandir el tamaño máximo de disco del contenedor

Visual Studio Build Tools y, en mayor medida, Visual Studio, requieren una gran cantidad de espacio en disco para todas las herramientas que se instalan. Aunque en el Dockerfile de ejemplo se deshabilita la caché del paquete, el tamaño de disco de las imágenes de contenedor debe aumentarse para alojar el espacio necesario. Actualmente, en Windows solamente se puede aumentar el tamaño de disco cambiando la configuración de Docker.

**En Windows 10**:

1. [Haga clic con el botón derecho en el icono de Docker para Windows](https://docs.docker.com/docker-for-windows/#docker-settings) en la bandeja del sistema y haga clic en **Configuración**.
2. [Haga clic en la sección Demonio](https://docs.docker.com/docker-for-windows/#docker-daemon).
3. [Alterne el botón **Básico**](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) a **Avanzado**.
4. Agregue la siguiente propiedad de matriz JSON para aumentar el espacio en disco a 120 GB (más que suficiente para Build Tools con espacio para que aumente).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Esta propiedad se agrega a todo lo que ya tenga. Por ejemplo, con estos cambios aplicados al archivo de configuración del demonio predeterminado, ahora verá lo siguiente:

   ```json
   {
     "registry-mirrors": [],
     "insecure-registries": [],
     "debug": true,
     "experimental": true,
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

5. Haga clic en **Aplicar**.

**En Windows Server 2016**:

1. Detenga el servicio "docker":

   ```shell
   sc.exe stop docker
   ```

2. Desde un símbolo del sistema con privilegios elevados, modifique "%ProgramData%\Docker\config\daemon.json" (o lo que especificó para `dockerd --config-file`).
3. Agregue la siguiente propiedad de matriz JSON para aumentar el espacio en disco a 120 GB (más que suficiente para Build Tools con espacio para que aumente).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Esta propiedad se agrega a todo lo que ya tenga.
4. Guarde y cierre el archivo.
5. Inicie el servicio "docker":

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>Paso 5. Crear y compilar el Dockerfile

Guarde el Dockerfile de ejemplo siguiente en un archivo nuevo en el disco. Si el archivo se denomina simplemente "Dockerfile", se reconoce de forma predeterminada.

> [!NOTE]
> En este Dockerfile de ejemplo solo se excluyen los SDK de Windows antiguos que no se pueden instalar en contenedores. Las versiones anteriores hacen que el comando genere un error.

1. Abra un símbolo del sistema.
2. Cree un directorio (recomendado):

   ```shell
   mkdir C:\BuildTools
   ```

3. Cambie los directorios a este nuevo directorio:

   ```shell
   cd C:\BuildTools
   ```

3. Guarde el contenido siguiente en C:\BuildTools\Dockerfile.

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.1.
   FROM microsoft/dotnet-framework:4.7.1

   # Restore the default Windows shell for correct batch processing below.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!NOTE]
   > Si basa la imagen directamente en microsoft/windowsservercore, puede que .NET Framework no se instale correctamente y no se indique ningún error de instalación. El código administrado podría no ejecutarse una vez completada la instalación. En su lugar, base la imagen en [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) o en otra versión más reciente. Tenga en cuenta también que puede ser que las nuevas imágenes usen PowerShell como valor `SHELL` predeterminado, lo que hará que las instrucciones `RUN` y `ENTRYPOINT` produzcan un error.

4. Ejecute el comando siguiente desde ese directorio.

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Este comando compila el archivo Dockerfile en el directorio actual con 2 GB de memoria. El valor predeterminado de 1 GB no es suficiente cuando se instalan algunas cargas de trabajo; pero es posible que pueda compilar con solo 1 GB de memoria en función de los requisitos de compilación.

   La imagen final se etiqueta con "buildtools2017:latest" para que se pueda ejecutar fácilmente en un contenedor como "buildtools2017" ya que la etiqueta "latest" es el valor predeterminado si no se especifica ninguna etiqueta. Si quiere usar una versión específica de Visual Studio Build Tools 2017 en un [escenario más avanzado](advanced-build-tools-container.md), en su lugar se podría etiquetar el contenedor con un número de compilación de Visual Studio específico además de "latest", para que los contenedores puedan usar una versión determinada de forma coherente.

## <a name="step-6-using-the-built-image"></a>Paso 6. Uso de la imagen compilada

Ahora que se ha creado una imagen, también se puede ejecutar en un contenedor para realizar compilaciones interactivas y automatizadas. En el ejemplo se usa el símbolo del sistema para desarrolladores, por lo que PATH y otras variables de entorno ya están configuradas.

1. Abra un símbolo del sistema.
2. Ejecute el contenedor para iniciar un entorno de PowerShell con todas las variables de entorno del desarrollador establecidas:

   ```shell
   docker run -it buildtools2017
   ```

Para usar esta imagen para el flujo de trabajo de CI/CD, puede publicarla en su propio [Azure Container Registry](https://azure.microsoft.com/services/container-registry) o en otro [registro de Docker](https://docs.docker.com/registry/deploying) interno para que los servidores solo tengan que extraerla.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Ejemplo avanzado de contenedores](advanced-build-tools-container.md)
* [Problemas conocidos de contenedores](build-tools-container-issues.md)
* [Identificadores de componentes y cargas de trabajo de Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
