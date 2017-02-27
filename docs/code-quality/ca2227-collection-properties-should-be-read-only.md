---
title: "CA2227: Las propiedades de la colecci&#243;n deben ser de solo lectura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
helpviewer_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA2227: Las propiedades de la colecci&#243;n deben ser de solo lectura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionPropertiesShouldBeReadOnly|  
|Identificador de comprobación|CA2227|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Una propiedad de escritura visible externamente es un tipo que implementa <xref:System.Collections.ICollection?displayProperty=fullName>.  La regla omite las matrices, los indizadores \(propiedades con el nombre 'Item'\) y los conjuntos de permisos.  
  
## Descripción de la regla  
 Una propiedad de colección de escritura permite al usuario reemplazar la colección por otra completamente diferente.  Una propiedad de sólo lectura impide que la colección se reemplace, pero sí permite establecer miembros individuales.  Si el objetivo es reemplazar la colección, el modelo de diseño más indicado es incluir un método para quitar todos los elementos de la colección y otro método para volver a rellenarla.  Vea los métodos <xref:System.Collections.ArrayList.Clear%2A> y <xref:System.Collections.ArrayList.AddRange%2A> de la clase <xref:System.Collections.ArrayList?displayProperty=fullName> para obtener un ejemplo de este modelo.  
  
 La serialización binaria y XML admiten propiedades de sólo lectura que son colecciones.  La clase <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> tiene requisitos concretos para los tipos que implementan <xref:System.Collections.ICollection> y <xref:System.Collections.IEnumerable?displayProperty=fullName>, a fin de ser serializable.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, haga que la propiedad sea de sólo lectura y, si el diseño lo exige, agregue métodos para borrar su contenido y rellenarla de nuevo.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo con una propiedad de colección de escritura y muestra cómo se puede reemplazar la colección directamente.  Además, se muestra la manera más adecuada de reemplazar una propiedad de colección de sólo lectura, utilizando los métodos `Clear` y `AddRange`.  
  
 [!code-cs[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## Reglas relacionadas  
 [CA1819: Las propiedades no deberían devolver matrices](../code-quality/ca1819-properties-should-not-return-arrays.md)