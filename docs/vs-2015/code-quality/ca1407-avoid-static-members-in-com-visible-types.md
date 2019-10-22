---
title: 'CA1407: Evite miembros estáticos en tipos visibles para COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6996d210417a56dd83532c481aaa0dc80b9f23ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655236"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Evite miembros estáticos en tipos visibles para COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|Identificador de comprobación|CA1407|
|Categoría|Microsoft. Interoperability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo que está marcado específicamente como visible para el modelo de objetos componentes (COM) contiene un método `public``static`.

## <a name="rule-description"></a>Descripción de la regla
 COM no admite métodos de `static`.

 Esta regla omite los descriptores de acceso de propiedades y eventos, métodos de sobrecarga de operadores o métodos marcados mediante el atributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o el atributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

 De forma predeterminada, los siguientes elementos son visibles para COM: ensamblados, tipos públicos, miembros de instancia pública en tipos públicos y todos los miembros de tipos de valor públicos.

 Para que se produzca esta regla, un <xref:System.Runtime.InteropServices.ComVisibleAttribute> de nivel de ensamblado debe establecerse en `false` y la clase <xref:System.Runtime.InteropServices.ComVisibleAttribute> debe estar establecida en `true`, como se muestra en el código siguiente.

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
 Para corregir una infracción de esta regla, cambie el diseño para utilizar un método de instancia que proporcione la misma funcionalidad que el método `static`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si un cliente COM no requiere acceso a la funcionalidad proporcionada por el método `static`.

## <a name="example-violation"></a>Ejemplo de infracción

### <a name="description"></a>Descripción
 En el ejemplo siguiente se muestra un método `static` que infringe esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Comentarios
 En este ejemplo, no se puede llamar al método **book. FromPages** desde com.

## <a name="example-fix"></a>Corrección de ejemplo

### <a name="description"></a>Descripción
 Para corregir la infracción en el ejemplo anterior, podría cambiar el método a un método de instancia, pero esto no tiene sentido en esta instancia. Una solución mejor es aplicar explícitamente `ComVisible(false)` al método para que resulte claro a otros desarrolladores que el método no se puede mostrar desde COM.

 En el ejemplo siguiente se aplica <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> al método.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Evite argumentos Int64 para clientes Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Vea también
 [Interoperating with Unmanaged Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) (Interoperar con código no administrado)
