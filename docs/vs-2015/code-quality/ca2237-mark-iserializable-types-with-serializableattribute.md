---
title: 'CA2237: Marcar los tipos ISerializable con SerializableAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 10a8fa5300241326f2af5df847974644bd4fe0d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201492"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Marcar los tipos ISerializable con SerializableAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|Identificador de comprobación|CA2237|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Implementa un tipo visible externamente el <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz y el tipo no está marcado con el <xref:System.SerializableAttribute?displayProperty=fullName> atributo. La regla omite los tipos derivados cuyo tipo base no es serializable.

## <a name="rule-description"></a>Descripción de la regla
 Para que reconozca el common language runtime como serializable, los tipos deben estar marcados con el <xref:System.SerializableAttribute> atributo incluso si el tipo utiliza una rutina de serialización personalizada a través de la implementación de la <xref:System.Runtime.Serialization.ISerializable> interfaz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, aplique el <xref:System.SerializableAttribute> al tipo de atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla para las clases de excepción porque deben ser serializables para que funcionen correctamente en dominios de aplicación.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla. Quite el <xref:System.SerializableAttribute> atributo línea para cumplir la regla.

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)



