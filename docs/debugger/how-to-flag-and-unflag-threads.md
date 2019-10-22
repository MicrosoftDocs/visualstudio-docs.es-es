---
title: Procedimiento Marcar y desmarcar subprocesos | Documentos de Microsoft
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
ms.openlocfilehash: e63f081ff54a18bb4b5ca5c1cbdf947670f10a7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906730"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>Procedimiento Marcar y desmarcar subprocesos (C#, Visual Basic, C++)

Puede marcar un subproceso que desea prestar atención especial con un icono en el **subprocesos**, **pilas paralelas** (vista de subprocesos), **inspección paralela**y  **Subprocesos de GPU** windows. Este icono ayuda a distinguir estos subprocesos marcados de otros.

Los subprocesos marcados también reciben un tratamiento especial en el **subprocesos** lista el **ubicación de depuración** barra de herramientas y en las otras ventanas de depuración multiproceso. Puede mostrar todos los subprocesos o solo subprocesos marcados en el **subprocesos** lista o en las otras ventanas.

### <a name="to-flag-or-unflag-a-thread"></a>Para marcar o quitar marcador de un subproceso

- En el **subprocesos** o **inspección paralela** , busque el subproceso que esté interesado y haga clic en el icono de marca para seleccionar o borrar la marca.
- En el **pilas paralelas** ventana, el botón secundario en un subproceso o el grupo de subprocesos y seleccione **marca / \<subproceso >** o **Quitar marcador / \<subproceso >**.

### <a name="to-unflag-all-threads"></a>Para quitar los marcadores de todos los subprocesos

- En la ventana **Subprocesos**, haga clic con el botón derecho del mouse en cualquier subproceso y, a continuación, haga clic en **Quitar marca de todos los subprocesos**.
- En el **inspección paralela** ventana, seleccione todos los subprocesos marcados y, a continuación, haga clic en y seleccione **Quitar marcador**.

### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados

- Elija la **mostrar solo subprocesos de marcados** botón en una de las ventanas de depuración multiproceso.

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
- [Tutorial: Depurar aplicaciones multiproceso con la ventana subprocesos](../debugger/how-to-use-the-threads-window.md)