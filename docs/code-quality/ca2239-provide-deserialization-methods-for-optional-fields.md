---
title: "CA2239: Proporcionar m&#233;todos de deserializaci&#243;n para campos opcionales | Microsoft Docs"
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
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
helpviewer_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2239: Proporcionar m&#233;todos de deserializaci&#243;n para campos opcionales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideDeserializationMethodsForOptionalFields|  
|Identificador de comprobación|CA2239|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo tiene un campo que se marca con el atributo <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> y el tipo no proporciona los métodos de control de eventos de deserialización.  
  
## Descripción de la regla  
 El atributo <xref:System.Runtime.Serialization.OptionalFieldAttribute> no tiene ningún efecto en la serialización; se serializan los campos marcados con el atributo.  Sin embargo, el campo se omite en la deserialización y mantiene el valor predeterminado asociado a su tipo.  Los controladores de eventos de deserialización se deben declarar para establecer el campo durante el proceso de deserialización.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue al tipo los métodos de control de eventos de deserialización.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el campo se debe omitir durante el proceso de deserialización.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo con un campo opcional y los métodos de control de eventos de deserialización.  
  
 [!code-cs[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]  
  
## Reglas relacionadas  
 [LCA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implementar los métodos de serialización de forma correcta](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)