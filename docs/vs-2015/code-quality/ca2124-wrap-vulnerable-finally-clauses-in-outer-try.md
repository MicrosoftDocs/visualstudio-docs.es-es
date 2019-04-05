---
title: 'CA2124: Incluir finally vulnerables externa cláusulas try | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1eb503e9f5a9251cb9a348d29c7cd9636389a080
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997228"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Incluir cláusulas finally vulnerables en un bloque try externo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|Identificador de comprobación|CA2124|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 En las versiones 1.0 y 1.1 de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], un método público o protegido contiene un `try` / `catch` / `finally` bloque. El `finally` bloque aparece para restablecer el estado de seguridad y no se incluye en un `finally` bloque.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla busca `try` / `finally` bloques de código que tenga como destino las versiones 1.0 y 1.1 de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que podrían ser vulnerables a los filtros de excepción malintencionados presentes en la pila de llamadas. Si se producen operaciones confidenciales como la suplantación en el bloque try, y se produce una excepción, el filtro puede ejecutarse antes de la `finally` bloque. El ejemplo de suplantación, esto significa que el filtro se ejecutaría como el usuario suplantado. Los filtros son actualmente sólo pueden implementarse en Visual Basic.

> [!WARNING]
>  **Tenga en cuenta** en las versiones 2.0 y versiones posteriores de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], protege automáticamente el tiempo de ejecución un `try` / `catch` /  `finally` block de los filtros de excepción malintencionados, si se produce el restablecimiento directamente dentro del método que contiene el bloque de excepción.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Coloque el desencapsulado `try` / `finally` en un bloque try externo. Vea el segundo ejemplo siguiente. Esto obliga la `finally` se ejecute antes de código de filtro.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo

### <a name="description"></a>Descripción
 El pseudocódigo siguiente muestra el patrón que detecta esta regla.

### <a name="code"></a>Código

```
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

## <a name="example"></a>Ejemplo
 El pseudocódigo siguiente muestra el patrón que puede usar para proteger el código y cumplir esta regla.

```
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
