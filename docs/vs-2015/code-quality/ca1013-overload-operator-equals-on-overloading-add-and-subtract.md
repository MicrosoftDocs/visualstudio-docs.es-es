---
title: 'CA1013: El operador de sobrecarga es igual al sobrecargar suma y resta | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5b735af635e59174a683763fa1633b0e33e0d10a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591193"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1013: sobrecarga del operador es igual al sobrecargar la suma y resta](https://docs.microsoft.com/visualstudio/code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract).

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|Identificador de comprobación|CA1013|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido implementa los operadores de suma o resta sin implementar el operador de igualdad.

## <a name="rule-description"></a>Descripción de la regla
 Cuando las instancias de un tipo pueden combinarse con operaciones como la suma y resta, casi siempre debe definir la igualdad para devolver `true` para que las dos instancias que tienen los mismos valores que lo constituyen.

 No se puede usar el operador de igualdad predeterminado en una implementación del operador de igualdad sobrecargada. Si lo hace, provocará un desbordamiento de pila. Para implementar el operador de igualdad, utilice el método Object.Equals en su implementación. Vea el ejemplo siguiente.

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
 Para corregir una infracción de esta regla, implemente el operador de igualdad para que sea matemáticamente coherente con los operadores de suma y resta.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la implementación predeterminada del operador de igualdad proporciona el comportamiento correcto para el tipo.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se define un tipo (`BadAddableType`) que infringe esta regla. Este tipo debe implementar el operador de igualdad para hacer las dos instancias que tienen los mismos valores de campo test `true` igualdad. El tipo `GoodAddableType` muestra la implementación. Tenga en cuenta que este tipo también implementa el operador de desigualdad y reemplaza <xref:System.Object.Equals%2A> para cumplir con otras reglas. También podría implementar una implementación completa <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente se comprueba la igualdad mediante el uso de instancias de los tipos definidos anteriormente en este tema para mostrar el valor predeterminado y comportamiento correcto para el operador de igualdad.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **¿Tipo no válida: {2,2} {2,2} son iguales? ¿No**
**tipo buena: {3,3} {3,3} son iguales? ¿Sí**
**tipo buena: {3,3} {3,3} son ==?   ¿Sí**
**tipo no válida: {2,2} {9,9} son iguales? ¿No**
**tipo buena: {3,3} {9,9} son ==?   No**
## <a name="see-also"></a>Vea también
 [Operadores de igualdad](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



