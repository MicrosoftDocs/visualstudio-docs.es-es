---
title: 'CA1413: Evitar los campos no públicos en tipos de valor visibles a través de COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3eb216af1b6cd742aff83b248b6752adea292345
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921839"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Evitar los campos no públicos en tipos de valor visibles a través de COM

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|Identificador de comprobación|CA1413|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo de valor que está marcado específicamente como visible en el modelo de objetos componentes (COM) declara un campo de instancia no público.

## <a name="rule-description"></a>Descripción de la regla
Los campos de instancia no públicos de tipos de valor visibles para COM están visibles para los clientes COM. Revise el contenido del campo para obtener información que no debe exponerse o que tendrá un diseño o efecto de seguridad imprevisto.

De forma predeterminada, todos los tipos de valor público son visibles para COM. Sin embargo, para reducir los falsos positivos, esta regla requiere que la visibilidad COM del tipo se indique explícitamente. El ensamblado contenedor debe marcarse con <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> el establecido `false` en y el tipo debe estar marcado con <xref:System.Runtime.InteropServices.ComVisibleAttribute> el establecido `true`en.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla y mantener el campo oculto, cambie el tipo de valor a un tipo de referencia <xref:System.Runtime.InteropServices.ComVisibleAttribute> o quite el atributo del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si es aceptable la exposición pública del campo.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe la regla.

[!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
[!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1407: Evitar miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Marcar ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vea también

- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)
- [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation)