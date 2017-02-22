---
title: "CA2240: Implementar ISerializable correctamente | Microsoft Docs"
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
  - "CA2240"
  - "ImplementISerializableCorrectly"
helpviewer_keywords: 
  - "CA2240"
  - "ImplementISerializableCorrectly"
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2240: Implementar ISerializable correctamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementISerializableCorrectly|  
|Identificador de comprobación|CA2240|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo visible externamente se puede asignar a la interfaz <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> y si una de las condiciones siguientes es verdadera:  
  
-   El tipo hereda pero no reemplaza el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> y el tipo declara campos de instancia que no se marcan con el atributo <xref:System.NonSerializedAttribute?displayProperty=fullName>.  
  
-   El tipo no es sealed e implementa un método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> que no es visible externamente ni reemplazable.  
  
## Descripción de la regla  
 Los campos de instancia que se declaran en un tipo que hereda la interfaz <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> no se incluyen automáticamente en el proceso de serialización.  Para incluir los campos, el tipo debe implementar el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> y el constructor de serialización.  Si los campos no se deben serializar, aplique el atributo <xref:System.NonSerializedAttribute> a los campos para indicar explícitamente la decisión.  
  
 En tipos que no se sellan \(sealed\), las implementaciones del método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> deberían ser visibles externamente.  Por tanto, se puede llamar al método mediante tipos derivados y se puede invalidar.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, haga que el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> sea visible y reemplazable, y asegúrese de que todos los campos de instancia se incluyan en el proceso de serialización marcado explícitamente con el atributo <xref:System.NonSerializedAttribute>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En el ejemplo siguiente se muestran dos tipos serializables que infringen la regla.  
  
 [!code-cs[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]  
  
## Ejemplo  
 En el ejemplo siguiente se corrigen las dos infracciones anteriores proporcionando una implementación de [ISerializable.GetObjectData](assetId:///ISerializable.GetObjectData?qualifyHint=False&autoUpgrade=False) de la clase Book que se puede invalidar y una implementación de assetId:///ISerializable.GetObjectData?qualifyHint=False&autoUpgrade=False de la clase Library.  
  
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]  
  
## Reglas relacionadas  
 [LCA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implementar los métodos de serialización de forma correcta](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)