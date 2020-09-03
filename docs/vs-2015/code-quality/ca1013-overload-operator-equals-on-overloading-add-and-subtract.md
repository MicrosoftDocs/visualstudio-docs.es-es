---
title: 'CA1013: sobrecargar el operador de igualdad en la sobrecarga de sumar y restar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2304b78073b806dfc4aec9686f061d946b379ded
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545423"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|Identificador de comprobación|CA1013|
|Category|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un tipo público o protegido implementa los operadores de suma o resta sin implementar el operador de igualdad.

## <a name="rule-description"></a>Descripción de la regla
 Cuando las instancias de un tipo se pueden combinar mediante operaciones como suma y resta, casi siempre se debe definir la igualdad que se va a devolver `true` para dos instancias cualesquiera que tengan los mismos valores constituyentes.

 No se puede usar el operador de igualdad predeterminado en una implementación sobrecargada del operador de igualdad. Si lo hace, se producirá un desbordamiento de pila. Para implementar el operador de igualdad, use el método Object. Equals en su implementación de. Consulte el ejemplo siguiente.

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente el operador de igualdad para que sea coherente con los operadores de suma y resta.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la implementación predeterminada del operador de igualdad proporciona el comportamiento correcto para el tipo.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se define un tipo ( `BadAddableType` ) que infringe esta regla. Este tipo debe implementar el operador de igualdad para que dos instancias de que tengan los mismos valores de campo comprueben la `true` igualdad. El tipo `GoodAddableType` muestra la implementación corregida. Tenga en cuenta que este tipo también implementa el operador de desigualdad e invalida <xref:System.Object.Equals%2A> para satisfacer otras reglas. Una implementación completa también implementaría <xref:System.Object.GetHashCode%2A> .

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se comprueba la igualdad mediante el uso de instancias de los tipos que se definieron previamente en este tema para mostrar el comportamiento predeterminado y correcto para el operador de igualdad.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Tipo incorrecto: {2,2} {2,2} ¿son iguales? No hay ningún** 
 **tipo correcto: {3,3} {3,3} ¿son iguales? Sí**, 
 **tipo bueno: {3,3} {3,3} ¿= =?   Sí** 
 **tipo incorrecto: {2,2} {9,9} ¿son iguales? No hay** 
 **buenos tipos: {3,3} {9,9} ¿= =?   No**
## <a name="see-also"></a>Consulte también
 [Operadores de igualdad](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
