---
title: 'CA2236: Llamar a métodos de clase base en tipos ISerializable | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4ec8c14da5c691f6f9740c6df86cb38aeb9fac5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142389"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Llamar a métodos de clase base en tipos ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|Identificador de comprobación|CA2236|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un tipo se deriva de un tipo que implementa el <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz y una de las siguientes condiciones es true:

- El tipo implementa el constructor de serialización, es decir, un constructor con la <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> firma del parámetro, pero no llama el constructor de serialización del tipo base.

- El tipo implementa la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método pero no llama a la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método del tipo base.

## <a name="rule-description"></a>Descripción de la regla
 En un proceso de serialización personalizada, un tipo implementa la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método para serializar sus campos y el constructor de serialización para deserializar los campos. Si el tipo se deriva de un tipo que implementa el <xref:System.Runtime.Serialization.ISerializable> interfaz, el tipo base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> constructor de serialización y el método debe llamarse a/serializar deserializar los campos del tipo base. En caso contrario, el tipo no se serialice y deserialice correctamente. Tenga en cuenta que si el tipo derivado no agrega ningún campo nuevo, el tipo no es necesario implementar el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método ni el constructor de serialización o llamar a los equivalentes del tipo base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame al tipo base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> constructor de método o la serialización de las correspondientes derivadas tipo método o constructor.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo derivado que cumple la regla llamando al constructor de serialización y <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método de la clase base.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteger los constructores de serialización](../code-quality/ca2120-secure-serialization-constructors.md)
