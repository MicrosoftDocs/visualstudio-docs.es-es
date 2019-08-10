---
title: 'CA2124: Incluir cláusulas finally vulnerables en un bloque try externo'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c75c7c240f694b18caacefc0f9b1ee07f54faf36
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920800"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Incluir cláusulas finally vulnerables en un bloque try externo

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|Identificador de comprobación|CA2124|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
En las versiones 1,0 y 1,1 del .NET Framework, un método público o protegido contiene un `try` / / `catch` `finally` bloque. El `finally` bloque parece restablecer el estado de seguridad y no se incluye en `finally` un bloque.

## <a name="rule-description"></a>Descripción de la regla
Esta regla ubica `try` / los bloques en código que tienen como destino las versiones 1,0 y 1,1 del .NET Framework que podrían ser vulnerables a los filtros de excepciones malintencionados presentes en la pila de llamadas. `finally` Si se producen operaciones confidenciales como la suplantación en el bloque try y se produce una excepción, el filtro se puede ejecutar `finally` antes que el bloque. En el ejemplo de suplantación, esto significa que el filtro se ejecutaría como el usuario suplantado. Los filtros solo se pueden implementar en Visual Basic.

> [!NOTE]
> En las versiones 2,0 y posteriores del .NET Framework, el motor en tiempo de `try` ejecución protege automáticamente un /  / `catch` `finally` bloque de filtros de excepciones malintencionados, si el restablecimiento se produce directamente dentro del método. contiene el bloque de excepción.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Coloque el desencapsulado `try` / `finally` en un bloque try externo. Vea el segundo ejemplo siguiente. Esto obliga a `finally` que se ejecute antes de filtrar el código.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo

### <a name="description"></a>DESCRIPCIÓN

El pseudocódigo siguiente muestra el patrón que detecta esta regla.

```csharp
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

En el siguiente pseudocódigo se muestra el patrón que puede usar para proteger el código y satisfacer esta regla.

```csharp
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```