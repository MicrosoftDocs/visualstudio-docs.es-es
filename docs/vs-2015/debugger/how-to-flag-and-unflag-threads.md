---
title: Procedimiento Marcar y desmarcar subprocesos | Documentos de Microsoft
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
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6d6a49dd9b90172686a90d92e6b630dd70b5cf0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189436"
---
# <a name="how-to-flag-and-unflag-threads"></a>Procedimiento Marcado y desmarcado de subprocesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede marcar un subproceso que desea prestar atención especial con un icono en el **subprocesos**, **pilas paralelas**, **inspección paralela**, y **GPU Subprocesos** windows. Este icono ayuda a distinguir estos subprocesos marcados de otros.  
  
 Los subprocesos marcados también reciben un tratamiento especial en el **subprocesos** lista el **ubicación de depuración** barra de herramientas. Esta lista puede mostrar todos los subprocesos o solo los marcados. Al marcar un subproceso, el **subproceso** lista cambia automáticamente para mostrar sólo subprocesos marcados, pero puede cambiarla a mostrar todos los subprocesos según corresponda.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Para marcar o desmarcar un subproceso utilizando la ventana Subprocesos  
  
- En el **subprocesos** , busque el subproceso que esté interesado y haga clic en el icono de marca para seleccionar o borrar la marca.  
  
### <a name="to-unflag-all-threads"></a>Para quitar los marcadores de todos los subprocesos  
  
- En la ventana **Subprocesos**, haga clic con el botón derecho del mouse en cualquier subproceso y, a continuación, haga clic en **Quitar marca de todos los subprocesos**.  
  
### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados  
  
- Elija el botón de marcador en la ventana de depuración.  
  
### <a name="to-flag-just-my-code"></a>Para marcar Solo mi código  
  
1. En la barra de herramientas de la parte superior de la ventana **Subprocesos**, haga clic en el icono de marca.  
  
2. En la lista desplegable **Marcar solo mi código**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Para marcar subprocesos que están asociados a módulos seleccionados  
  
1. En la barra de herramientas de la parte superior de la ventana **Subprocesos**, haga clic en el icono de marca.  
  
2. En la lista desplegable, haga clic en **Marcar selección de módulos personalizados**.  
  
3. En el cuadro de diálogo **Seleccionar módulos**, seleccione los módulos que desea.  
  
4. (Opcional) En el cuadro **Buscar**, escriba una cadena para buscar módulos concretos.  
  
5. Haga clic en **OK**.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Tutorial: Depuración de una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md)
