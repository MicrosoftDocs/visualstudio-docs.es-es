---
title: Usar una directiva de protección de análisis de código
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2de2322b42be2591fa0f6cdcfc49572322dcd140
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587490"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Cómo: exigir código mantenible con una directiva de protección de análisis de código

Los desarrolladores pueden usar la herramienta de métricas de código para medir la complejidad y el mantenimiento del código, pero no puede invocar las métricas de código como parte de una directiva de protección. Sin embargo, puede habilitar las reglas de análisis de código que comprueban el cumplimiento del código con estándares de métricas de código y aplicar las reglas a través de las directivas de protección. Para obtener más información sobre las métricas de código, consulte [valores de métricas de código](../code-quality/code-metrics-values.md).

Puede habilitar la profundidad de la herencia, el acoplamiento de clases, el índice de mantenimiento y las reglas de complejidad para aplicar código mantenible a través de una directiva de protección de análisis de código. Las cuatro reglas se encuentran en la categoría "reglas de mantenimiento" en el editor de directivas de análisis de código.

Los administradores de control de versiones de Team Foundation pueden agregar las reglas de mantenimiento del análisis de código a los requisitos de la Directiva de protección. Estas directivas de inserción en el repositorio requieren que los desarrolladores ejecuten el análisis de código en función de estos cambios de reglas antes de iniciar una inserción en el repositorio.

## <a name="to-open-the-code-analysis-policy-editor"></a>Para abrir el editor de directivas de análisis de código

1. En **Team Explorer**, haga clic con el botón secundario en el proyecto, haga clic en **configuración del proyecto**y, a continuación, haga clic en **control de código fuente**.

     Aparecerá el cuadro de diálogo **control de código fuente** .

2. En la pestaña **Directiva de inserción en el repositorio** , haga clic en **Agregar**.

     Aparece el cuadro de diálogo **Agregar Directiva de inserción en el repositorio** .

3. En la lista **Directiva de protección** , active la casilla **análisis de código** y, a continuación, haga clic en **Aceptar**.

     Aparecerá el cuadro de diálogo **Editor de directivas de análisis de código** .

## <a name="to-enable-code-analysis-maintainability-rules"></a>Para habilitar las reglas de mantenimiento del análisis de código

1. En el cuadro de diálogo **Editor de directivas de análisis de código** , en configuración de **reglas**, expanda el nodo **reglas de mantenimiento** .

2. Active las casillas de las siguientes reglas:

   - Profundidad de herencia: **CA1501 AvoidExcessiveInheritance** -Threshold: ADVERTENCIA a más de 5 niveles de profundidad

   - Complejidad: **CA1502 AvoidExcessiveComplexity** -Threshold: ADVERTENCIA en más de 25

   - Índice de mantenimiento: **CA1505 AvoidUnmaintainableCode** -Threshold: ADVERTENCIA en menos de 20

   - Acoplamiento de clases: **CA1506 AvoidExcessiveClassCoupling** -Threshold: ADVERTENCIA en más de 80 para una clase y más de 30 para un método

     Además, si desea una infracción de regla para evitar una compilación correcta, active la casilla **tratar ADVERTENCIA como error** junto a la descripción de la regla.

3. Haga clic en **Aceptar**. La nueva Directiva de inserción en el repositorio se aplica ahora a las protecciones futuras.

## <a name="see-also"></a>Vea también

- [Valores de las métricas de código](../code-quality/code-metrics-values.md)
- [Crear y usar directivas de protección de análisis de código](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
