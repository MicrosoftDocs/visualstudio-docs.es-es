---
title: Depuración de .NET Core en Linux
description: Depure .NET Core en Linux con Secure Shell (SSH) creando asociaciones a un proceso. Prepare su aplicación para la depuración. Compile e implemente la aplicación. Asocie el depurador.
ms.custom: SEO-VS-2020
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99bfd1df6d977830e5b8e332efa3d0af653d3aec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934616"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>Depuración de .NET Core en Linux con SSH mediante la asociación a un proceso

A partir de Visual Studio 2017, puede crear asociaciones a los procesos de .NET Core que se ejecutan en una implementación de Linux local o remota a través de SSH. En este artículo se describe cómo configurar la depuración y cómo depurar. Para conocer los escenarios de depuración con contenedores de Docker, consulte [Asociación a procesos que se ejecutan en contenedores de Docker](../debugger/attach-to-process-running-in-docker-container.md) y el artículo sobre las [herramientas de contenedor](../containers/edit-and-refresh.md). Para depurar Linux en WSL 2 desde Visual Studio (sin asociar al proceso), vea [Depuración de aplicaciones de .NET Core en WSL 2 con Visual Studio](../debugger/debug-dotnet-core-in-wsl-2.md).

## <a name="prerequisites"></a>Requisitos previos

- En el equipo de Visual Studio, debe instalar la carga de trabajo **Desarrollo de ASP.NET y web** o bien la carga de trabajo **Desarrollo multiplataforma de .NET Core**.

- En el servidor Linux, debe instalar el servidor SSH, descomprimirlo e instalarlo con curl o wget. Por ejemplo, en Ubuntu puede hacerlo mediante la ejecución de:

  ``` cmd
  sudo apt-get install openssh-server unzip curl
  ```

- En el servidor Linux, [instale el entorno de ejecución de .NET en Linux](/dotnet/core/install/linux) y busque la página que coincida con la distribución de Linux (por ejemplo, Ubuntu). El SDK de .NET no es necesario.

- Para obtener instrucciones completas sobre ASP.NET Core, consulte [Hospedar ASP.NET Core en Linux con Nginx](/aspnet/core/host-and-deploy/linux-nginx) y [Hospedar ASP.NET Core en Linux con Apache](/aspnet/core/host-and-deploy/linux-apache).

## <a name="prepare-your-application-for-debugging"></a>Preparación de la aplicación para la depuración

Para preparar la aplicación para su depuración:

- Considere la posibilidad de usar una configuración de depuración al compilar la aplicación. Es mucho más difícil depurar el código compilado comercial (una configuración de versión) que el código compilado por depuración. Si necesita usar una configuración de versión, deshabilite primero Solo mi código. Para deshabilitar esta configuración, elija **Herramientas** > **Opciones** > **Depuración** y, a continuación, anule la selección de **Habilitar Solo mi código**.

- Asegúrese de que el proyecto está configurado para generar [archivos PDB portátiles](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (que es la configuración predeterminada) y compruebe que los PBD están en la misma ubicación que el archivo DLL. Para configurarlo en Visual Studio, haga clic con el botón derecho en el proyecto y, a continuación, elija **Propiedades** > **Compilar** > **Configuración avanzada** > **Información de depuración**.

## <a name="build-and-deploy-the-application"></a>Compilar e implementar la aplicación

Puede usar varios métodos para implementar la aplicación antes de la depuración. Por ejemplo, se puede:

- Copiar orígenes en el equipo de destino y compilar con ```dotnet build``` en la máquina Linux.

- Compilar la aplicación en Windows y transferir los artefactos de compilación a la máquina Linux. (Los artefactos de compilación se componen de la propia aplicación, los PDB portátiles, las bibliotecas en tiempo de ejecución de las que pueden depender y el archivo *.deps.json*).

Cuando se implemente la aplicación, inicie la aplicación.

## <a name="attach-the-debugger"></a>Asociar el depurador

Cuando la aplicación se ejecuta en la máquina de Linux, está listo para asociar el depurador.

1. En Visual Studio, seleccione **Depurar** > **Asociar al proceso...**

1. En la lista **Tipo de conexión**, seleccione **SSH**.

1. Cambie el **Destino de conexión** a la dirección IP o el nombre de host del equipo de destino.

   Si aún no ha proporcionado credenciales, se le pedirá que escriba una contraseña o un archivo de clave privada.

   No es necesario configurar ningún puerto, excepto aquel en el que se ejecuta el servidor SSH.

1. Busque el proceso que desea depurar.

   El código se ejecuta en un nombre de proceso único o en un proceso denominado dotnet. Para encontrar el proceso que le interesa, consulte la columna **Título**, que muestra los argumentos de la línea de comandos para el proceso.

   En el ejemplo siguiente, verá una lista de procesos de un equipo Linux remoto a través de un transporte SSH mostrado en el cuadro de diálogo **Asociar al proceso**.

   ![Asociación al proceso de Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Elija **Asociar**.

1. En el cuadro de diálogo que aparece, seleccione el tipo de código que desea depurar. Elija **Administrado (.NET Core para Unix)** .

1. Use las características de depuración de Visual Studio para depurar la aplicación.

   En el ejemplo siguiente, verá que el depurador de Visual Studio se detuvo en un punto de interrupción en el código que se ejecuta en una máquina remota de Linux.

   ![Llegar a un punto de interrupción](media/remote-debug-linux-over-ssh-hit-breakpoint.png)