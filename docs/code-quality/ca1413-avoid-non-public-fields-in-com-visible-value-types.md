---
title: 'CA1413: Evite campos no públicos en tipos de valor visibles para COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 060d8ebd26b08ef02a9986846bdab2a25a85072f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547911"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Evite campos no públicos en tipos de valor visibles para COM

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|Identificador de comprobación|CA1413|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo de valor marcado específicamente como visible para el modelo de objetos componentes (COM) declara un campo de instancia no públicos.

## <a name="rule-description"></a>Descripción de la regla
 Los campos de instancia no públicos de tipos de valor visibles para COM están visibles para los clientes COM. Revise el contenido del campo para obtener información que no deba exponerse o que tendrá un efecto no deseado de diseño y la seguridad.

 De forma predeterminada, todos los tipos de valor públicos son visibles para COM. Sin embargo, para reducir los falsos positivos, esta regla requiere la visibilidad de COM de tipo explícita. El ensamblado contenedor debe estar marcado con el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> establecido en `false` y el tipo se debe marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `true`.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla y mantener el campo oculto, cambie el tipo de valor a un tipo de referencia o quite el <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si es aceptable pública exposición del campo.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vea también

- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)
- [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation)