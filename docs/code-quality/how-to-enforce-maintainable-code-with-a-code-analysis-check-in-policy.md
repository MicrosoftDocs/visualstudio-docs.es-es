---
title: 'Cómo: Exigir código mantenible con una directiva de protección de los análisis de código'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6269b4839c552fa6a1e982226bbb311cb7d5e9d9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921132"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Cómo: exigir código mantenible con una directiva de protección de análisis de código

Los desarrolladores pueden usar la herramienta de métricas de código para medir la complejidad y el mantenimiento del código, pero no se puede invocar las métricas de código como parte de una directiva de protección. Sin embargo, puede habilitar las reglas de análisis de código que comprueben la compatibilidad del código con los estándares de métricas de código y aplicar las reglas a través de directivas de protección. Para obtener más información acerca de las métricas de código, vea [valores de métrica de código](../code-quality/code-metrics-values.md).

Puede habilitar la profundidad de herencia, acoplamiento de clases, índice de mantenimiento y las reglas de complejidad exigir código mantenible a través de una directiva de protección de análisis de código. Los cuatro de estas reglas se encuentran en la categoría "Reglas de mantenimiento" en el editor de directivas de análisis de código.

Los administradores de control de versiones de Team Foundation pueden agregar las reglas de mantenimiento de análisis de código a los requisitos de directiva de protección. Estos en el repositorio directivas requieren los desarrolladores ejecutar el análisis de código en función de estos cambios en las reglas antes de iniciar en el repositorio.

## <a name="to-open-the-code-analysis-policy-editor"></a>Para abrir el editor de directivas de análisis de código

1. En **Team Explorer**, haga clic en el proyecto de equipo, haga clic en **configuración del proyecto de equipo**y, a continuación, haga clic en **Control de código fuente**.

     El **Control de código fuente** aparece el cuadro de diálogo.

2. En el **directiva de protección** ficha y haga clic en **agregar**.

     El **Agregar directiva de protección** aparece el cuadro de diálogo.

3. En el **directiva de protección** lista, seleccione la **análisis de código** casilla de verificación y, a continuación, haga clic en **Aceptar**.

     El **Editor de directiva de análisis de código** aparece el cuadro de diálogo.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Para habilitar reglas de mantenimiento de análisis de código

1. En el **Editor de directiva de análisis de código** cuadro de diálogo **configuración de reglas de**, expanda la **reglas de mantenimiento** nodo.

2. Active las casillas de verificación de las reglas siguientes:

    -   Profundidad de herencia: **CA1501 AvoidExcessiveInheritance** -umbral: advertencia en más de 5 niveles de profundidad

    -   Complejidad: **AvoidExcessiveComplexity CA1502** -umbral: advertencia en más de 25

    -   Índice de mantenimiento: **AvoidUnmaintainableCode CA1505** -umbral: advertencia en menos de 20

    -   Acoplamiento de clase: **AvoidExcessiveClassCoupling CA1506** -umbral: advertencia en más de 80 para una clase y más de 30 para un método

    Además, si desea que una infracción de regla para evitar que una compilación correcta, seleccione la **Tratar advertencia como un Error** casilla de verificación situada junto a la descripción de la regla.

3. Haga clic en **Aceptar**. Ahora, la nueva directiva de protección se aplica a las protecciones futuras.

## <a name="see-also"></a>Vea también

- [Valores de métrica de código](../code-quality/code-metrics-values.md)
- [Crear y usar directivas de protección de análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)