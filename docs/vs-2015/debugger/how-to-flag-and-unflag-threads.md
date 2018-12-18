---
title: 'Cómo: marcar y desmarcar subprocesos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 5816007476da56321e58182e636b54a5a5697994
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817495"
---
# <a name="how-to-flag-and-unflag-threads"></a>Cómo: Marcar y quitar marcadores de subprocesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede marcar un subproceso que desea prestar atención especial con un icono en el **subprocesos**, **pilas paralelas**, **inspección paralela**, y **GPU Subprocesos** windows. Este icono ayuda a distinguir estos subprocesos marcados de otros.  
  
 Los subprocesos marcados también reciben un tratamiento especial en el **subprocesos** lista el **ubicación de depuración** barra de herramientas. Esta lista puede mostrar todos los subprocesos o solo los marcados. Al marcar un subproceso, el **subproceso** lista cambia automáticamente para mostrar sólo subprocesos marcados, pero puede cambiarla a mostrar todos los subprocesos según corresponda.  
  
### <a name="to-flag-or-unflag-a-thread-by-using-the-threads-window"></a>Para marcar o desmarcar un subproceso utilizando la ventana Subprocesos  
  
-   En el **subprocesos** , busque el subproceso que esté interesado y haga clic en el icono de marca para seleccionar o borrar la marca.  
  
### <a name="to-unflag-all-threads"></a>Para quitar los marcadores de todos los subprocesos  
  
-   En el **subprocesos** ventana, haga clic en cualquier subproceso y, a continuación, haga clic en **desmarcar todos los subprocesos**.  
  
### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados  
  
-   Elija el botón de marcador en la ventana de depuración.  
  
### <a name="to-flag-just-my-code"></a>Para marcar Solo mi código  
  
1.  En la barra de herramientas en la parte superior de la **subprocesos** ventana, haga clic en el icono de marca.  
  
2.  En la lista desplegable, haga clic en **marcar solo mi código**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Para marcar subprocesos que están asociados a módulos seleccionados  
  
1.  En la barra de herramientas de la **subprocesos** ventana, haga clic en el icono de marca.  
  
2.  En la lista desplegable, haga clic en **Marcar selección de módulos personalizados**.  
  
3.  En el **seleccione módulos** cuadro de diálogo, seleccione los módulos que desee.  
  
4.  (Opcional) En el **búsqueda** , escriba una cadena de búsqueda de módulos específicos.  
  
5.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Tutorial: Depurar una aplicación multiproceso](../debugger/walkthrough-debugging-a-multithreaded-application.md)



