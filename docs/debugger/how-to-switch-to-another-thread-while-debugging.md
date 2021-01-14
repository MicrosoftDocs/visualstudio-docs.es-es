---
title: Cambiar a otro subproceso durante la depuración
description: Revise los distintos métodos que existen para cambiar a otro subproceso durante la depuración de una aplicación multiproceso en Visual Studio.
ms.custom: SEO-VS-2020, seodec18
ms.date: 04/27/2017
ms.topic: how-to
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
ms.openlocfilehash: 8df37beafe7a6c8f88631568ea9eb36394c105a5
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150722"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>Procedimiento Cambio a otro subproceso durante la depuración en Visual Studio (C#, Visual Basic, C++)
Al depurar una aplicación multiproceso, puede usar cualquiera de los métodos existentes para pasar del subproceso en el que ha estado trabajando a otro.

> [!NOTE]
> Si quiere controlar el orden en el que se ejecutan los subprocesos, debe [inmovilizar y reanudar subprocesos](../debugger/get-started-debugging-multithreaded-apps.md).

Al examinar los subprocesos en el editor de código y las distintas ventanas de depuración multiproceso, la flecha amarilla indica el subproceso actual. Una flecha verde con un extremo curvo indica que un subproceso no actual tiene el contexto del depurador actual.

### <a name="to-switch-to-any-thread-that-appears"></a>Para pasar a otro subproceso que aparezca

- En la ventana **Subprocesos** o en **Inspección paralela**, haga doble clic en el subproceso.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>Para cambiar a un subproceso en una ventana de código fuente

- En el medianil izquierdo, haga clic con el botón derecho en un icono de marcador de un subproceso, ![Marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker"), seleccione **Cambiar a** y haga clic en el nombre del subproceso al que quiere cambiar. El menú contextual muestra únicamente los subprocesos de esa ubicación concreta.

     Si no aparece ningún marcador de subproceso, haga clic con el botón derecho en la ventana **Subprocesos** y compruebe que **Mostrar subprocesos en código fuente** está seleccionado.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Para cambiar a un subproceso en la barra de herramientas Ubicación de depuración

1. En la barra de herramientas **Ubicación de depuración**, haga clic en la lista **Subproceso**.

2. En la lista, haga clic en el subproceso al que desee cambiar.

## <a name="see-also"></a>Vea también
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
