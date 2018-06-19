---
title: Propiedades de los roles de dominio
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 48e2ba4180e72b68838e33f099fbb31186006698
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31951221"
---
# <a name="properties-of-domain-roles"></a>Propiedades de los roles de dominio
Las propiedades en la siguiente tabla están asociadas con un rol de dominio. Para obtener información acerca de las funciones de dominio, consulte [descripción de los modelos, las clases y relaciones](../modeling/understanding-models-classes-and-relationships.md). Para obtener más información acerca de cómo utilizar estas propiedades, vea [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Property|Descripción|Default|
|--------------|-----------------|-------------|
|Tipo de colección|Si este rol tiene una multiplicidad de 0.. * o 1.. \*, esta propiedad personaliza el tipo genérico que se utiliza para almacenar el conjunto de vínculos.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> se utiliza|
|Atributos personalizados|Atributos que especifique aquí se agregará como atributos a la clase de código generado.|< none\>|
|Es la propiedad admite la exploración|Si `True`, y si la multiplicidad de la relación es de 0.. 1 o 1.. 1, se pueden examinar las propiedades de rol por el usuario en el **propiedades** ventana. La propiedad muestra el nombre del elemento en el otro extremo del vínculo de relación.|`True`|
|Es el generador de propiedad|Si `True`, se genera una propiedad de rol para este rol, que puede utilizar para recorrer la relación en el código de programa. Si se establece false, puede recorrer la relación de forma menos eficaz mediante el uso de métodos estáticos de la relación de dominio.|`True`|
|Modificador de acceso de captador de propiedad|El modificador de acceso para el captador de la propiedad generada (`public`, `internal`, `private`, `protected`, o `protected internal`).|`public`|
|Modificador de acceso de establecedor de propiedad|El modificador de acceso para el establecedor de la propiedad generada (`public`, `internal`, `private`, `protected`, o `protected internal`).|`public`|
|Multiplicity|El número de elementos del modelo que puede reproducir la función opuesta (`0..1`, `1..1`, `0..*`, o `1..*`). Si la multiplicidad es `0..*` o `1..*`, a continuación, la propiedad generada representa una colección; en caso contrario, la propiedad generada representa un elemento de modelo simple.|Depende del tipo de relación y si se trata del rol de origen o destino en la relación.|
|nombre|El nombre de la función de dominio. Esta propiedad no puede contener espacios en blanco.|El nombre de la clase de dominio del Reproductor de rol para este rol.|
|Propaga copia|`DoNotPropagateCopy` -El encargado de la función copiada no tendrá ninguna copia de este vínculo.<br /><br /> `PropagateCopyToLinkOnly` -El vínculo copiado apunta a la existente función opuesto.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -El vínculo copiado apunta a una copia de la función opuesto.|`PropagateCopyToLinkAndOppositeRolePlayer` para los roles de origen de las incrustaciones.<br /><br /> `DoNotPropagateCopy` para otros roles.<br /><br /> Para obtener más información, vea [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md)|
|Propaga la eliminación|`True` Para eliminar el elemento que esta función se reproduce cuando se elimina el vínculo asociado.|`True` para el destino de una función de incrustación.<br /><br /> `False` para otros roles.<br /><br /> Para obtener más información, consulte [personalizar el comportamiento de eliminación](../modeling/customizing-deletion-behavior.md).|
|Nombre de la propiedad|El nombre de la propiedad que se generan en el código del Reproductor de rol. Este nombre no puede contener espacios en blanco.|El nombre de la función opuesta si este rol tiene un cero a uno o una multiplicidad de uno a uno; en caso contrario, el nombre de la función opuesta pluralized.|
|Encargado de función|La clase de dominio del elemento que se puede reproducir este rol en la relación. Esta propiedad es de sólo lectura.|La clase de dominio del Reproductor de rol para este rol.|
|Notas|Notas informales que están asociadas con el rol de dominio.|< none\>|
|Categoría|La categoría en la que la propiedad generada aparece en la **propiedades** ventana en el diseñador generado. Si esta propiedad está vacía, la propiedad generada aparece bajo la **varios** categoría|< none\>|
|Descripción|La descripción que se usa para documentar código y se usa en la interfaz de usuario del diseñador generado.<br /><br /> La descripción aparece en la información sobre herramientas de IntelliSense para la propiedad generada en la clase de Reproductor de rol.|`Description for` *el nombre completo de la función*|
|Nombre para mostrar|El nombre que se muestra en el diseñador generado para el rol de dominio.|El valor ajustado de la propiedad Name.|
|Help Keyword|La palabra clave opcional que se utiliza para indizar la Ayuda F1 para el rol de dominio.|\<Ninguno >|
|Propiedad nombre para mostrar|El nombre que se muestra en el diseñador generado para la propiedad de función generado.|El valor ajustado de la propiedad de nombre de la propiedad.|

> [!NOTE]
> El valor predeterminado de un nombre para mostrar se basa en el valor de propiedad asociado insertando espacios antes de cada carácter en mayúsculas que va precedida por un carácter en minúscula y no seguido por otro carácter en mayúsculas.

## <a name="see-also"></a>Vea también

- [Propiedades de las relaciones de dominio](../modeling/properties-of-domain-relationships.md)