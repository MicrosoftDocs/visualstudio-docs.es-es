---
title: Advertencias de mantenimiento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e448a72e2ff92b3e3028829d4b1e7658c304ee3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667891"
---
# <a name="maintainability-warnings"></a>advertencias de mantenimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las advertencias de mantenimiento admiten el mantenimiento de bibliotecas y aplicaciones.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1500: Los nombres de las variables no deben coincidir con los nombres de los campos](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Un método de instancia declara un parámetro o una variable local cuyo nombre coincide con un campo de instancia del tipo declarativo, lo que conduce a errores.|
|[CA1501: Evitar una herencia excesiva](../code-quality/ca1501-avoid-excessive-inheritance.md)|Un tipo tiene más de cuatro niveles de profundidad en su jerarquía de herencia. Las jerarquías de tipos con demasiados niveles de anidación pueden resultar difíciles de seguir, comprender y mantener.|
|[CA1502: Evitar una complejidad excesiva](../code-quality/ca1502-avoid-excessive-complexity.md)|Esta regla mide el número de rutas de acceso independientes de forma lineal a través del método, que es determinado por el número y la complejidad de bifurcaciones condicionales.|
|[CA1504: Revisar los nombres de campos erróneos](../code-quality/ca1504-review-misleading-field-names.md)|El nombre de un campo de instancia comienza por "s_", o el nombre de un campo estático (compartido en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) comienza por "m_".|
|[CA1505: Evitar código que no se puede mantener](../code-quality/ca1505-avoid-unmaintainable-code.md)|Un tipo o método tiene un valor del índice de mantenimiento bajo. Un índice de mantenimiento bajo indica que un tipo o método resulta probablemente difícil de mantener y se debería volver a diseñar.|
|[CA1506: Evitar el acoplamiento excesivo de clases](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Esta regla mide el acoplamiento de clase contando el número de referencias de tipo únicas que contiene un tipo o método.|

## <a name="see-also"></a>Consulte también
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
