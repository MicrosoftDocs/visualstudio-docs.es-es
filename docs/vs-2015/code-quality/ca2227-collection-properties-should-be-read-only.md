---
title: 'CA2227: las propiedades de la colección deben ser de solo lectura | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8aee6f7172414de809d964652411c1f077fe0cdd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658869"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Las propiedades de la colección deben ser de solo lectura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|Identificador de comprobación|CA2227|
|Categoría|Microsoft. Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Una propiedad grabable externamente visible es un tipo que implementa <xref:System.Collections.ICollection?displayProperty=fullName>. La regla omite las matrices, los indizadores (propiedades con el nombre ' item ') y los conjuntos de permisos.

## <a name="rule-description"></a>Descripción de la regla
 Una propiedad de colección de escritura permite al usuario reemplazar la colección por una colección completamente diferente. Una propiedad de sólo lectura impide que la colección se reemplace, pero sí permite establecer miembros individuales. Si el reemplazo de la colección es un objetivo, el modelo de diseño preferido consiste en incluir un método para quitar todos los elementos de la colección y un método para volver a rellenar la colección. Vea los métodos <xref:System.Collections.ArrayList.Clear%2A> y <xref:System.Collections.ArrayList.AddRange%2A> de la clase <xref:System.Collections.ArrayList?displayProperty=fullName> para obtener un ejemplo de este patrón.

 Tanto la serialización binaria como la de XML admiten propiedades de solo lectura que son colecciones. La clase <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> tiene requisitos específicos para los tipos que implementan <xref:System.Collections.ICollection> y <xref:System.Collections.IEnumerable?displayProperty=fullName> para ser serializables.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, haga que la propiedad sea de solo lectura y, si el diseño lo requiere, agregue métodos para borrar y volver a rellenar la colección.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo con una propiedad de colección de escritura y se muestra cómo se puede reemplazar la colección directamente. Además, se muestra la manera preferida de reemplazar una propiedad de colección de solo lectura mediante métodos `Clear` y `AddRange`.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1819: Las propiedades no deberían devolver matrices](../code-quality/ca1819-properties-should-not-return-arrays.md)
