---
title: 'CA2105: Los campos de matrices no deberían ser de solo lectura'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91a97983a8760d7f5df04fe6e5b0a56a782a11ce
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915211"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Los campos de matrices no deberían ser de solo lectura
|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|Identificador de comprobación|CA2105|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Se declara un campo público o protegido que contiene una matriz de solo lectura.

## <a name="rule-description"></a>Descripción de la regla
 Al aplicar el `readonly` (`ReadOnly` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) no se puede cambiar el modificador a un campo que contiene una matriz, el campo para hacer referencia a una matriz distinta. Sin embargo, se pueden cambiar los elementos de la matriz almacenados en un campo de solo lectura. Código que toma decisiones o realiza operaciones que se basan en los elementos de una matriz de solo lectura que son accesibles públicamente podría contener una vulnerabilidad de seguridad explotable.

 Tenga en cuenta que también tiene un campo público infringe la regla de diseño [CA1051: no declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir la vulnerabilidad de seguridad identificada por esta regla, no confíe en el contenido de una matriz de solo lectura que son accesibles públicamente. Se recomienda encarecidamente que utilice uno de los procedimientos siguientes:

-   Reemplace la matriz con una colección fuertemente tipada que no se puede cambiar. Para obtener más información, consulta <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

-   Reemplace el campo público con un método que devuelve un clon de una matriz privada. Dado que el código no se basa en el clon, no hay ningún riesgo si se modifican los elementos.

 Si opta por el segundo método, no Reemplace el campo con una propiedad; propiedades que devuelven matrices afectan negativamente afectan al rendimiento. Para obtener más información, consulte [CA1819: propiedades no deberían devolver matrices](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Se recomienda encarecidamente no usar la exclusión de una advertencia de esta regla. Se producen casi ningún escenarios donde el contenido de un campo de solo lectura no es importante. Si este es el caso con su escenario, quite el `readonly` modificador en lugar de excluir el mensaje.

## <a name="example"></a>Ejemplo
 Este ejemplo muestra los peligros de infringir esta regla. La primera parte muestra una biblioteca de ejemplo que tiene un tipo, `MyClassWithReadOnlyArrayField`, que contiene dos campos (`grades` y `privateGrades`) que no son seguras. El campo `grades` es público y, por tanto, vulnerable a cualquier llamador. El campo `privateGrades` es privado, pero sigue siendo vulnerable porque se devuelve a los llamadores por el `GetPrivateGrades` método. El `securePrivateGrades` campo se expone de forma segura mediante el `GetSecurePrivateGrades` método. Se declara como privado para seguir los procedimientos de diseño recomendados. La segunda parte muestra código que cambia los valores almacenados en el `grades` y `privateGrades` los miembros.

 La biblioteca de clases de ejemplo aparece en el ejemplo siguiente.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example"></a>Ejemplo
 El código siguiente utiliza la biblioteca de clases de ejemplo para ilustrar los problemas de seguridad de la matriz de solo lectura.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

 El resultado de este ejemplo es:

 **Antes de manipulación: grados: 90, 90, 90 grados privada: 90, 90, 90 grados seguros, 90, 90, 90**
**después de la manipulación: grados: 90, 555, 90 grados privada: 90, 555, 90 grados seguros, 90, 90, 90**
## <a name="see-also"></a>Vea también
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>