---
title: 'Cómo: Administrar varios subprocesos en código administrado | Microsoft Docs'
description: Obtenga información sobre cómo administrar varios subprocesos en el código si la extensión VSPackage administrada llama a métodos asincrónicos o tiene operaciones fuera del Visual Studio de interfaz de usuario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 39319b748dd41c6936e7b70e20243202452fae67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903091"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Cómo: Administrar varios subprocesos en código administrado
Si tiene una extensión de VSPackage administrada que llama a métodos asincrónicos o tiene operaciones que se ejecutan en subprocesos distintos del subproceso de interfaz de usuario de Visual Studio, debe seguir las instrucciones que se indican a continuación. Puede mantener el subproceso de interfaz de usuario con capacidad de respuesta porque no es necesario esperar a que se complete el trabajo en otro subproceso. Puede hacer que el código sea más eficaz, ya que no tiene subprocesos adicionales que ocupa espacio en la pila y puede hacer que sea más confiable y fácil de depurar, ya que evita interbloqueos y código que no responde.

 En general, puede cambiar del subproceso de la interfaz de usuario a otro subproceso, o viceversa. Cuando el método devuelve un resultado, el subproceso actual es el subproceso desde el que se llamó originalmente.

> [!IMPORTANT]
> En las siguientes instrucciones se usan las API del espacio <xref:Microsoft.VisualStudio.Threading> de nombres, en particular, la <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> clase . Las API de este espacio de nombres son nuevas en [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] . Puede obtener una instancia de de de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> la <xref:Microsoft.VisualStudio.Shell.ThreadHelper> propiedad `ThreadHelper.JoinableTaskFactory` .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Cambio del subproceso de interfaz de usuario a un subproceso en segundo plano

1. Si está en el subproceso de interfaz de usuario y desea realizar un trabajo asincrónico en un subproceso en segundo plano, use `Task.Run()` :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Si está en el subproceso de interfaz de usuario y desea bloquear sincrónicamente mientras realiza el trabajo en un subproceso en segundo plano, use la <xref:System.Threading.Tasks.TaskScheduler> propiedad `TaskScheduler.Default` dentro de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Cambio de un subproceso en segundo plano al subproceso de interfaz de usuario

1. Si está en un subproceso en segundo plano y desea hacer algo en el subproceso de interfaz de usuario, use <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Puede usar el método para <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> cambiar al subproceso de interfaz de usuario. Este método envía un mensaje al subproceso de interfaz de usuario con la continuación del método asincrónico actual y también se comunica con el resto del marco de subprocesos para establecer la prioridad correcta y evitar interbloqueos.

     Si el método de subproceso en segundo plano no es asincrónico y no puede hacerlo asincrónico, puede seguir utilizando la sintaxis para cambiar al subproceso de interfaz de usuario encapsulando el trabajo con , como en este `await` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> ejemplo:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
