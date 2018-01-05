---
title: 'CA1013: Suma y resta de sobrecarga el operador de igualdad sobrecarga | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
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
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d668760159af34e8f22a69bed41de185fa4254e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga
|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|Identificador de comprobación|CA1013|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo público o protegido implementa los operadores de suma o resta sin implementar el operador de igualdad.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Cuando las instancias de un tipo se pueden combinar mediante operaciones como la suma y resta, casi siempre debe definir la igualdad para devolver `true` para que las dos instancias que tienen los mismos valores que la componen.  
  
 No puede utilizar el operador de igualdad predeterminado en una implementación sobrecargada del operador de igualdad. Si lo hace, provocará un desbordamiento de pila. Para implementar el operador de igualdad, utilice el método Object.Equals en la implementación. Vea el ejemplo siguiente.  
  
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
 Es seguro suprimir una advertencia de esta regla cuando la implementación predeterminada del operador de igualdad proporciona el comportamiento adecuado para el tipo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se define un tipo (`BadAddableType`) que infringe esta regla. Este tipo debe implementar el operador de igualdad para hacer que las dos instancias que tienen los mismos valores de campo probar `true` igualdad. El tipo `GoodAddableType` muestra la implementación correcta. Tenga en cuenta que este tipo también implementa el operador de desigualdad y reemplaza <xref:System.Object.Equals%2A> para cumplir con otras reglas. Una implementación completa también implementaría <xref:System.Object.GetHashCode%2A>.  
  
 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se comprueba la igualdad utilizando instancias de los tipos que se han definido anteriormente en este tema para mostrar el valor predeterminado y un comportamiento correcto para el operador de igualdad.  
  
 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
 **¿Tipo no válido: {2,2} {2,2} son iguales? No**  
**¿Tipo: {3,3} {3,3} son iguales? Sí**  
**¿Tipo: {3,3} {3,3} son ==?   Sí**  
**¿Tipo no válido: {2,2} {9,9} son iguales? No**  
**¿Tipo: {3,3} {9,9} son ==?   No**   
## <a name="see-also"></a>Vea también  
 [Operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators)