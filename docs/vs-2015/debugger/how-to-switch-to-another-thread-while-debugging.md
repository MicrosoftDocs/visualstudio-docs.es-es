---
title: 'Cómo: cambiar a otro subproceso durante la depuración | Microsoft Docs'
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
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f481a0b1cb2142dc7dbfe11e17ac627753cebf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176516"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Cómo: Cambiar a otro subproceso durante la depuración
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al depurar una aplicación multithreading, puede utilizar uno de los métodos existentes para intercambiar entre el contexto del subproceso en el que ha estado trabajando y otro subproceso.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Para pasar a otro subproceso que aparezca en la ventana Subprocesos  
  
- Haga doble clic en el subproceso.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Para cambiar a un subproceso en una ventana de código fuente  
  
- En el margen interno izquierdo, haga clic con el botón secundario en un indicador de subproceso, seleccione **cambiar a**y, a continuación, haga clic en el nombre del subproceso al que desea cambiar. El menú contextual muestra únicamente los subprocesos de esa ubicación concreta.  
  
     Si no aparece ningún indicador, haga clic con el botón secundario en la ventana **subprocesos** y compruebe que está seleccionada la opción **Mostrar subprocesos en origen** .  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Para cambiar a un subproceso en la barra de herramientas Ubicación de depuración  
  
1. En la barra de herramientas **Ubicación de depuración** , haga clic en el cuadro **subproceso** .  
  
2. En la lista, haga clic en el subproceso al que desee cambiar.  
  
## <a name="see-also"></a>Consulte también  
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
