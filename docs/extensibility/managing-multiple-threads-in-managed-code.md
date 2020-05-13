---
title: 'Cómo: Administración de varios subprocesos en código administrado ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceaa0af4f57fe374cf9cf4b2dd8b4f40af74a852
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702780"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Cómo: Administrar varios subprocesos en código administrado
Si tiene una extensión VSPackage administrada que llama a métodos asincrónicos o tiene operaciones que se ejecutan en subprocesos que no sean el subproceso de interfaz de usuario de Visual Studio, debe seguir las instrucciones que se indican a continuación. Puede mantener la capacidad de respuesta del subproceso de interfaz de usuario porque no necesita esperar a que se complete el trabajo en otro subproceso. Puede hacer que el código sea más eficaz, ya que no tiene subprocesos adicionales que ocupa espacio de pila y puede hacer que sea más confiable y más fácil de depurar porque evita interbloqueos y bloqueos.

 En general, puede cambiar del subproceso de interfaz de usuario a otro subproceso, o viceversa. Cuando se devuelve el método, el subproceso actual es el subproceso desde el que se llamó originalmente.

> [!IMPORTANT]
> Las siguientes directrices usan <xref:Microsoft.VisualStudio.Threading> las API del <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> espacio de nombres, en particular, la clase. Las API de este espacio [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]de nombres son nuevas en . Puede obtener una instancia <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> de <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory`a desde la propiedad .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Cambiar del subproceso de interfaz de usuario a un subproceso en segundo plano

1. Si está en el subproceso de interfaz de usuario y `Task.Run()`desea realizar un trabajo asincrónico en un subproceso en segundo plano, utilice:

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Si está en el subproceso de interfaz de usuario y desea bloquear sincrónicamente mientras realiza el trabajo en un subproceso en segundo plano, utilice la <xref:System.Threading.Tasks.TaskScheduler> propiedad `TaskScheduler.Default` dentro <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>de:

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

1. Si está en un subproceso en segundo plano y desea <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>hacer algo en el subproceso de interfaz de usuario, utilice:

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Puede usar <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> el método para cambiar al subproceso de interfaz de usuario. Este método publica un mensaje en el subproceso de interfaz de usuario con la continuación del método asincrónico actual y también se comunica con el resto del marco de subprocesos para establecer la prioridad correcta y evitar interbloqueos.

     Si el método de subproceso en segundo plano no es asincrónico `await` y no puede hacerlo asíncrono, puede seguir usando la sintaxis para cambiar al subproceso de interfaz de usuario ajustando el trabajo con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, como en este ejemplo:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
