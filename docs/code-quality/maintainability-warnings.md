---
title: advertencias de mantenimiento
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcb1165ea00d407f5b4840358cc270eb299ba198
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586220"
---
# <a name="maintainability-warnings"></a>Advertencias de mantenimiento

Las advertencias de mantenimiento admiten el mantenimiento de bibliotecas y aplicaciones.

## <a name="in-this-section"></a>En esta sección

| Regla | Descripción |
|-----------|-----------------------------------|
| [CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos](../code-quality/ca1500.md) | Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo, lo que conduce a errores. |
| [CA1501: Evitar una herencia excesiva](../code-quality/ca1501.md) | Un tipo tiene más de cuatro niveles de profundidad en su jerarquía de herencia. Las jerarquías de tipos con demasiados niveles de anidación pueden resultar difíciles de seguir, comprender y mantener. |
| [CA1502: Evitar una complejidad excesiva](../code-quality/ca1502.md) | Esta regla mide el número de rutas de acceso independientes de forma lineal a través del método, que es determinado por el número y la complejidad de bifurcaciones condicionales. |
| [CA1504: Revisar los nombres de campos erróneos](../code-quality/ca1504.md) | El nombre de un campo de instancia comienza por "s_", o el nombre de un campo estático ( [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]compartido en) comienza por "m_". |
| [CA1505: Evitar código que no se puede mantener](../code-quality/ca1505.md) | Un tipo o método tiene un valor del índice de mantenimiento bajo. Un índice de mantenimiento bajo indica que un tipo o método resulta probablemente difícil de mantener y se debería volver a diseñar. |
| [CA1506: Evitar el acoplamiento excesivo de clases](../code-quality/ca1506.md) | Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método. |
| [CA1507: Usar nameof en lugar de la cadena](../code-quality/ca1507.md) | Un literal de cadena se usa como argumento en el `nameof` que se podría utilizar una expresión. |
| [CA1508: Evitar código de condición no alcanzado](../code-quality/ca1508.md) | Un método tiene código condicional que siempre se evalúa como `true` o `false` en tiempo de ejecución. Esto conduce a código muerto en la `false` rama de la condición. |
| [CA1509: entrada no válida en el archivo de configuración de métricas de código](../code-quality/ca1509.md) | Las reglas de métricas de código, como [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) y [CA1506](ca1506.md), proporcionan un archivo `CodeMetricsConfig.txt` de configuración denominado que tiene una entrada no válida. |

## <a name="see-also"></a>Consulte también

- [Medir la complejidad y el mantenimiento del código administrado](../code-quality/code-metrics-values.md)
