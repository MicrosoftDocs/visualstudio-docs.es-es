---
title: Procedimiento para marcar y quitar marcadores de subprocesos | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189436"
---
# <a name="how-to-flag-and-unflag-threads"></a>Cómo: Marcar y quitar marcadores de subprocesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede marcar un subproceso al que desea prestar atención especial marcándolos con un icono **en las ventanas subprocesos**, **pilas paralelas**, **inspección paralela**y **subprocesos de GPU** . Este icono ayuda a distinguir estos subprocesos marcados de otros.  
  
 Los subprocesos marcados también reciben un tratamiento especial en la lista de **subprocesos** de la barra de herramientas **Ubicación de depuración** . Esta lista puede mostrar todos los subprocesos o solo los marcados. Al marcar un subproceso, la lista de **subprocesos** cambia automáticamente para mostrar solo los subprocesos marcados, pero puede cambiarla de nuevo para mostrar todos los subprocesos según corresponda.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Para marcar o desmarcar un subproceso utilizando la ventana Subprocesos  
  
- En la ventana **subprocesos** , busque el subproceso que le interese y haga clic en el icono de marca para activar o desactivar la marca.  
  
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
  
5. Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Consulte también  
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Tutorial: Depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md)
