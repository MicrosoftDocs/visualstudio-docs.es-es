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
ms.openlocfilehash: 11ad6280ad1213008bbb8ca8f6311ca34231d308
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732442"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Cómo: cambiar a otro subproceso durante la depuración en VisualC#Studio (, C++Visual Basic,)
Al depurar una aplicación multiproceso, puede usar cualquiera de los diversos métodos para cambiar del subproceso con el que ha estado trabajando a otro subproceso.

> [!NOTE]
> Si desea controlar el orden en el que se ejecutan los subprocesos, debe [inmovilizar y reanudar los subprocesos](../debugger/get-started-debugging-multithreaded-apps.md).

Al examinar los subprocesos en el editor de código y las distintas ventanas de depuración multiproceso, la flecha amarilla indica el subproceso actual. Una flecha verde con una cola tipográfica indica que un subproceso no actual tiene el contexto del depurador actual.

### <a name="to-switch-to-any-thread-that-appears"></a>Para cambiar a cualquier subproceso que aparezca

- En la ventana **subprocesos** o **inspección paralela** , haga doble clic en el subproceso.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Para cambiar a un subproceso en una ventana de código fuente

- En el margen interno izquierdo, haga clic con el botón secundario en un icono de marcador de subproceso ![marcador](../debugger/media/dbg-thread-marker.png "ThreadMarker")de subproceso, seleccione **cambiar a**y, a continuación, haga clic en el nombre del subproceso al que desea cambiar. El menú contextual muestra únicamente los subprocesos de esa ubicación concreta.

     Si no aparecen marcadores de subprocesos, haga clic con el botón secundario en la ventana **subprocesos** y compruebe que está seleccionada la opción **Mostrar subprocesos en origen** .

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Para cambiar a un subproceso en la barra de herramientas Ubicación de depuración

1. En la barra de herramientas **Ubicación de depuración** , haga clic en la lista **subproceso** .

2. En la lista, haga clic en el subproceso al que desee cambiar.

## <a name="see-also"></a>Vea también
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
