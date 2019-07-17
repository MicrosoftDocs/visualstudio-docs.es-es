---
title: Procedimiento Cambiar a otro subproceso durante la depuración | Documentos de Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68176516"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Procedimiento Cambio a otro subproceso durante la depuración
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al depurar una aplicación multithreading, puede utilizar uno de los métodos existentes para intercambiar entre el contexto del subproceso en el que ha estado trabajando y otro subproceso.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Para pasar a otro subproceso que aparezca en la ventana Subprocesos  
  
- Haga doble clic en el subproceso.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Para cambiar a un subproceso en una ventana de código fuente  
  
- En el medianil izquierdo, haga clic en un indicador de subproceso, apunte a **cambie a**y, a continuación, haga clic en el nombre del subproceso al que desea cambiar. El menú contextual muestra únicamente los subprocesos de esa ubicación concreta.  
  
     Si no aparece ningún indicador, haga clic en el **subprocesos** ventana y compruebe que **Mostrar subprocesos en código fuente** está seleccionada.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Para cambiar a un subproceso en la barra de herramientas Ubicación de depuración  
  
1. En el **ubicación de depuración** barra de herramientas, haga clic en el **subprocesos** cuadro.  
  
2. En la lista, haga clic en el subproceso al que desee cambiar.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
