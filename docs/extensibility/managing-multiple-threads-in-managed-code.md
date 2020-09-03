---
title: 'Cómo: administrar varios subprocesos en código administrado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe5cef9f7aebcbfc93ffd057a109647e45b5967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387075"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Cómo: administrar varios subprocesos en código administrado
Si tiene una extensión VSPackage administrada que llama a métodos asincrónicos o tiene operaciones que se ejecutan en subprocesos distintos del subproceso de interfaz de usuario de Visual Studio, debe seguir las instrucciones que se indican a continuación. Puede mantener la capacidad de respuesta del subproceso de la interfaz de usuario porque no es necesario esperar a que se complete el trabajo en otro subproceso. Puede hacer que el código sea más eficaz, ya que no tiene subprocesos adicionales que ocupen espacio de pila, y puede hacer que sea más confiable y más fácil de depurar, ya que evita los interbloqueos y el código que no responde.

 En general, puede cambiar del subproceso de interfaz de usuario a otro subproceso, o viceversa. Cuando el método devuelve, el subproceso actual es el subproceso del que se llamó originalmente.

> [!IMPORTANT]
> Las instrucciones siguientes usan las API del <xref:Microsoft.VisualStudio.Threading> espacio de nombres, en particular, la <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> clase. Las API de este espacio de nombres son nuevas en [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] . Puede obtener una instancia de a <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> partir de la <xref:Microsoft.VisualStudio.Shell.ThreadHelper> propiedad `ThreadHelper.JoinableTaskFactory` .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Cambiar del subproceso de interfaz de usuario a un subproceso en segundo plano

1. Si está en el subproceso de la interfaz de usuario y desea realizar el trabajo asincrónico en un subproceso en segundo plano, use `Task.Run()` :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Si se encuentra en el subproceso de la interfaz de usuario y desea bloquearse sincrónicamente mientras realiza el trabajo en un subproceso en segundo plano, use la <xref:System.Threading.Tasks.TaskScheduler> propiedad `TaskScheduler.Default` en <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Cambiar de un subproceso en segundo plano al subproceso de interfaz de usuario

1. Si se encuentra en un subproceso en segundo plano y desea hacer algo en el subproceso de la interfaz de usuario, use <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Puede usar el <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> método para cambiar al subproceso de la interfaz de usuario. Este método envía un mensaje al subproceso de la interfaz de usuario con la continuación del método asincrónico actual y también se comunica con el resto del marco de trabajo de subprocesos para establecer la prioridad correcta y evitar los interbloqueos.

     Si el método de subproceso en segundo plano no es asincrónico y no puede convertirlo en asincrónico, puede seguir usando la `await` sintaxis para cambiar al subproceso de la interfaz de usuario mediante el ajuste del trabajo con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> , como en este ejemplo:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
