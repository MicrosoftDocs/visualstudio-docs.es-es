---
title: Procedimiento Exigir código mantenible con una directiva de protección de análisis de código | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 27593a450f7c2a1b34c1c84bc1d4e7ea5bb5919f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142252"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procedimiento Exigir código de mantenimiento con una directiva de protección de análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los desarrolladores pueden usar la herramienta de métricas de código para medir la complejidad y el mantenimiento de su código, pero las métricas del código no pueden invocar como parte de una directiva de protección. Sin embargo, un equipo puede habilitar las reglas de análisis de código que comprueban el cumplimiento de su código con los estándares de las métricas del código y aplican las reglas mediante las directivas de protección. Para obtener más información acerca de las métricas de código, vea el [valores de las métricas de código](../code-quality/code-metrics-values.md).  
  
 Los programadores pueden habilitar la profundidad de herencia, acoplamiento de clases, índice de mantenimiento y las reglas de complejidad exigir código mantenible a través de directivas de protección de análisis de código. Cuatro de estas reglas se encuentra en la categoría "Reglas de mantenimiento" en el editor de directivas de análisis de código.  
  
 Los administradores de la versión de control para [!INCLUDE[esprfound](../includes/esprfound-md.md)] puede agregar las reglas de mantenimiento de análisis de código a los requisitos de directiva de protección. Estos en el repositorio directivas requieren que los desarrolladores ejecutar análisis de código en función de estos cambios en las reglas antes de iniciar una inserción en el.  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>Para abrir el Editor de directivas de análisis de código  
  
1. En **Team Explorer**, haga clic en el proyecto de equipo, haga clic en **configuración del proyecto de equipo**y, a continuación, haga clic en **Control de código fuente**.  
  
     El **Control de código fuente** aparece el cuadro de diálogo.  
  
2. En el **directiva de protección** ficha y haga clic en **agregar**.  
  
     El **Agregar directiva de protección** aparece el cuadro de diálogo.  
  
3. En el **directiva de protección** lista, seleccione el **análisis de código** casilla de verificación y, a continuación, haga clic en **Aceptar**.  
  
     El **Editor de directiva de análisis de código** aparece el cuadro de diálogo.  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>Para habilitar reglas de mantenimiento de análisis de código  
  
1. En el **Editor de directiva de análisis de código** cuadro de diálogo **configuración de la regla**, expanda el **reglas de mantenimiento** nodo.  
  
2. Seleccione las casillas de las reglas siguientes:  
  
    - Profundidad de herencia: **CA1501 AvoidExcessiveInheritance** -umbral: Advertencia en más de 5 niveles de profundidad  
  
    - Complejidad: **CA1502 AvoidExcessiveComplexity** -umbral: Advertencia en más de 25  
  
    - Índice de mantenimiento: **CA1505 AvoidUnmaintainableCode** -umbral: Advertencia a menos de 20  
  
    - Acoplamiento de clases: **CA1506 AvoidExcessiveClassCoupling** -umbral: Advertencia en más de 80 para una clase y más de 30 para un método  
  
    - Además, si desea que una infracción de regla para evitar que una compilación, seleccione el **Tratar advertencia como un Error** casilla de verificación situada junto a la descripción de la regla.  
  
3. Haga clic en **OK**. Ahora, la nueva directiva de protección se aplica a las protecciones futuras.  
  
## <a name="see-also"></a>Vea también  
 [Valores de las métricas de código](../code-quality/code-metrics-values.md)   
 [Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
