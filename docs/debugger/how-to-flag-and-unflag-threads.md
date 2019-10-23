---
title: 'Cómo: Marcar y quitar marcadores de subprocesos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68a2ce8b6ec429b3f7f5cd782c3dac52602eff16
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733236"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>Cómo: marcar y desmarcar subprocesos (C#, C++Visual Basic,)

Puede marcar un subproceso al que desea prestar atención especial si lo marca con un icono **en las ventanas subprocesos**, **pilas paralelas** (vista de subproceso), **inspección paralela**y **subprocesos de GPU** . Este icono ayuda a distinguir estos subprocesos marcados de otros.

Los subprocesos marcados también reciben un tratamiento especial en la lista de **subprocesos** de la barra de herramientas de **Ubicación de depuración** y en las otras ventanas de depuración multiproceso. Puede mostrar todos los subprocesos o solo los subprocesos marcados en la lista de **subprocesos** o en las otras ventanas.

### <a name="to-flag-or-unflag-a-thread"></a>Para marcar o quitar marcador de un subproceso

- En la ventana **subprocesos** o **inspección paralela** , busque el subproceso que le interese y haga clic en el icono de marca para activar o desactivar la marca.
- En la ventana **pilas paralelas** , haga clic con el botón derecho en un subproceso o grupo de subprocesos y seleccione **Flag/\<thread >** o **Unflag/\<thread >** .

### <a name="to-unflag-all-threads"></a>Para quitar los marcadores de todos los subprocesos

- En la ventana **Subprocesos**, haga clic con el botón derecho del mouse en cualquier subproceso y, a continuación, haga clic en **Quitar marca de todos los subprocesos**.
- En la ventana **inspección paralela** , seleccione todos los subprocesos marcados, haga clic con el botón derecho y seleccione **Quitar marcador**.

### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados

- Elija el botón **Mostrar solo subprocesos marcados** en una de las ventanas de depuración multiproceso.

### <a name="to-flag-just-my-code"></a>Para marcar Solo mi código

1. En la barra de herramientas de la parte superior de la ventana **Subprocesos**, haga clic en el icono de marca.

2. En la lista desplegable **Marcar solo mi código**.

### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Para marcar subprocesos que están asociados a módulos seleccionados

1. En la barra de herramientas de la parte superior de la ventana **Subprocesos**, haga clic en el icono de marca.

2. En la lista desplegable, haga clic en **Marcar selección de módulos personalizados**.

3. En el cuadro de diálogo **Seleccionar módulos**, seleccione los módulos que desea.

4. (Opcional) En el cuadro **Buscar**, escriba una cadena para buscar módulos concretos.

5. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también
- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Introducción a la depuración de aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md)
- [Tutorial: depurar aplicaciones multiproceso mediante la ventana subprocesos](../debugger/how-to-use-the-threads-window.md)