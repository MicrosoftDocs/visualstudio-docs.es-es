---
title: Depuración remota de .NET Core en Linux | Microsoft Docs
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23bc0fa990a79b1855ec382f42248a0f847c3c9c
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/29/2020
ms.locfileid: "78200870"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>Depuración remota de .NET Core con SSH

A partir de Visual Studio 2017, puede asociarse a los procesos de .NET Core que se ejecutan en Linux a través de SSH. En este artículo se describe cómo configurar la depuración y cómo depurar.

## <a name="prerequisites"></a>Requisitos previos

En el equipo de Visual Studio, debe instalar la carga de trabajo **Desarrollo de ASP.NET y web** o bien la carga de trabajo **Desarrollo multiplataforma de .NET Core**.

En el servidor Linux, debe instalar el servidor SSH, descomprimirlo e instalarlo con curl o wget. Por ejemplo, en Ubuntu puede hacerlo mediante la ejecución de:

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>Compilar e implementar la aplicación

Para preparar la aplicación para su depuración:

- Considere la posibilidad de usar una configuración de depuración al compilar la aplicación. Es mucho más difícil depurar el código compilado comercial (una configuración de versión) que el código compilado por depuración. Si necesita usar una configuración de versión, deshabilite primero Solo mi código. Para deshabilitar esta configuración, elija **Herramientas** > **Opciones** > **Depuración** y, a continuación, anule la selección de **Habilitar Solo mi código**.

- Asegúrese de que el proyecto está configurado para generar [archivos PDB portátiles](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (que es la configuración predeterminada) y asegúrese de que los PBD están en la misma ubicación que el archivo DLL. Para configurarlo en Visual Studio, haga clic con el botón derecho en el proyecto y, a continuación, elija **Propiedades** > **Compilar** > **Configuración avanzada** > **Información de depuración**.

Puede usar varios métodos para implementar la aplicación antes de la depuración. Por ejemplo, se puede:

- Copiar orígenes en el equipo de destino y compilar con ```dotnet build``` en la máquina Linux.

- Compilar la aplicación en Windows y transferir los artefactos de compilación a la máquina Linux. (Los artefactos de compilación se componen de la propia aplicación, las bibliotecas en tiempo de ejecución de las que puede depender y el archivo *.deps.json*).

## <a name="attach-the-debugger"></a>Asociar el depurador

Una vez configurados los equipos, inicie la aplicación en la máquina Linux y, de este modo, estará listo para asociar el depurador.

1. En Visual Studio, seleccione **Depurar** > **Asociar al proceso...**

1. En la lista **Tipo de conexión**, seleccione **SSH**.

1. Cambie el **Destino de conexión** a la dirección IP o el nombre de host del equipo de destino.

1. Busque el proceso que desea depurar.

   El código se ejecuta en un nombre de proceso único o en un proceso denominado dotnet. Para encontrar el proceso que le interesa, consulte la columna **Título**, que muestra los argumentos de la línea de comandos para el proceso.

   En el ejemplo siguiente, verá una lista de procesos de un equipo Linux remoto a través de un transporte SSH mostrado en el cuadro de diálogo **Asociar al proceso**.

   ![Asociación al proceso de Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Elija **Asociar**.

1. En el cuadro de diálogo que aparece, seleccione el tipo de código que desea depurar. Elija **Administrado (.NET Core para Unix)** .

1. Use las características de depuración de Visual Studio para depurar la aplicación.

   En el ejemplo siguiente, verá que el depurador de Visual Studio se detuvo en un punto de interrupción en el código que se ejecuta en una máquina remota de Linux.

   ![Llegar a un punto de interrupción](media/remote-debug-linux-over-ssh-hit-breakpoint.png)