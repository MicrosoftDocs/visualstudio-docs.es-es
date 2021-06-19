---
title: Propiedades de los roles de dominio
description: Obtenga información sobre las propiedades asociadas a un rol de dominio, como Tipo de colección, Atributos personalizados y Propiedades que se pueden abrir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 670704a86f0c149d26c7c869259c0f2f6bb75881
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385153"
---
# <a name="properties-of-domain-roles"></a>Propiedades de los roles de dominio
Las propiedades de la tabla siguiente están asociadas a un rol de dominio. Para obtener información sobre los roles de dominio, vea [Descripción de modelos, clases y relaciones.](../modeling/understanding-models-classes-and-relationships.md) Para obtener más información sobre cómo usar estas propiedades, vea [Personalizar y extender un Domain-Specific language](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|Tipo de colección|Si este rol tiene una multiplicidad de 0...* o 1.. , esta propiedad personaliza el tipo genérico que se usa para almacenar la colección \* de vínculos.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> se usa|
|Atributos personalizados|Los atributos que especifique aquí se agregarán como atributos a la clase de código generada.|<ninguno\>|
|Is Property Browsable|Si es y si la multiplicidad de la relación es `True` 0...1 o 1..1, el usuario puede examinar la propiedad de rol en la **ventana** Propiedades. La propiedad muestra el nombre del elemento en el otro extremo del vínculo de relación.|`True`|
|Generador de propiedades Is|Si `True` es , se genera una propiedad de rol para este rol, que puede usar para recorrer la relación en el código del programa. Si establece este valor false, puede recorrer la relación de una manera menos eficaz mediante el uso de métodos estáticos de la relación de dominio.|`True`|
|Modificador de acceso del getter de propiedad|Modificador de acceso para el getter de la propiedad generada ( `public` , , , o `internal` `private` `protected` `protected internal` ).|`public`|
|Modificador de acceso del setter de propiedad|Modificador de acceso para el setter de la propiedad generada ( `public` , , , o `internal` `private` `protected` `protected internal` ).|`public`|
|Multiplicidad|Número de elementos del modelo que pueden desempeñar el rol opuesto ( `0..1` , `1..1` , o `0..*` `1..*` ). Si la multiplicidad es o , la propiedad generada representa una colección; de lo contrario, la propiedad generada `0..*` representa un único elemento de `1..*` modelo.|Depende del tipo de relación y de si este es el rol de origen o de destino de la relación.|
|Nombre|Nombre del rol de dominio. Esta propiedad no puede contener espacios en blanco.|Nombre de la clase de dominio del reproductor de roles para este rol.|
|Propaga la copia|`DoNotPropagateCopy` - El reproductor de roles copiado no tendrá ninguna copia de este vínculo.<br /><br /> `PropagateCopyToLinkOnly` - El vínculo copiado apunta al reproductor de roles opuesto existente.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` - El vínculo copiado apunta a una copia del reproductor de rol opuesto.|`PropagateCopyToLinkAndOppositeRolePlayer` para los roles de origen de las incrustaciones.<br /><br /> `DoNotPropagateCopy` para otros roles.<br /><br /> Para obtener más información, vea [Personalización del comportamiento de copia.](../modeling/customizing-copy-behavior.md)|
|Propaga la eliminación|`True` para eliminar el elemento que desempeña este rol cuando se elimina el vínculo asociado.|`True` para el destino de un rol de inserción.<br /><br /> `False` para otros roles.|
|Nombre de la propiedad|Nombre de la propiedad generada en el código del reproductor de roles. Este nombre no puede contener espacios en blanco.|Nombre del rol opuesto si este rol tiene una multiplicidad de cero a uno o de uno a uno. de lo contrario, el nombre plural del rol opuesto.|
|Reproductor de roles|Clase de dominio del elemento que puede desempeñar este rol en la relación. Esta propiedad es de solo lectura.|Clase de dominio del reproductor de roles para este rol.|
|Notas|Notas informales asociadas al rol de dominio.|<ninguno\>|
|Category|Categoría bajo la que aparece la propiedad generada en la **ventana Propiedades** del diseñador generado. Si esta propiedad está vacía, la propiedad generada aparece en la **categoría** Misc|<ninguno\>|
|Descripción|Descripción que se usa para documentar el código y que se usa en la interfaz de usuario del diseñador generado.<br /><br /> La descripción aparece en la información sobre herramientas de IntelliSense para la propiedad generada en la clase del reproductor de roles.|`Description for`*el nombre completo del rol*|
|Display Name (Nombre para mostrar)|Nombre que se muestra en el diseñador generado para el rol de dominio.|Valor ajustado de la propiedad Name.|
|Help Keyword|Palabra clave opcional que se usa para indexar la ayuda F1 para el rol de dominio.|\<none>|
|Nombre para mostrar de la propiedad|Nombre que se muestra en el diseñador generado para la propiedad de rol generada.|Valor ajustado de la propiedad Nombre de propiedad.|

> [!NOTE]
> El valor predeterminado de un nombre para mostrar se basa en el valor de propiedad asociado insertando espacios delante de cada carácter en mayúscula precedido por un carácter en minúsculas y que no va seguido de otro carácter en mayúsculas.

## <a name="see-also"></a>Vea también

- [Propiedades de las relaciones de dominio](../modeling/properties-of-domain-relationships.md)