---
title: 'CA2227: Propiedades de la colección deben ser de solo lectura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3182a254ed5e22c560523911f87dc852708a9eb1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997007"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Las propiedades de la colección deben ser de solo lectura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|Identificador de comprobación|CA2227|
|Categoría|Microsoft.Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Una propiedad de escritura visible externamente es un tipo que implementa <xref:System.Collections.ICollection?displayProperty=fullName>. La regla omite las matrices, los indizadores (propiedades con el nombre 'Item') y conjuntos de permisos.

## <a name="rule-description"></a>Descripción de la regla
 Una propiedad de colección grabable permite al usuario reemplazar la colección con una colección completamente diferente. Una propiedad de sólo lectura impide que la colección se reemplace, pero sí permite establecer miembros individuales. Si su objetivo es reemplazar la colección, el patrón de diseño preferido es incluir un método para quitar todos los elementos de la colección y un método para volver a rellenar la colección. Consulte la <xref:System.Collections.ArrayList.Clear%2A> y <xref:System.Collections.ArrayList.AddRange%2A> métodos de la <xref:System.Collections.ArrayList?displayProperty=fullName> clase para obtener un ejemplo de este patrón.

 Serialización XML y binaria admiten propiedades de solo lectura que son colecciones. El <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> clase tiene requisitos específicos para los tipos que implementan <xref:System.Collections.ICollection> y <xref:System.Collections.IEnumerable?displayProperty=fullName> con el fin de ser serializable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, que la propiedad de sólo lectura y, si lo requiere el diseño, agregue métodos para borrar y volver a rellenar la colección.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo con una propiedad de colección grabable y muestra cómo se puede reemplazar la colección directamente. Además, la manera preferida de sustitución de una propiedad de colección de solo lectura mediante `Clear` y `AddRange` se muestran los métodos.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1819: Las propiedades no deberían devolver matrices](../code-quality/ca1819-properties-should-not-return-arrays.md)
