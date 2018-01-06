---
title: "Cómo: depurar código XAML con el Diseñador de flujo de trabajo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: uwp
ms.openlocfilehash: 32144a651fe9178da8bc87a10377e2c4d086d398
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Depurar XAML con el Diseñador de flujo de trabajo
Los flujos de trabajo se definen en términos de código XAML. La representación de la interfaz de usuario de flujo de trabajo se compila sobre el árbol XAML que define el flujo de trabajo. La experiencia de depuración es similar a la depuración de flujos de trabajo en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Por ejemplo, mientras se depura el código XAML, la ventanas de valores locales, de inspección y de subprocesos se comportan de la misma forma que la depuración de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Además, la vista de pila de llamadas durante la depuración de código XAML es una vista jerárquica basada en líneas del flujo de ejecución para el flujo de trabajo.  
  
> [!NOTE]
>  Si el XAML para un flujo de trabajo se encuentra en el mismo ensamblado que las actividades, la parte del ensamblado de los nombres de clase no se incluye. Sin esta parte de los nombres de clase (actividad), el XAML no se puede cargar en tiempo de ejecución. No se recomienda definir actividades en el mismo espacio de nombres que el proyecto principal; si no, el XAML necesitará editarse a mano después de editarse en el diseñador.  
  
### <a name="to-debug-workflow-xaml"></a>Para depurar el XAML de flujo de trabajo  
  
1.  Abra un flujo de trabajo o proyecto de actividades en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Establecer un punto de interrupción en la actividad o actividades que desea depurar tal y como se describe en [Cómo: establecer puntos de interrupción en flujos de trabajo](../workflow-designer/how-to-set-breakpoints-in-workflows.md).  
  
3.  Haga clic en el archivo .xaml que contiene la definición de flujo de trabajo y seleccione **ver código**. Verá un punto de interrupción que se muestra en la misma línea que la declaración del elemento XAML de la actividad para la que establece el punto de interrupción en la vista de diseño.  
  
4.  Invocar el depurador, como se describe en [Cómo: invocar el depurador de flujo de trabajo](../workflow-designer/how-to-invoke-the-workflow-debugger.md).  
  
5.  Cuando la ejecución del código llegue a uno de los puntos de interrupción, se resaltará el elemento XAML asociado a ese punto de interrupción. Para mover el siguiente punto de interrupción, use la **F10** o **F11** clave.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: establecer puntos de interrupción en flujos de trabajo](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Cómo: Invocar el depurador de flujo de trabajo](../workflow-designer/how-to-invoke-the-workflow-debugger.md)