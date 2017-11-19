---
title: "Cómo: administrar varios subprocesos en código administrado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c246c8be1d10893b018d5d0c5727d4af42efdc6b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>Cómo: administrar varios subprocesos en código administrado
Si tiene una extensión de VSPackage administrada que llama a métodos asincrónicos o tiene operaciones que se ejecutan en subprocesos distintos del subproceso de interfaz de usuario de Visual Studio, debe seguir las instrucciones que se indica a continuación. Puede que el subproceso de interfaz de usuario siga respondiendo porque no es necesario esperar el trabajo en otro subproceso que se complete. Puede hacer que el código sea más eficaz, porque no tiene subprocesos adicionales que ocupan espacio de pila y lo hacer que sea más confiables y fáciles de depurar, puesto que evitar los interbloqueos y se bloquea.  
  
 En general, puede cambiar desde el subproceso de interfaz de usuario a un subproceso diferente, o viceversa. Cuando el método vuelve, el subproceso actual es el subproceso de la que se llamó originalmente.  
  
> [!IMPORTANT]
>  Las instrucciones siguientes utilizan las API en el <xref:Microsoft.VisualStudio.Threading> espacio de nombres, en particular, la <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> clase. Las API en este espacio de nombres son una Novedades de [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Puede obtener una instancia de un <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> desde el <xref:Microsoft.VisualStudio.Shell.ThreadHelper> propiedad `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Cambiar desde el subproceso de interfaz de usuario a un subproceso en segundo plano  
  
1.  Si se encuentra en el subproceso de interfaz de usuario y desea hacer el trabajo asincrónico en un subproceso en segundo plano, use Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  Si se encuentra en el subproceso de interfaz de usuario y que desea bloquear de forma sincrónica mientras está realizando trabajo en un subproceso en segundo plano, use la <xref:System.Threading.Tasks.TaskScheduler> propiedad `TaskScheduler.Default` en <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Cambio de un subproceso en segundo plano al subproceso de interfaz de usuario  
  
1.  Si se encuentra en un subproceso en segundo plano y desea realizar alguna acción en el subproceso de interfaz de usuario, use <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Puede usar el <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> método para cambiar al subproceso de interfaz de usuario. Este método envía un mensaje al subproceso de interfaz de usuario con la continuación del método asincrónico actual y también se comunica con el resto de subproceso framework para establecer la prioridad correcta y evitar los interbloqueos.  
  
     Si el método de subproceso de fondo no es asincrónico y no se puede convertir asincrónico, todavía puede usar el `await` sintaxis para cambiar al subproceso de interfaz de usuario ajustando el trabajo con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, como en este ejemplo:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```