---
title: "CA1407: Evite miembros estáticos en tipos visibles para COM | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 43240b8969026a8bbec18528230d3ca97bcb2236
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Evite miembros estáticos en tipos visibles para COM
|||  
|-|-|  
|TypeName|AvoidStaticMembersInComVisibleTypes|  
|Identificador de comprobación|CA1407|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo marcado específicamente como visible para el modelo de objetos componentes (COM) contiene un `public``static` método.  
  
## <a name="rule-description"></a>Descripción de la regla  
 COM no es compatible con `static` métodos.  
  
 Esta regla omite las propiedades y los descriptores de acceso de eventos, métodos o métodos que se marcan utilizando la sobrecarga de operadores el <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributo o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo.  
  
 De forma predeterminada, los siguientes son visibles para COM: ensamblados, tipos públicos, miembros de instancia públicos en tipos públicos y todos los miembros de tipos de valor públicos.  
  
 Para esta regla para que se produzca, un nivel de ensamblado <xref:System.Runtime.InteropServices.ComVisibleAttribute> debe establecerse en `false` y la clase - <xref:System.Runtime.InteropServices.ComVisibleAttribute> debe establecerse en `true`, como se muestra en el código siguiente.  
  
```csharp  
using System;  
using System.Runtime.InteropServices;   
  
[assembly: ComVisible(false)]   
namespace Samples  
{      
    [ComVisible(true)]  
    public class MyClass  
    {  
        public static void DoSomething()  
        {  
        }  
    }  
}  
```  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el diseño para utilizar un método de instancia que proporciona la misma funcionalidad que la `static` método.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si un cliente COM no requiere acceso a la funcionalidad proporcionada por el `static` método.  
  
## <a name="example-violation"></a>Infracción de ejemplo  
  
### <a name="description"></a>Descripción  
 El ejemplo siguiente muestra un `static` método que infringe esta regla.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]  
  
### <a name="comments"></a>Comentarios  
 En este ejemplo, el **Book.FromPages** método no se puede llamar desde COM.  
  
## <a name="example-fix"></a>Corrección del ejemplo  
  
### <a name="description"></a>Descripción  
 Para corregir la infracción en el ejemplo anterior, puede cambiar el método a un método de instancia, pero no tiene sentido en esta instancia. Una solución mejor es aplicar explícitamente `ComVisible(false)` al método para dejar claro a otros desarrolladores que el método no pueden verse desde COM.  
  
 El ejemplo siguiente aplica <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> al método.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
 [CA1406: Evite argumentos Int64 para clientes Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)  
  
 [CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
## <a name="see-also"></a>Vea también  
 [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)