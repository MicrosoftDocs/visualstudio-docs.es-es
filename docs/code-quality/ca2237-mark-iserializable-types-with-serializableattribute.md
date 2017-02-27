---
title: "CA2237: Marcar los tipos ISerializable con SerializableAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
helpviewer_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2237: Marcar los tipos ISerializable con SerializableAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkISerializableTypesWithSerializable|  
|Identificador de comprobación|CA2237|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo visible externamente implementa la interfaz <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> y el tipo no se marca con el atributo <xref:System.SerializableAttribute?displayProperty=fullName>.  La regla omite los tipos derivados cuyo tipo base no es serializable.  
  
## Descripción de la regla  
 Para que los tipos sean reconocidos como serializables por el Common Language Runtime deben estar marcados con el atributo <xref:System.SerializableAttribute> incluso si el tipo utiliza una rutina de serialización personalizada a través de la implementación de la interfaz <xref:System.Runtime.Serialization.ISerializable>.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, aplique el atributo <xref:System.SerializableAttribute> al tipo.  
  
## Cuándo suprimir advertencias  
 No suprima ninguna advertencia de esta regla para las clases de excepción porque deben ser serializables para que funcionen correctamente en los dominios de aplicación.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe la regla.  Quite los comentarios de línea del atributo <xref:System.SerializableAttribute> para cumplir la regla.  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-cs[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## Reglas relacionadas  
 [LCA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implementar los métodos de serialización de forma correcta](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)