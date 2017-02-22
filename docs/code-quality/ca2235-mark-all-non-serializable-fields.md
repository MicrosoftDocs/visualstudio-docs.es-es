---
title: "CA2235: Marcar todos los campos no serializables | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
helpviewer_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2235: Marcar todos los campos no serializables
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAllNonSerializableFields|  
|Identificador de comprobación|CA2235|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un campo de instancia de un tipo que no es serializable se declara en un tipo que es serializable.  
  
## Descripción de la regla  
 Un tipo serializable es aquel marcado con el atributo <xref:System.SerializableAttribute?displayProperty=fullName>.  Cuando se serializa el tipo, se produce una excepción <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> si un tipo contiene un campo de instancia de un tipo que no es serializable.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, aplique el atributo <xref:System.NonSerializedAttribute?displayProperty=fullName> al campo que no es serializable.  
  
## Cuándo suprimir advertencias  
 Sólo suprima ninguna advertencia de esta regla si se declara un tipo <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> que permite deserializar instancias del campo.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo que infringe la regla y otro que la cumple.  
  
 [!code-cs[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## Reglas relacionadas  
 [LCA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implementar los métodos de serialización de forma correcta](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)