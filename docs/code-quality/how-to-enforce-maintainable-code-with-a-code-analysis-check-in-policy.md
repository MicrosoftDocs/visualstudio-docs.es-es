---
title: "Cómo: exigir código mantenible con una directiva de protección de análisis de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d9697c7d6a216c08e34eb19287d22a76d67a55
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Cómo: Exigir código mantenible con una directiva de protección de los análisis de código
Los desarrolladores pueden usar la herramienta de métricas de código para medir la complejidad y el mantenimiento del código, pero que no invocan las métricas de código como parte de una directiva de protección. Sin embargo, un equipo puede habilitar reglas de análisis de código que comprueben la compatibilidad del código con los estándares de métrica del código y aplican las reglas a través de directivas de protección. Para obtener más información acerca de las métricas de código, vea la [valores de métrica de código](../code-quality/code-metrics-values.md).  
  
 Los desarrolladores pueden habilitar la profundidad de herencia, acoplamiento de clases, índice de mantenimiento y las reglas de complejidad exigir código mantenible a través de directivas de protección de análisis de código. Los cuatro de estas reglas se encuentran en la categoría "Reglas de mantenimiento" en el editor de directivas de análisis de código.  
  
 Los administradores de versión controlar para [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] puede agregar las reglas de mantenimiento de análisis de código a los requisitos de directiva de protección. Estos en el repositorio directivas requieren los desarrolladores ejecutar el análisis de código en función de estos cambios en las reglas antes de iniciar en el repositorio.  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>Para abrir el Editor de directivas de análisis de código  
  
1.  En **Team Explorer**, haga clic en el proyecto de equipo, haga clic en **configuración del proyecto de equipo**y, a continuación, haga clic en **Control de código fuente**.  
  
     El **Control de código fuente** aparece el cuadro de diálogo.  
  
2.  En el **directiva de protección** ficha y haga clic en **agregar**.  
  
     El **Agregar directiva de protección** aparece el cuadro de diálogo.  
  
3.  En el **directiva de protección** lista, seleccione la **análisis de código** casilla de verificación y, a continuación, haga clic en **Aceptar**.  
  
     El **Editor de directiva de análisis de código** aparece el cuadro de diálogo.  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>Para habilitar reglas de mantenimiento de análisis de código  
  
1.  En el **Editor de directiva de análisis de código** cuadro de diálogo **configuración de reglas de**, expanda la **reglas de mantenimiento** nodo.  
  
2.  Active las casillas de verificación de las reglas siguientes:  
  
    -   Profundidad de herencia: **CA1501 AvoidExcessiveInheritance** -umbral: advertencia en más de 5 niveles de profundidad  
  
    -   Complejidad: **AvoidExcessiveComplexity CA1502** -umbral: advertencia en más de 25  
  
    -   Índice de mantenimiento: **AvoidUnmaintainableCode CA1505** -umbral: advertencia en menos de 20  
  
    -   Acoplamiento de clase: **AvoidExcessiveClassCoupling CA1506** -umbral: advertencia en más de 80 para una clase y más de 30 para un método  
  
    -   Además, si desea que una infracción de regla para evitar que una compilación, seleccione la **Tratar advertencia como un Error** casilla de verificación situada junto a la descripción de la regla.  
  
3.  Haga clic en **Aceptar**. Ahora, la nueva directiva de protección se aplica a las protecciones futuras.  
  
## <a name="see-also"></a>Vea también  
 [Valores de métrica de código](../code-quality/code-metrics-values.md)   
 [Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)