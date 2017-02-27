---
title: "LCA2236: Llamar a m&#233;todos de clase base en tipos ISerializable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
helpviewer_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# LCA2236: Llamar a m&#233;todos de clase base en tipos ISerializable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallBaseClassMethodsOnISerializableTypes|  
|Identificador de comprobación|CA2236|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo se deriva de un tipo que implementa la interfaz <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> y se cumple una de las condiciones siguientes:  
  
-   El tipo implementa la serialización del constructor, es decir, un constructor con <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, la firma del parámetro <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, pero no llama al constructor de la serialización del tipo base.  
  
-   El tipo implementa el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> pero no llama al método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> del tipo base.  
  
## Descripción de la regla  
 En un proceso de serialización personalizado, un tipo implementa el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> para serializar sus campos y el constructor de la serialización para deserializar los campos.  Si el tipo deriva de un tipo que implementa la interfaz <xref:System.Runtime.Serialization.ISerializable>, debería llamarse al método del tipo base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> y al constructor de la serialización para serializar\/deserializar los campos del tipo base.  De lo contrario, el tipo no se serializará ni se deserializará correctamente.  Tenga en cuenta que si el tipo derivado no agrega ningún campo nuevo, el tipo no necesita implementar el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> ni el constructor de la serialización ni llamar a los equivalentes del tipo base.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, llame al método del tipo base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> o al constructor de serialización desde el constructor o el método del tipo derivado correspondiente.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo derivado que cumple la regla llamando al constructor de serialización y el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> de la clase base.  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-cs[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## Reglas relacionadas  
 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implementar los métodos de serialización de forma correcta](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)