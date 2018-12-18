---
title: advertencias de mantenimiento
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 340d57df4223cab134ef5cf46180dd1a8c552c08
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887155"
---
# <a name="maintainability-warnings"></a>advertencias de mantenimiento

Advertencias de mantenimiento admiten mantenimiento de la biblioteca y aplicación.

## <a name="in-this-section"></a>En esta sección

| Regla | Descripción |
|-----------|-----------------------------------|
| [CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo, lo que conduce a errores. |
| [CA1501: Evite una herencia excesiva](../code-quality/ca1501-avoid-excessive-inheritance.md) | Un tipo tiene más de cuatro niveles de profundidad en su jerarquía de herencia. Las jerarquías de tipos con demasiados niveles de anidación pueden resultar difíciles de seguir, comprender y mantener. |
| [CA1502: Evite la excesiva complejidad](../code-quality/ca1502-avoid-excessive-complexity.md) | Esta regla mide el número de rutas de acceso independientes de forma lineal a través del método, que es determinado por el número y la complejidad de ramas condicionales. |
| [CA1504: Revise los nombres de campos erróneos](../code-quality/ca1504-review-misleading-field-names.md) | El nombre de un campo de instancia empieza por "s_" o el nombre de un estático (compartido en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) campo empieza por "m_". |
| [CA1505: Evite código que no se puede mantener](../code-quality/ca1505-avoid-unmaintainable-code.md) | Un tipo o método tiene un valor del índice de mantenimiento bajo. Un índice de mantenimiento bajo indica que un tipo o método resulta probablemente difícil de mantener y se debería volver a diseñar. |
| [CA1506: Evite el acoplamiento excesivo de clases](../code-quality/ca1506-avoid-excessive-class-coupling.md) | Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método. |

## <a name="see-also"></a>Vea también

- [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)