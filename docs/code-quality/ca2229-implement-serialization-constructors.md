---
title: "CA2229: Implementar constructores de serializaci&#243;n | Microsoft Docs"
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
  - "CA2229"
  - "ImplementSerializationConstructors"
helpviewer_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2229: Implementar constructores de serializaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|Identificador de comprobación|CA2229|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 El tipo implementa la interfaz <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, no es un delegado ni una interfaz, y una de las condiciones siguientes es verdadera:  
  
-   El tipo no tiene un constructor que toma un objeto <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> y un objeto <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> \(la firma del constructor de serialización\).  
  
-   El tipo no está sellado y el modificador de acceso para su constructor de serialización no está protegido \(familia\).  
  
-   El tipo está sellado y el modificador de acceso para su constructor de serialización no es privado.  
  
## Descripción de la regla  
 Esta regla es relevante para los tipos que admiten la serialización personalizada.  Un tipo es compatible con la serialización personalizada si implementa la interfaz <xref:System.Runtime.Serialization.ISerializable>.  Es necesario que el constructor de serialización deserialice o vuelva a crear objetos que se han serializado utilizando el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente el constructor de serialización.  Para una clase sellada, marque el constructor como privado; de lo contrario, márquelo como protegido.  
  
## Cuándo suprimir advertencias  
 No suprima ninguna infracción de la regla.  El tipo no será deserializable y no funcionará en muchos escenarios.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe la regla.  
  
 [!code-cs[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## Reglas relacionadas  
 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## Vea también  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>