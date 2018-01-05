---
title: "CA2111: Los punteros no deberían estar visibles | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 31ae25892b6b5a153a0a4d1e52047eb5be2368d1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Los punteros no deberían estar visibles
|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|Identificador de comprobación|CA2111|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un público o protegido <xref:System.IntPtr?displayProperty=fullName> o <xref:System.UIntPtr?displayProperty=fullName> campo no es de solo lectura.  
  
## <a name="rule-description"></a>Descripción de la regla  
 <xref:System.IntPtr>y <xref:System.UIntPtr> son tipos de puntero que se usan para tener acceso a memoria no administrada. Si un puntero no es privado, interno ni de solo lectura, el código malintencionado puede cambiar el valor del puntero, potencialmente permitir el acceso a ubicaciones arbitrarias en memoria o provocando errores del sistema o aplicación.  
  
 Si desea proteger el acceso al tipo que contiene el campo de puntero, vea [CA2112: los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Proteja el puntero mediante la realización de solo lectura, interno o privado.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprimir una advertencia de esta regla si no se debe confiar en el valor del puntero.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra punteros que infringen y cumplen la regla. Observe que los punteros no privados también infringen la regla [CA1051: no declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>Vea también  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>