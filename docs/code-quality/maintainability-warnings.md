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
ms.openlocfilehash: 5dad282bfc1c539216b55e41d77d7743808311d6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587373"
---
# <a name="maintainability-warnings"></a>Advertencias de mantenimiento

Las advertencias de mantenimiento admiten el mantenimiento de bibliotecas y aplicaciones.

## <a name="in-this-section"></a>En esta sección

| Regla | Descripción |
|-----------|-----------------------------------|
| [CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos](../code-quality/ca1500.md) | Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo, lo que conduce a errores. |
| [CA1501: Evite una herencia excesiva](../code-quality/ca1501.md) | Un tipo tiene más de cuatro niveles de profundidad en su jerarquía de herencia. Las jerarquías de tipos con demasiados niveles de anidación pueden resultar difíciles de seguir, comprender y mantener. |
| [CA1502: Evite la excesiva complejidad](../code-quality/ca1502.md) | Esta regla mide el número de rutas de acceso independientes de forma lineal a través del método, que es determinado por el número y la complejidad de bifurcaciones condicionales. |
| [CA1504: Revise los nombres de campos erróneos](../code-quality/ca1504.md) | El nombre de un campo de instancia comienza por "s_", o el nombre de un campo estático (compartido en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) comienza por "m_". |
| [CA1505: Evite código que no se puede mantener](../code-quality/ca1505.md) | Un tipo o método tiene un valor del índice de mantenimiento bajo. Un índice de mantenimiento bajo indica que un tipo o método resulta probablemente difícil de mantener y se debería volver a diseñar. |
| [CA1506: Evite el acoplamiento excesivo de clases](../code-quality/ca1506.md) | Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método. |
| [CA1507: usar nombre en lugar de cadena](../code-quality/ca1507.md) | Un literal de cadena se usa como argumento en el que se podría usar una expresión de `nameof`. |

## <a name="see-also"></a>Vea también

- [Medir la complejidad y el mantenimiento del código administrado](../code-quality/code-metrics-values.md)
