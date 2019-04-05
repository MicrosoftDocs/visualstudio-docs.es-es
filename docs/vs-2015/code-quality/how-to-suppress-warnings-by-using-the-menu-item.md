---
title: Filtrar Suprimir advertencias mediante el elemento de menú | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 83fd93d2e1e2e5d99f7ea8eca9f5de4ce1b4c7f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987626"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Filtrar Suprimir advertencias mediante el elemento de menú
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Origen de supresión no se admite para proyectos de sitio web.  
  
 Puede utilizar la ventana de análisis de código para suprimir las advertencias de análisis de código. Suprimir una advertencia no es el mismo que si lo deshabilitan. Al suprimir una advertencia, se aplica solo a una instancia determinada de la infracción. Otras infracciones de la misma advertencia todavía se notificará en la ventana Lista de errores.  
  
 Después de ejecutar el análisis de código, puede determinar que una o varias de las advertencias de análisis de código que se muestran en la ventana de análisis de código no son aplicables a su aplicación. Por ejemplo, podría determinar que el código es correcto tal y como está. O bien, podría ser el caso de que algunos infracciones de prioridad baja y no se corregirá en el ciclo de desarrollo actual. Independientemente del motivo, es útil con frecuencia indicar que la advertencia es que no son aplicables para que los miembros del equipo sepan que se ha revisado el código y que se determinó que se puede suprimir la advertencia. Origen de supresión es útil porque le permite colocar una supresión cerca de donde se genera la advertencia.  
  
 Puede elegir si la supresión aparecerá en el código fuente o en el archivo de supresión global. Algunas supresiones se deben colocar en el archivo de supresión global. Si es así, el **en origen** opción estará deshabilitada.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Para suprimir una advertencia mediante el uso de elemento de menú  
  
1.  En el **analizar** menú, elija **Windows** y, a continuación, elija **análisis de código**.  
  
2.  En el **análisis de código** ventana, seleccione la supresión de advertencia.  
  
3.  Elija las acciones y luego elija **Suprimir mensajes**y, a continuación, elija **en origen** o **en el archivo de supresión del proyecto**.  
  
     Se suprime la advertencia concreta, y la advertencia aparece en la ventana de análisis de código con un tachado.  
  
> [!NOTE]
>  Las supresiones que no tienen un destino aparecen en el archivo de supresión global.
