---
title: "CA2124: Incluir finally vulnerables cláusulas en externa try | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 567c519b09042dbd0bba447d4631544dd78ca1ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Incluir cláusulas Finally vulnerables en un bloque Try externo
|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|Identificador de comprobación|CA2124|  
|Categoría|Microsoft.Security|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 En las versiones 1.0 y 1.1 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], un método público o protegido contiene un `try` / `catch` / `finally` bloque. El `finally` bloque aparece para restablecer el estado de seguridad y no se incluye en un `finally` bloque.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla busca `try` / `finally` bloques de código que tenga como destino las versiones 1.0 y 1.1 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que pueden ser vulnerables a los filtros de excepción malintencionados presentes en la pila de llamadas. Si las operaciones reservadas como la suplantación aparecen en el bloque try, y se produce una excepción, el filtro puede ejecutarse antes de la `finally` bloque. En el ejemplo de suplantación, esto significa que el filtro se ejecutaría como el usuario suplantado. Los filtros son actualmente sólo pueden implementarse en Visual Basic.  
  
> [!WARNING]
>  **Tenga en cuenta** en las versiones 2.0 y posteriores de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], protege automáticamente el tiempo de ejecución un `try` / `catch` /  `finally` impide los filtros de excepción malintencionados, si se produce el restablecimiento directamente dentro del método que contiene el bloque de excepción.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Coloque el desempaquetarse `try` / `finally` en un bloque try externo. Vea el segundo ejemplo siguiente. Esto fuerza la `finally` a ejecutarse antes que el código de filtro.  
  
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