---
title: Administración de varios subprocesos en código administrado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c1438c7425ba3d3fe1071fb2d06d7bc3345d900
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186737"
---
# <a name="managing-multiple-threads-in-managed-code"></a>Administración de varios subprocesos en código administrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si tiene una extensión VSPackage administrada que llama a métodos asincrónicos o tiene operaciones que se ejecutan en subprocesos distintos del subproceso de interfaz de usuario de Visual Studio, debe seguir las instrucciones que se indican a continuación. Puede que el subproceso de interfaz de usuario siga respondiendo porque no necesita esperar por el trabajo en otro subproceso para completar. Puede hacer que el código sea más eficaz, porque no tiene subprocesos adicionales que ocupan espacio de pila y hacer más fiable y fácil de depurar porque evitar interbloqueos y bloqueos.  
  
 En general, puede cambiar desde el subproceso de interfaz de usuario a un subproceso diferente, o viceversa. Cuando el método vuelve, el subproceso actual es el subproceso desde el que se llamó originalmente.  
  
> [!IMPORTANT]
>  Las instrucciones siguientes utilizan las API en el <xref:Microsoft.VisualStudio.Threading> espacio de nombres, en particular, el <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> clase. Las API en este espacio de nombres son nuevas en [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Puede obtener una instancia de un <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> desde el <xref:Microsoft.VisualStudio.Shell.ThreadHelper> propiedad `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Cambiar desde el subproceso de interfaz de usuario a un subproceso en segundo plano  
  
1.  Si se encuentra en el subproceso de interfaz de usuario y desea hacer el trabajo asincrónico en un subproceso en segundo plano, use Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  Si se encuentra en el subproceso de interfaz de usuario y desea bloquear de forma sincrónica mientras esté realizando el trabajo en un subproceso en segundo plano, use la <xref:System.Threading.Tasks.TaskScheduler> propiedad `TaskScheduler.Default` dentro de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Cambiar de un subproceso en segundo plano al subproceso de interfaz de usuario  
  
1.  Si se encuentra en un subproceso en segundo plano y desea hacer algo en el subproceso de interfaz de usuario, use <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Puede usar el <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> método para cambiar al subproceso de interfaz de usuario. Este método envía un mensaje al subproceso de interfaz de usuario con la continuación del método asincrónico actual y también se comunica con el resto del marco subprocesamiento para establecer la prioridad correcta y evitar los interbloqueos.  
  
     Si el método de subproceso en segundo plano no es asincrónico y no se puede convertir asincrónico, puede usar el `await` sintaxis para cambiar al subproceso de UI al ajustar su trabajo con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, como en este ejemplo:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```

