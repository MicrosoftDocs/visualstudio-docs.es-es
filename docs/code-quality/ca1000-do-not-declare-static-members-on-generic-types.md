---
title: "CA1000: No declarar miembros estáticos en tipos genéricos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 11bef403ffedee1a22ba615ee1744a7e93f8c1b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: No declarar miembros estáticos en tipos genéricos
|||  
|-|-|  
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|  
|Identificador de comprobación|CA1000|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo genérico visible externamente contiene un `static` (`Shared` en Visual Basic) miembro.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Cuando un `static` se denomina miembro de un tipo genérico, se debe especificar el argumento de tipo para el tipo. Cuando se llama a un miembro de instancia genérico que no admite la interferencia, se debe especificar el argumento de tipo para el miembro. La sintaxis para especificar el argumento de tipo en estos dos casos es diferente y resulta fácil confundirse, como se muestran en las llamadas siguientes:  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```csharp  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 Por lo general, tanto de las declaraciones anteriores deben evitarse para que el argumento de tipo no tienen que especificarse cuando se llama al miembro. Esto da como resultado una sintaxis para llamar a los miembros en genéricos que no es distinta de la sintaxis para tipos no genéricos. Para obtener más información, consulte [CA1004: los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite al miembro estático o cámbielo por un miembro de instancia.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. Al proporcionar genéricos con una sintaxis que sea fácil de entender y usar reduce el tiempo que se necesita para obtener información y aumenta la velocidad de adopción de nuevas bibliotecas.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>Vea también  
 [Genéricos](/dotnet/csharp/programming-guide/generics/index)