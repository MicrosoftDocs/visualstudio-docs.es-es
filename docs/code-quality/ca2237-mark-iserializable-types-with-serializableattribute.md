---
title: 'CA2237: Marcar los tipos ISerializable con SerializableAttribute'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7121211d474369f55cff36a7b7d388b7ddfc1a24
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Marcar los tipos ISerializable con SerializableAttribute
|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|Identificador de comprobación|CA2237|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo visible externamente implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz y el tipo no está marcado con el <xref:System.SerializableAttribute?displayProperty=fullName> atributo. La regla omite los tipos derivados cuyo tipo base no es serializable.

## <a name="rule-description"></a>Descripción de la regla
 Para que sea reconocida por common language runtime como serializable, los tipos deben estar marcados con el <xref:System.SerializableAttribute> atributo incluso si el tipo utiliza una rutina de serialización personalizada a través de la implementación de la <xref:System.Runtime.Serialization.ISerializable> interfaz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, aplique la <xref:System.SerializableAttribute> para el tipo de atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla para las clases de excepción porque deben ser serializables para que funcionen correctamente en dominios de aplicación.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe la regla. Quite el <xref:System.SerializableAttribute> atributo línea para cumplir la regla.

 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)