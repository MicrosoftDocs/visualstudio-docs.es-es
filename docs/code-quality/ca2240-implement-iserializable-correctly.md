---
title: 'CA2240: Implementar ISerializable correctamente | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c8e3f9ba0e3cb182ec08dd802dc87728a0fb9dc0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Implementar ISerializable correctamente
|||  
|-|-|  
|TypeName|ImplementISerializableCorrectly|  
|Identificador de comprobación|CA2240|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Un tipo visible externamente es asignable a la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz y una de las siguientes condiciones es true:  
  
-   El tipo hereda pero no reemplaza el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método y el tipo declara campos de instancia que no están marcados con el <xref:System.NonSerializedAttribute?displayProperty=fullName> atributo.  
  
-   El tipo no está sellado y el tipo implementa una <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método que no es visible externamente ni reemplazable.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Campos que se declaran en un tipo que hereda de la instancia la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz no se incluyen automáticamente en el proceso de serialización. Para incluir los campos, el tipo debe implementar la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método y el constructor de serialización. Si los campos no se deben serializar, aplique el <xref:System.NonSerializedAttribute> atributo a los campos para indicar explícitamente la decisión.  
  
 En tipos que no son sealed, las implementaciones de la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método debe ser visible externamente. Por lo tanto, el método puede llamarse mediante tipos derivados y es reemplazable.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, realice la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método visible y reemplazable y asegúrese de que todos los campos de instancia se incluyen en el proceso de serialización o se marca explícitamente con el <xref:System.NonSerializedAttribute> atributo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra dos tipos serializables que infringen la regla.  
  
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se corrige las infracciones anteriores dos proporcionando una implementación puede invalidar de <xref:System.Runtime.Serialization.ISerializable.GetObjectData> en la clase Book y proporcionando una implementación de `GetObjectData` en la clase de biblioteca.  
  
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)  
 [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)  
