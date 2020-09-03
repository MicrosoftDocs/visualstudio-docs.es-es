---
title: 'CA2105: los campos de matriz no deben ser de solo lectura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: db52bf869642a5bdcc28eeb0792b295ae314a508
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538676"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Los campos de matrices no deben ser de solo lectura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|Identificador de comprobación|CA2105|
|Category|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un campo público o protegido que contiene una matriz se declara como de solo lectura.

## <a name="rule-description"></a>Descripción de la regla
 Al aplicar el `readonly` `ReadOnly` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] modificador (en) a un campo que contiene una matriz, el campo no se puede cambiar para hacer referencia a una matriz diferente. Sin embargo, se pueden cambiar los elementos de la matriz almacenados en un campo de solo lectura. El código que toma decisiones o realiza operaciones que se basan en los elementos de una matriz de solo lectura a la que se puede tener acceso públicamente podría contener una vulnerabilidad de seguridad explotable.

 Tenga en cuenta que tener un campo público también infringe la regla de diseño [CA1051: no declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para solucionar la vulnerabilidad de seguridad que se identifica mediante esta regla, no confíe en el contenido de una matriz de solo lectura a la que se pueda tener acceso públicamente. Se recomienda encarecidamente que use uno de los procedimientos siguientes:

- Reemplace la matriz por una colección fuertemente tipada que no se pueda cambiar. Para obtener más información, vea <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Reemplace el campo público por un método que devuelva un clon de una matriz privada. Dado que el código no se basa en el clon, no hay ningún riesgo si se modifican los elementos.

  Si elige el segundo enfoque, no Reemplace el campo por una propiedad. las propiedades que devuelven matrices afectan negativamente al rendimiento. Para obtener más información, vea [CA1819: las propiedades no deben devolver matrices](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No se recomienda la exclusión de una advertencia de esta regla. Casi no hay escenarios en los que el contenido de un campo de solo lectura no sea importante. Si este es el caso del escenario, quite el `readonly` modificador en lugar de excluir el mensaje.

## <a name="example"></a>Ejemplo
 Este ejemplo muestra los peligros de infringir esta regla. La primera parte muestra una biblioteca de ejemplo que tiene un tipo, `MyClassWithReadOnlyArrayField` , que contiene dos campos ( `grades` y `privateGrades` ) que no son seguros. El campo `grades` es público y, por tanto, es vulnerable a cualquier llamador. El campo `privateGrades` es privado pero sigue siendo vulnerable porque lo devuelve el método a los llamadores `GetPrivateGrades` . El `securePrivateGrades` campo se expone de forma segura mediante el `GetSecurePrivateGrades` método. Se declara como privado para seguir los procedimientos de diseño correctos. La segunda parte muestra el código que cambia los valores almacenados en los `grades` `privateGrades` miembros y.

 La biblioteca de clases de ejemplo aparece en el ejemplo siguiente.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Ejemplo
 En el código siguiente se usa la biblioteca de clases de ejemplo para ilustrar los problemas de seguridad de la matriz de solo lectura.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 La salida de este ejemplo es:

 **Antes de la alteración: calificaciones: 90, 90, 90 calificaciones privadas: 90, 90, 90 notas seguras, 90, 90, 90** 
 **Después de la manipulación: calificaciones: 90, 555, 90 calificaciones privadas: 90, 555, 90 notas seguras, 90, 90, 90**
## <a name="see-also"></a>Consulte también
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
