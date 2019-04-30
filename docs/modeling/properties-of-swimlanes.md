---
title: Propiedades de las calles
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab2e10eed7452bf58390513bed68fac3f4c9a0f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823912"
---
# <a name="properties-of-swimlanes"></a>Propiedades de las calles
Puede agregar las calles a un diagrama. Las calles dividen un diagrama en áreas verticales u horizontales. Puede definir otras formas que se muestre en las calles. Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Las calles tienen las propiedades que aparecen en la tabla siguiente.

|Propiedad|Descripción|Default|
|-|-|-|
|Color de relleno del cuerpo|El color de relleno para el cuerpo de la calle.|Blanco|
|Color de relleno de encabezado|El color de relleno para el encabezado del carril.|DarkGray|
|Color del separador|El color de la línea de separación.|LightGray|
|Estilo del separador de línea|El estilo de la línea de separación (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, o `Custom`).|`Dash`|
|Grosor del separador|El grosor de la línea de separación en pulgadas.|0.03125|
|Color del texto|El color que se usa para los elementos Decorator de texto que están asociados a esta calle.|Negro|
|Modificador de acceso|El nivel de acceso de la clase (`public` o `internal`).|Public|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código que se genera a partir de esta calle.|\<none>|
|Genera doble derivada|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|No tiene Constructor personalizado|Si `True`, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la calle (`none`, `abstract` o `sealed`).|ninguna|
|Carril base|La clase base de esta calle.|(ninguno)|
|Name|El nombre de esta calle.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está asociado a esta calle.|Espacio de nombres actual|
|Tipo de información sobre herramientas|Cómo se define la información sobre herramientas (`fixed`, `variable`, o `none`). Si `fixed`, a continuación, el valor de la `Fixed Tooltip Text` propiedad se usa; si `variable`, a continuación, la información sobre herramientas se define mediante código personalizado.|\<none>|
|Notas|Notas informales asociadas con esta calle.|\<none>|
|Alineación|Alineación horizontal o vertical.|Vertical|
|Alto inicial|Alto inicial de este carril, en pulgadas. Se aplica solamente a carriles horizontales.|0|
|Ancho inicial|Ancho inicial de este carril, en pulgadas. Se aplica solamente a carriles verticales.|0|
|Expone el Color del texto|Si `True`, el usuario puede establecer el color de una calle en el diseñador generado. Para ello, haga clic en la forma de calle y haga clic en **agregar expuestos**.|False|
|Descripción|Se usa para documentar el diseñador generado.|\<none>|
|Display Name|El nombre que se mostrará en el diseñador generado para hacer referencia a esta clase de calle.|\<none>|
|Texto de información sobre herramientas fijo|El texto que se usa para una información sobre herramientas fija.|\<none>|
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 para este carril.|\<none>|

## <a name="see-also"></a>Vea también

- [Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)