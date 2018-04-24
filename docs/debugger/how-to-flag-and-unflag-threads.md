---
title: 'Cómo: marcar y quitar marcadores de subprocesos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 052c9d65e833152c0d3d3f67eda41742119eccaf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-flag-and-unflag-threads"></a>Cómo: Marcar y quitar marcadores de subprocesos
Puede marcar un subproceso al que desea prestar atención especial con un icono en el **subprocesos**, **pilas paralelas** (vista de subprocesos), **inspección paralela**y  **Subprocesos de GPU** windows. Este icono ayuda a distinguir estos subprocesos marcados de otros.  
  
Los subprocesos marcados también reciben un tratamiento especial en el **subprocesos** lista el **ubicación de depuración** barra de herramientas y en las demás ventanas de depuración multiproceso. Puede mostrar todos los subprocesos o solo los subprocesos marcados en el **subprocesos** lista o en las otras ventanas.
  
### <a name="to-flag-or-unflag-a-thread"></a>Para marcar o quitar marcador de un subproceso 
  
-   En el **subprocesos** o **inspección paralela** ventana, busque el subproceso que le interesa y haga clic en el icono de marca para seleccionar o borrar la marca. 
-   En el **pilas paralelas** ventana, el botón secundario en un subproceso o el grupo de subprocesos y seleccione **marca / <thread>**  o **Quitar marcador / <thread>** .
  
### <a name="to-unflag-all-threads"></a>Para quitar los marcadores de todos los subprocesos  
  
-   En el **subprocesos** ventana, haga clic en cualquier subproceso y, a continuación, haga clic en **desmarcar todos los subprocesos**.
-   En el **inspección paralela** ventana, seleccione todos los subprocesos marcados, a continuación, haga clic en y seleccione **Quitar marcador**.  
  
### <a name="to-display-only-flagged-threads"></a>Para mostrar solo los subprocesos marcados  
  
-   Elija la **mostrar sólo subprocesos de marca** botón en una de las ventanas de depuración multiproceso.  
  
### <a name="to-flag-just-my-code"></a>Para marcar Solo mi código  
  
1.  En la barra de herramientas en la parte superior de la **subprocesos** ventana, haga clic en el icono de marca.  
  
2.  En la lista desplegable, haga clic en **marcar solo mi código**.  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>Para marcar subprocesos que están asociados a módulos seleccionados  
  
1.  En la barra de herramientas de la **subprocesos** ventana, haga clic en el icono de marca.  
  
2.  En la lista desplegable, haga clic en **Marcar selección de módulos personalizados**.  
  
3.  En el **seleccione módulos** cuadro de diálogo, seleccione los módulos que desea.  
  
4.  (Opcional) En el **búsqueda** , escriba una cadena de búsqueda de módulos específicos.  
  
5.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Empezar a depurar aplicaciones multiproceso](../debugger/get-started-debugging-multithreaded-apps.md)  
 [Tutorial: Depurar aplicaciones multiproceso con la ventana subprocesos](../debugger/how-to-use-the-threads-window.md)