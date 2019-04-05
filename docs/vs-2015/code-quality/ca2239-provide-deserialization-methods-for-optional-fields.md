---
title: 'CA2239: Proporcionar métodos de deserialización para campos opcionales | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5bfb682e3b2220a6eb68e7f225e147b8106c3e7c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58986796"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Proporcionar métodos de deserialización para campos opcionales
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|Identificador de comprobación|CA2239|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo tiene un campo que está marcado con el <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> atributo y el tipo no proporciona métodos de control de eventos de deserialización.

## <a name="rule-description"></a>Descripción de la regla
 El <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributo no tiene ningún efecto en la serialización; se serializa un campo marcado con el atributo. Sin embargo, el campo se omite en la deserialización y conserva el valor predeterminado asociado con su tipo. Para establecer el campo durante el proceso de deserialización se deben declarar como controladores de eventos de deserialización.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue métodos para el tipo de control de eventos de deserialización.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el campo se debe omitir durante el proceso de deserialización.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra a un tipo con un campo opcional y el evento de deserialización de los métodos de control.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/cs/FxCop.Usage.OptionalFields.cs#1)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/vb/FxCop.Usage.OptionalFields.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: Proteger los constructores de serialización](../code-quality/ca2120-secure-serialization-constructors.md)
