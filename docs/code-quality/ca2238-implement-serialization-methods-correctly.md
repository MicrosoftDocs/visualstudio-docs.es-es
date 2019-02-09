---
title: 'CA2238: Implementar métodos de serialización correctamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 79448909dcffd9c55ecf78154295ac77a7538bdf
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930264"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Implementar métodos de serialización correctamente

|||
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|Identificador de comprobación|CA2238|
|Categoría|Microsoft.Usage|
|Cambio problemático|Importante: si el método es visible fuera del ensamblado.<br /><br /> No problemático: si el método no es visible fuera del ensamblado.|

## <a name="cause"></a>Motivo
 Un método que controla un evento de serialización no especifica la firma correcta, el tipo de valor devuelto ni la visibilidad.

## <a name="rule-description"></a>Descripción de la regla
 Un método se designa un controlador de eventos de serialización aplicando uno de los atributos de eventos de serialización siguientes:

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  Controladores de eventos de serialización toman un único parámetro de tipo <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, return `void`y tienen `private` visibilidad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, corrija la firma, el tipo de valor devuelto o la visibilidad del controlador de eventos de serialización.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra los controladores de eventos de serialización correctamente declarados.

 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteger los constructores de serialización](../code-quality/ca2120-secure-serialization-constructors.md)