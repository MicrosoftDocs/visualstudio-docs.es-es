---
title: 'Cómo: exigir código mantenible con una directiva de protección de análisis de código | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0d54ca9a31e8a1bbd2496bf8689a119e53580c79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660220"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Cómo: Exigir código mantenible con una directiva de protección de los análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los desarrolladores pueden usar la herramienta de métricas de código para medir la complejidad y el mantenimiento del código, pero no pueden invocar las métricas de código como parte de una directiva de protección. Sin embargo, un equipo puede habilitar reglas de análisis de código que comprueban el cumplimiento de su código con estándares de métricas de código y aplican las reglas mediante directivas de protección. Para obtener más información sobre las métricas de código, consulte los valores de las [métricas de código](../code-quality/code-metrics-values.md).

 Los desarrolladores pueden habilitar la profundidad de la herencia, el acoplamiento de clases, el índice de mantenimiento y las reglas de complejidad para aplicar código mantenible a través de las directivas de protección de análisis de código. Las cuatro reglas se encuentran en la categoría "reglas de mantenimiento" en el editor de directivas de análisis de código.

 Los administradores de control de versiones de [!INCLUDE[esprfound](../includes/esprfound-md.md)] pueden agregar las reglas de mantenimiento del análisis de código a los requisitos de la Directiva de protección. Estas directivas de inserción en el repositorio requieren que los desarrolladores ejecuten el análisis de código en función de estos cambios de reglas antes de iniciar una inserción en el repositorio.

### <a name="to-open-the-code-analysis-policy-editor"></a>Para abrir el editor de directivas de análisis de código

1. En **Team Explorer**, haga clic con el botón secundario en el proyecto de equipo, haga clic en **configuración del proyecto de equipo**y, a continuación, en control de **código fuente**.

     Aparecerá el cuadro de diálogo **control de código fuente** .

2. En la pestaña **Directiva de inserción en el repositorio** , haga clic en **Agregar**.

     Aparece el cuadro de diálogo **Agregar Directiva de inserción en el repositorio** .

3. En la lista **Directiva de protección** , active la casilla **análisis de código** y, a continuación, haga clic en **Aceptar**.

     Aparecerá el cuadro de diálogo **Editor de directivas de análisis de código** .

### <a name="to-enable-code-analysis-maintainability-rules"></a>Para habilitar las reglas de mantenimiento del análisis de código

1. En el cuadro de diálogo **Editor de directivas de análisis de código** , en configuración de **reglas**, expanda el nodo **reglas de mantenimiento** .

2. Active las casillas de las siguientes reglas:

    - Profundidad de herencia: **CA1501 AvoidExcessiveInheritance** -Threshold: ADVERTENCIA a más de 5 niveles de profundidad

    - Complejidad: **CA1502 AvoidExcessiveComplexity** -Threshold: ADVERTENCIA en más de 25

    - Índice de mantenimiento: **CA1505 AvoidUnmaintainableCode** -Threshold: ADVERTENCIA en menos de 20

    - Acoplamiento de clases: **CA1506 AvoidExcessiveClassCoupling** -Threshold: ADVERTENCIA en más de 80 para una clase y más de 30 para un método

    - Además, si desea una infracción de regla para evitar una compilación, active la casilla **tratar ADVERTENCIA como error** junto a la descripción de la regla.

3. Haga clic en **Aceptar**. La nueva Directiva de inserción en el repositorio se aplica ahora a las protecciones futuras.

## <a name="see-also"></a>Consulte también
 [Valores de métricas de código](../code-quality/code-metrics-values.md) [crear y usar directivas de protección de análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
