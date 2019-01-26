---
title: Procedimiento Exigir código de mantenimiento con una directiva de protección de análisis de código
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9b868054813f65e15c3dfd422be7240df09e284
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956758"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Procedimiento Exigir código mantenible con una directiva de protección de análisis de código

Los desarrolladores pueden usar la herramienta de métricas de código para medir la complejidad y el mantenimiento de su código, pero no se puede invocar las métricas del código como parte de una directiva de protección. Sin embargo, puede habilitar las reglas de análisis de código que comprueben el cumplimiento de su código con los estándares de las métricas de código y aplicar las reglas mediante las directivas de protección. Para obtener más información acerca de las métricas de código, vea [valores de métricas de código](../code-quality/code-metrics-values.md).

Puede habilitar la profundidad de herencia, acoplamiento de clases, índice de mantenimiento y las reglas de complejidad exigir código mantenible a través de una directiva de protección de análisis de código. Cuatro de estas reglas se encuentra en la categoría "Reglas de mantenimiento" en el editor de directivas de análisis de código.

Los administradores de control de versiones de Team Foundation pueden agregar las reglas de mantenimiento de análisis de código a los requisitos de directiva de protección. Estos en el repositorio directivas requieren que los desarrolladores ejecutar análisis de código en función de estos cambios en las reglas antes de iniciar una inserción en el.

## <a name="to-open-the-code-analysis-policy-editor"></a>Para abrir el editor de directivas de análisis de código

1. En **Team Explorer**, haga clic en el proyecto, haga clic en **configuración del proyecto**y, a continuación, haga clic en **Control de código fuente**.

     El **Control de código fuente** aparece el cuadro de diálogo.

2. En el **directiva de protección** ficha y haga clic en **agregar**.

     El **Agregar directiva de protección** aparece el cuadro de diálogo.

3. En el **directiva de protección** lista, seleccione el **análisis de código** casilla de verificación y, a continuación, haga clic en **Aceptar**.

     El **Editor de directiva de análisis de código** aparece el cuadro de diálogo.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Para habilitar reglas de mantenimiento de análisis de código

1. En el **Editor de directiva de análisis de código** cuadro de diálogo **configuración de la regla**, expanda el **reglas de mantenimiento** nodo.

2. Seleccione las casillas de las reglas siguientes:

   - Profundidad de herencia: **CA1501 AvoidExcessiveInheritance** -umbral: Advertencia en más de 5 niveles de profundidad

   - Complejidad: **CA1502 AvoidExcessiveComplexity** -umbral: Advertencia en más de 25

   - Índice de mantenimiento: **CA1505 AvoidUnmaintainableCode** -umbral: Advertencia a menos de 20

   - Acoplamiento de clases: **CA1506 AvoidExcessiveClassCoupling** -umbral: Advertencia en más de 80 para una clase y más de 30 para un método

     Además, si desea que una infracción de regla para evitar que una compilación correcta, seleccione la **Tratar advertencia como un Error** casilla de verificación situada junto a la descripción de la regla.

3. Haga clic en **Aceptar**. Ahora, la nueva directiva de protección se aplica a las protecciones futuras.

## <a name="see-also"></a>Vea también

- [Valores de las métricas de código](../code-quality/code-metrics-values.md)
- [Crear y usar directivas de protección de análisis de código](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)