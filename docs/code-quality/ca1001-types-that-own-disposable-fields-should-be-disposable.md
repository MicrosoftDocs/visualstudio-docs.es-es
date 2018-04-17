---
title: 'CA1001: Los tipos que poseen campos descartables deben ser descartables | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1306f594af4639d1b2af24d07e4654f8825cd3d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Los tipos que poseen campos descartables deben ser descartables
|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|Identificador de comprobación|CA1001|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático: si el tipo no es visible fuera del ensamblado.<br /><br /> Problemático: si el tipo es visible fuera del ensamblado.|  
  
## <a name="cause"></a>Motivo  
 Una clase declara e implementa un campo de instancia que es un <xref:System.IDisposable?displayProperty=fullName> tipo y la clase no implementa <xref:System.IDisposable>.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Una clase que implementa el <xref:System.IDisposable> interfaz para desechar recursos no administrados que posee. Un campo de instancia que es un <xref:System.IDisposable> tipo indica que el campo posee un recurso no administrado. Una clase que declara un <xref:System.IDisposable> campo indirectamente posee un recurso no administrado y debería implementar la <xref:System.IDisposable> interfaz. Si la clase no posee directamente los recursos no administrados, no debe implementar un finalizador.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente <xref:System.IDisposable> desde y hacia el <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> llamada al método el <xref:System.IDisposable.Dispose%2A> método Dispose del campo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra una clase que infringe la regla y una clase que cumpla la regla implementando <xref:System.IDisposable>. La clase no implementa un finalizador porque la clase no posee directamente los recursos no administrados.  
  
 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA2213: Aplique Dispose a los campos a los que se pueda](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: Los métodos Dispose deben llamar al método Dispose de la clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: Los tipos que poseen recursos nativos deben ser descartables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)