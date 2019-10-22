---
title: Procedimiento Establecer un nombre de subproceso en código administrado | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b800fbd2f39d75f110a059c70b87a203eb72e7d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157675"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Procedimiento Establecimiento de un nombre de subproceso en código administrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La denominación de los subprocesos es posible en cualquier edición de Visual Studio. La denominación de los subprocesos es útil para hacer el seguimiento en la ventana **Subprocesos**. Dado que el **subprocesos** ventana no está disponible en las ediciones Express de Visual Studio, la denominación tiene poca utilidad en las ediciones Express.  
  
 Para establecer un nombre de subproceso en código administrado, utilice la propiedad <xref:System.Threading.Thread.Name%2A>.  
  
## <a name="example"></a>Ejemplo  
  
```  
Public Class Needle  
    ' This method will be called when the thread is started.  
    Sub Baz()  
        Console.WriteLine("Needle Baz is running on another thread")  
    End Sub  
End Class  
  
Sub Main()  
    Console.WriteLine("Thread Simple Sample")  
    Dim oNeedle As New Needle()  
   ' Create a Thread object.   
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)  
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## <a name="see-also"></a>Vea también  
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: Establecimiento de un nombre de subproceso en código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)
