---
title: "CA2120: Proteger los constructores de serializaciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2120"
  - "SecureSerializationConstructors"
helpviewer_keywords: 
  - "CA2120"
  - "SecureSerializationConstructors"
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2120: Proteger los constructores de serializaciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecureSerializationConstructors|  
|Identificador de comprobación|CA2120|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El tipo implementa la interfaz <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, no es un delegado o ni una interfaz, y se declara en un ensamblado que permite llamadores que no son de plena confianza.  El tipo tiene un constructor que toma un objeto <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> y un objeto <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> \(la firma del constructor de serialización\).  Una comprobación de seguridad no protege este constructor, pero protege uno o más constructores regulares del tipo.  
  
## Descripción de la regla  
 Esta regla es relevante para los tipos que admiten la serialización personalizada.  Un tipo es compatible con la serialización personalizada si implementa la interfaz <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>.  Se requiere el constructor de serialización y se utiliza para deserializar o volver a crear objetos que se han serializado utilizando el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>.  Dado que el constructor de serialización asigna e inicializa objetos, las comprobaciones de seguridad presentes en constructores regulares también deben estar presentes en el constructor de serialización.  Si infringe esta regla, los llamadores que no pudieron crear una instancia podrían utilizar el constructor de serialización para ello.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, proteja el constructor de serialización con solicitudes de seguridad idénticas a las que protegen otros constructores.  
  
## Cuándo suprimir advertencias  
 No suprima ninguna infracción de la regla.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe la regla.  
  
 [!code-cs[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]  
  
## Reglas relacionadas  
 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## Vea también  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>