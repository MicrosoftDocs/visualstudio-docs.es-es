---
title: 'CA2227: Las propiedades de la colección deben ser de solo lectura'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: f1bbd3e6ba97d969694e7d2142978c12552b3c50
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860256"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Las propiedades de la colección deben ser de solo lectura

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|Identificador de comprobación|CA2227|
|Categoría|Microsoft.Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Una propiedad de escritura visible externamente es de un tipo que implementa <xref:System.Collections.ICollection?displayProperty=fullName>. Esta regla omite las matrices, los indizadores (propiedades con el nombre 'Item') y conjuntos de permisos.

## <a name="rule-description"></a>Descripción de la regla

Una propiedad de colección grabable permite al usuario reemplazar la colección con una colección completamente diferente. Una propiedad de sólo lectura impide que la colección se reemplace, pero permite a los miembros individuales que se puede establecer. Si su objetivo es reemplazar la colección, el patrón de diseño preferido es incluir un método para quitar todos los elementos de la colección y un método para volver a rellenar la colección. Consulte la <xref:System.Collections.ArrayList.Clear%2A> y <xref:System.Collections.ArrayList.AddRange%2A> métodos de la <xref:System.Collections.ArrayList?displayProperty=fullName> clase para obtener un ejemplo de este patrón.

Serialización XML y binaria admiten propiedades de solo lectura que son colecciones. El <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> clase tiene requisitos específicos para los tipos que implementan <xref:System.Collections.ICollection> y <xref:System.Collections.IEnumerable?displayProperty=fullName> con el fin de ser serializable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, asegúrese de la propiedad de solo lectura. Si lo requiere el diseño, agregue métodos para borrar y volver a rellenar la colección.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Puede suprimir la advertencia si la propiedad forma parte de un [el objeto de transferencia de datos (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) clase.

En caso contrario, no suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra un tipo con una propiedad de colección grabable y muestra cómo se puede reemplazar la colección directamente. Además, se muestra la manera preferida de sustitución de una propiedad de colección de solo lectura mediante `Clear` y `AddRange` métodos.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1819: Las propiedades no deberían devolver matrices](../code-quality/ca1819-properties-should-not-return-arrays.md)