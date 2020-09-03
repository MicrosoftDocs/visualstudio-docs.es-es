---
title: 'CA2124: encapsular cláusulas Finally vulnerables en try externo | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4e191ca10456f133e1213961ca2d1ed9cb8e040b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544305"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Incluir cláusulas finally vulnerables en un bloque try externo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|Identificador de comprobación|CA2124|
|Category|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 En las versiones 1,0 y 1,1 de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , un método público o protegido contiene un `try` / `catch` / `finally` bloque. El `finally` bloque parece restablecer el estado de seguridad y no se incluye en un `finally` bloque.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla ubica `try` / `finally` los bloques en código que tienen como destino las versiones 1,0 y 1,1 del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que podrían ser vulnerables a los filtros de excepciones malintencionados presentes en la pila de llamadas. Si se producen operaciones confidenciales como la suplantación en el bloque try y se produce una excepción, el filtro se puede ejecutar antes que el `finally` bloque. En el ejemplo de suplantación, esto significa que el filtro se ejecutaría como el usuario suplantado. Los filtros solo se pueden implementar en Visual Basic.

> [!WARNING]
> En las versiones 2,0 y posteriores de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , el tiempo de ejecución protege automáticamente un `try` / `catch` /  `finally` bloque de los filtros de excepciones malintencionados, si el restablecimiento se produce directamente dentro del método que contiene el bloque de excepción.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Coloque el desencapsulado `try` / `finally` en un bloque try externo. Vea el segundo ejemplo siguiente. Esto obliga `finally` a que se ejecute antes de filtrar el código.

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
 En el siguiente pseudocódigo se muestra el patrón que puede usar para proteger el código y satisfacer esta regla.

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
