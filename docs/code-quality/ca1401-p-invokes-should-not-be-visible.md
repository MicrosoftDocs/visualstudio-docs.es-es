---
title: "CA1401: Invoca P no debería estar visible | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 707c78c6101c3cec554efe0f6957e4f08c059c3a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: Los elementos P/Invoke no deben estar visibles
|||  
|-|-|  
|TypeName|PInvokesShouldNotBeVisible|  
|Identificador de comprobación|CA1401|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un método público o protegido en un tipo público tiene el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo (también se implementa por la `Declare` palabra clave en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los métodos que se marcan con la <xref:System.Runtime.InteropServices.DllImportAttribute> atributo (o métodos que se definen mediante la `Declare` palabra clave en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) usar servicios de invocación de plataforma para tener acceso a código no administrado. No se deberían exponer estos métodos. Al mantener estos métodos privados o internos, se asegura de que no se puede usar la biblioteca de infringir la seguridad al permitir que los llamadores acceso a las API no administradas que no puede llamar en caso contrario.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nivel de acceso del método.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se declara un método que infringe esta regla.  
  
 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]