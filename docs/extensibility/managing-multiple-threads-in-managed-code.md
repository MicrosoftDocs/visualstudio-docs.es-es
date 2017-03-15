---
title: "Cómo: administrar varios subprocesos en código administrado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: 417dc6e5285859424dfa3b482a90f1a141cff163
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>Cómo: administrar varios subprocesos en código administrado
Si tiene una extensión VSPackage administrada que llama a métodos asincrónicos o tiene operaciones que se ejecutan en subprocesos distintos del subproceso de interfaz de usuario de Visual Studio, debe seguir las instrucciones que se indican a continuación. Puede mantener el subproceso de UI con capacidad de respuesta porque no necesita esperar al trabajo en otro subproceso complete. Puede hacer que el código sea más eficaz, porque no tiene subprocesos adicionales que ocupan espacio de pila y hacer más confiable y fácil de depurar, puesto que evita bloqueos e interbloqueos.  
  
 En general, puede cambiar del subproceso de interfaz de usuario a un subproceso diferente, o viceversa. Cuando el método vuelve, el subproceso actual es el subproceso desde el que se llamó originalmente.  
  
> [!IMPORTANT]
>  Las siguientes directrices usar las API en el <xref:Microsoft.VisualStudio.Threading>espacio de nombres, en concreto, la <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>clase.</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> </xref:Microsoft.VisualStudio.Threading> Las API en este espacio de nombres son nuevas en [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Puede obtener una instancia de un <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>desde el <xref:Microsoft.VisualStudio.Shell.ThreadHelper>propiedad `ThreadHelper.JoinableTaskFactory`.</xref:Microsoft.VisualStudio.Shell.ThreadHelper> </xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Cambiar desde el subproceso de interfaz de usuario a un subproceso en segundo plano  
  
1.  Si se encuentra en el subproceso de interfaz de usuario y desea hacer el trabajo asincrónico en un subproceso en segundo plano, use Task.Run():  
  
    ```c#  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  Si se encuentra en el subproceso de UI y desea bloquear de forma sincrónica mientras está realizando un trabajo en un subproceso en segundo plano, use la <xref:System.Threading.Tasks.TaskScheduler>propiedad `TaskScheduler.Default` en <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> </xref:System.Threading.Tasks.TaskScheduler>  
  
    ```c#  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Cambiar de un subproceso en segundo plano al subproceso de interfaz de usuario  
  
1.  Si se encuentra en un subproceso en segundo plano y desea hacer algo en el subproceso de interfaz de usuario, utilice <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>  
  
    ```c#  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Puede usar el <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>para cambiar al subproceso de UI.</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> Este método envía un mensaje al subproceso de interfaz de usuario con la continuación del método asincrónico actual y también se comunica con el resto del marco subproceso para establecer la prioridad correcta y evitar los interbloqueos.  
  
     Si el método de subproceso de segundo plano no es asincrónico y no se puede convertir asincrónico, puede usar el `await` sintaxis para cambiar al subproceso de UI ajustando el trabajo con <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, como en este ejemplo:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>  
  
    ```c#  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
