---
title: 'CA2240: implementar ISerializable correctamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0abc95811dc870abbfaa583fbaa7705302a70781
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670168"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Implementar ISerializable correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|Identificador de comprobación|CA2240|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo visible externamente se puede asignar a la interfaz <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> y se cumple una de las siguientes condiciones:

- El tipo hereda pero no invalida el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> y el tipo declara los campos de instancia que no están marcados con el atributo <xref:System.NonSerializedAttribute?displayProperty=fullName>.

- El tipo no está sellado y el tipo implementa un método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> que no es visible y reemplazable externamente.

## <a name="rule-description"></a>Descripción de la regla
 Los campos de instancia que se declaran en un tipo que hereda la interfaz <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> no se incluyen automáticamente en el proceso de serialización. Para incluir los campos, el tipo debe implementar el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> y el constructor de serialización. Si no se deben serializar los campos, aplique el atributo <xref:System.NonSerializedAttribute> a los campos para indicar explícitamente la decisión.

 En los tipos que no están sellados, las implementaciones del método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> deben ser visibles externamente. Por lo tanto, los tipos derivados pueden llamar al método y se puede reemplazar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, haga que el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> sea visible y Overridable, y asegúrese de que todos los campos de instancia se incluyen en el proceso de serialización o que están marcados explícitamente con el atributo <xref:System.NonSerializedAttribute>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran dos tipos serializables que infringen la regla.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrigen las dos infracciones anteriores proporcionando una implementación invalidable de [ISerializable. GetObjectData] (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) en la clase Book y proporcionando una implementación de <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> en la clase Library.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)
