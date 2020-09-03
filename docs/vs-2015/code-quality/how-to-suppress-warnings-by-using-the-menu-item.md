---
title: 'Cómo: suprimir advertencias mediante el elemento de menú | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96b7433ff4f696989142aa2c2ce47982006b93b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72610013"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Cómo: Suprimir advertencias mediante el elemento de menú
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> En la supresión de código fuente no se admite para los proyectos de sitio Web.

 Puede utilizar la ventana Análisis de código para suprimir las advertencias de análisis de código. Suprimir una advertencia no es lo mismo que deshabilitarla. Cuando se suprime una advertencia, solo se aplica a una instancia determinada de la infracción. También se mostrarán otras infracciones de la misma advertencia en la ventana Lista de errores.

 Después de ejecutar el análisis de código, puede determinar que una o varias de las advertencias de análisis de código que se muestran en la ventana Análisis de código no se aplican a la aplicación. Por ejemplo, puede determinar que el código es correcto tal y como está. O bien, podría ser el caso de que algunas infracciones tengan prioridad baja y no se corrijan en el ciclo de desarrollo actual. Independientemente de la razón, a menudo resulta útil indicar que la advertencia no es aplicable para permitir que los miembros del equipo sepan que el código se ha revisado y que se ha determinado que la advertencia se puede suprimir. La supresión del código fuente es útil porque permite poner una supresión cerca de donde se genera la advertencia.

 Puede elegir si la supresión aparecerá en el código fuente o en el archivo de supresión global. Algunas supresiones deben colocarse en el archivo de supresión global. En este caso, se deshabilitará la opción **en origen** .

### <a name="to-suppress-a-warning-by-using-menu-item"></a>Para suprimir una advertencia mediante el elemento de menú

1. En el menú **analizar** , elija **ventanas** y, a continuación, elija **análisis de código**.

2. En la ventana **análisis de código** , seleccione la advertencia suprimir.

3. Elija acciones, seleccione **suprimir mensajes**y, a continuación, elija **en origen** o **en archivo de supresión de proyecto**.

     Se suprime la advertencia específica y la advertencia aparece en la ventana Análisis de código con un tachado.

> [!NOTE]
> Las supresiones que no tienen un destino aparecen en el archivo de supresión global.
