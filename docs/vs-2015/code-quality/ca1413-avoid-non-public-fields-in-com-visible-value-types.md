---
title: 'CA1413: Evite campos no públicos en tipos de valor visibles para COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1054330b26cf145ebcbc943a56dc699fe793999f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548465"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Evitar los campos no públicos en tipos de valor visibles a través de COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|Identificador de comprobación|CA1413|
|Category|Microsoft. Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo de valor que está marcado específicamente como visible en el modelo de objetos componentes (COM) declara un campo de instancia no público.

## <a name="rule-description"></a>Descripción de la regla
 Los campos de instancia no públicos de tipos de valor visibles para COM están visibles para los clientes COM. Revise el contenido del campo para obtener información que no debe exponerse o que tendrá un diseño o efecto de seguridad imprevisto.

 De forma predeterminada, todos los tipos de valor público son visibles para COM. Sin embargo, para reducir los falsos positivos, esta regla requiere que la visibilidad COM del tipo se indique explícitamente. El ensamblado contenedor debe marcarse con el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> establecido en `false` y el tipo debe estar marcado con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `true` .

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla y mantener el campo oculto, cambie el tipo de valor a un tipo de referencia o quite el <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si es aceptable la exposición pública del campo.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe la regla.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1407: Evitar los miembros estáticos en tipos visibles a través de COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Marcar los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Consulte también
 [Interoperar con código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) que [cumple los tipos de .net para la interoperación](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
