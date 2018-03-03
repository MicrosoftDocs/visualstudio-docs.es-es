---
title: "Cómo: exigir código mantenible con una directiva de protección de análisis de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 80f3d2385fa1023637081b787c8d938ae42f79b4
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Cómo: exigir código mantenible con una directiva de protección de análisis de código

Los desarrolladores pueden usar la herramienta de métricas de código para medir la complejidad y el mantenimiento del código, pero no se puede invocar las métricas de código como parte de una directiva de protección. Sin embargo, puede habilitar las reglas de análisis de código que comprueben la compatibilidad del código con los estándares de métricas de código y aplicar las reglas a través de directivas de protección. Para obtener más información acerca de las métricas de código, vea [valores de métrica de código](../code-quality/code-metrics-values.md).

Puede habilitar la profundidad de herencia, acoplamiento de clases, índice de mantenimiento y las reglas de complejidad exigir código mantenible a través de una directiva de protección de análisis de código. Los cuatro de estas reglas se encuentran en la categoría "Reglas de mantenimiento" en el editor de directivas de análisis de código.

Los administradores de control de versiones de Team Foundation pueden agregar las reglas de mantenimiento de análisis de código a los requisitos de directiva de protección. Estos en el repositorio directivas requieren los desarrolladores ejecutar el análisis de código en función de estos cambios en las reglas antes de iniciar en el repositorio.

## <a name="to-open-the-code-analysis-policy-editor"></a>Para abrir el editor de directivas de análisis de código

1. en **Team Explorer**, haga clic en el proyecto de equipo, haga clic en **configuración del proyecto de equipo**y, a continuación, haga clic en **Control de código fuente**.

     The **Source Control** dialog box appears.

2. en el **directiva de protección** ficha y haga clic en **agregar**.

     The **Add Check-in Policy** dialog box appears.

3. en el **directiva de protección** lista, seleccione la **análisis de código** casilla de verificación y, a continuación, haga clic en **Aceptar**.

     The **Code Analysis Policy Editor** dialog box appears.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Para habilitar reglas de mantenimiento de análisis de código

1. en el **Editor de directiva de análisis de código** cuadro de diálogo **configuración de reglas de**, expanda la **reglas de mantenimiento** nodo.

2. Seleccione las casillas de las reglas siguientes:

    -   Profundidad de herencia: **CA1501 AvoidExcessiveInheritance** -umbral: advertencia en más de 5 niveles de profundidad

    -   Complejidad: **AvoidExcessiveComplexity CA1502** -umbral: advertencia en más de 25

    -   Índice de mantenimiento: **AvoidUnmaintainableCode CA1505** -umbral: advertencia en menos de 20

    -   Acoplamiento de clase: **AvoidExcessiveClassCoupling CA1506** -umbral: advertencia en más de 80 para una clase y más de 30 para un método

    Además, si desea que una infracción de regla para evitar que una compilación correcta, seleccione la **Tratar advertencia como un Error** casilla de verificación situada junto a la descripción de la regla.

3. Haga clic en **Aceptar**. Ahora, la nueva directiva de protección se aplica a las protecciones futuras.

## <a name="see-also"></a>Vea también

[Los valores de las métricas de código](../code-quality/code-metrics-values.md)
[crear y usar directivas de protección de análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)