---
title: "Cómo: Suprimir advertencias mediante el elemento de menú | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a197170285a8f8a9d3f0cc01638557f30fd1f126
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Cómo: Suprimir advertencias mediante el elemento de menú
> [!NOTE]
>  Origen de supresión no se admite para los proyectos de sitio web.  
  
 Puede utilizar la ventana de análisis de código para suprimir las advertencias de análisis de código. Suprimir una advertencia no es el mismo que si se deshabilita. Cuando se suprime una advertencia, solo se aplica a una instancia determinada de la infracción. Otras infracciones de la misma advertencia todavía se incluirán en la ventana Lista de errores.  
  
 Después de ejecutar el análisis de código, se podría determinar que una o varias de las advertencias de análisis de código que se muestran en la ventana de análisis de código no son aplicables a su aplicación. Por ejemplo, podría determinar que el código es correcto, tal y como está. O bien, podría ser el caso que haya algunas infracciones de baja prioridad y no se corregirá en el ciclo de desarrollo actual. Independientemente del motivo, resulta útil en muchas ocasiones indicar que la advertencia no es aplicable para que los miembros del equipo sepan que se ha revisado el código y que se ha determinado que se puede suprimir la advertencia. Origen de supresión es útil porque permite colocar una supresión cerca de donde se genera la advertencia.  
  
 Puede elegir si la supresión aparecerá en el código fuente o en el archivo de supresión global. Algunas supresiones deben colocarse en el archivo de supresión global. Si este es el caso, el **en origen** opción estará deshabilitada.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Para suprimir una advertencia mediante el elemento de menú  
  
1.  En el **analizar** menú, elija **Windows** y, a continuación, elija **análisis de código**.  
  
2.  En el **análisis de código** ventana, seleccione la supresión de advertencia.  
  
3.  Elija Acciones y después elija **Suprimir mensajes**y, a continuación, elija **en origen** o **en el archivo de supresión de proyecto**.  
  
     Se suprime la advertencia concreta, y la advertencia aparece en la ventana de análisis de código con un tachado.  
  
> [!NOTE]
>  Supresiones que no tienen un destino aparecen en el archivo de supresión global.