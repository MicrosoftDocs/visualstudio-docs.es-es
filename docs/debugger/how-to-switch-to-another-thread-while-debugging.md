---
title: Cambiar a otro subproceso durante la depuración
ms.custom: seodec18
ms.date: 04/27/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 163d14de4880ed1c5e2ae6a3170ec5ae1ae47485
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005194"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Procedimiento Cambiar a otro subproceso durante la depuración en Visual Studio (C#, Visual Basic, C++)
Cuando se depura una aplicación multiproceso, puede usar cualquiera de los diversos métodos para cambiar desde el subproceso que ha estado trabajando con a otro subproceso.

> [!NOTE]
> Si desea controlar el orden en que se ejecutan los subprocesos, deberá [inmovilizar y reanudar subprocesos](../debugger/get-started-debugging-multithreaded-apps.md).

Al examinar los subprocesos en el editor de código y las distintas ventanas de depuración multiproceso, la flecha amarilla indica el subproceso actual. Una flecha verde con una cola rizada indica que un subproceso distinto del actual tiene el contexto actual del depurador.
  
### <a name="to-switch-to-any-thread-that-appears"></a>Para cambiar a cualquier subproceso que aparece 
  
-   En el **subprocesos** o **inspección paralela** ventana, haga doble clic en el subproceso.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Para cambiar a un subproceso en una ventana de código fuente  
  
-   En el medianil izquierdo, haga clic en un icono de marcador de subproceso ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker"), apunte a **cambie a**y, a continuación, haga clic en el nombre del subproceso al que desea cambiar . El menú contextual muestra únicamente los subprocesos de esa ubicación concreta.  
  
     Si no hay marcadores de subprocesos aparecen, haga clic en el **subprocesos** ventana y compruebe que **Mostrar subprocesos en código fuente** está seleccionada.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Para cambiar a un subproceso en la barra de herramientas Ubicación de depuración  
  
1.  En el **ubicación de depuración** barra de herramientas, haga clic en el **subprocesos** lista.  
  
2.  En la lista, haga clic en el subproceso al que desee cambiar.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
