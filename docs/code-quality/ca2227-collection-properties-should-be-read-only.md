---
title: "CA2227: Propiedades de la colección deben ser de solo lectura | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a1835c5e600320ec8b36102e4749d92cf21eae1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Las propiedades de la colección deben ser de solo lectura
|||  
|-|-|  
|TypeName|CollectionPropertiesShouldBeReadOnly|  
|Identificador de comprobación|CA2227|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Una propiedad de escritura visible externamente es un tipo que implementa <xref:System.Collections.ICollection?displayProperty=fullName>. La regla omite las matrices, los indizadores (propiedades con el nombre 'Item') y conjuntos de permisos.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Una propiedad de colección grabable permite al usuario reemplazar la colección por otra completamente diferente. Una propiedad de sólo lectura impide que la colección se reemplace, pero sí permite establecer miembros individuales. Si su objetivo es reemplazar la colección, el patrón de diseño preferido consiste en incluir un método para quitar todos los elementos de la colección y un método para volver a rellenar la colección. Consulte la <xref:System.Collections.ArrayList.Clear%2A> y <xref:System.Collections.ArrayList.AddRange%2A> métodos de la <xref:System.Collections.ArrayList?displayProperty=fullName> clase para obtener un ejemplo de este patrón.  
  
 Serialización XML y binaria admiten propiedades de solo lectura que son colecciones. El <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> clase tiene requisitos específicos para los tipos que implementan <xref:System.Collections.ICollection> y <xref:System.Collections.IEnumerable?displayProperty=fullName> para que sean serializables.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, convierta la propiedad de solo lectura y, si lo requiere el diseño, agregue métodos para borrar y volver a rellenar la colección.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo con una propiedad de colección grabable y muestra cómo se puede reemplazar la colección directamente. Además, la forma preferida de sustitución de una propiedad de colección de solo lectura mediante `Clear` y `AddRange` se muestran los métodos.  
  
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1819: Las propiedades no deberían devolver matrices](../code-quality/ca1819-properties-should-not-return-arrays.md)