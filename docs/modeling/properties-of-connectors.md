---
title: Propiedades de los conectores
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6d2d3d747c128cfa2afbb63ae43289e0b50519b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810072"
---
# <a name="properties-of-connectors"></a>Propiedades de los conectores
Los conectores representan las relaciones de dominio en un diseñador generado.

 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Los conectores tienen las propiedades que se enumeran en la tabla siguiente.

|Propiedad.|Descripción|Default|
|-|-|-|
|Color|Color de este conector.|Negro|
|Estilo de guión|El estilo de guión para la línea de este conector (sólido, guión, punto, DashDot, DashDotDot o personalizado).|Sólido|
|Estilo de extremo de origen|El estilo del extremo de origen para este conector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|Ninguno|
|Estilo de extremo de destino|El estilo de extremo de destino para este conector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|Ninguno|
|Color del texto|Color que se usa para los decoradores de texto que están asociados a este conector.|Negro|
|Thickness|El grosor de la línea para este conector, medido en pulgadas.|0,03125|
|Modificador de acceso|Nivel de acceso de la clase ( `public` o `internal` ).|Público|
|Atributos personalizados|Se usa para agregar atributos a la clase de código fuente que se genera a partir de este conector.|\<none>|
|Genera Double derived|Si `True` es, se generarán una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Tiene un constructor personalizado|Si `True` es, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Inheritance (modificador)|Describe el tipo de herencia de la clase de código fuente que se genera a partir del conector ( `none` `abstract` o `sealed` ).|ninguno|
|Conector base|Clase base de este conector.|(ninguno)|
|NOMBRE|Nombre de este conector.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está afiliado a este conector.|Espacio de nombres actual|
|Tipo de información sobre herramientas|Cómo se define la información sobre herramientas (Fixed, variable o None). Si es Fixed, el valor de la `Fixed Tooltip Text` propiedad se usa como información sobre herramientas; si es variable, la información sobre herramientas se define en código personalizado.|\<none>|
|Notas|Notas informales asociadas a este conector.|\<none>|
|Estilo de enrutamiento|El estilo que se usa para enrutar el conector. Un `Rectilinear` conector hace que las vueltas a la derecha se realicen según sea necesario; un `Straight` conector no.|Recta|
|Color expuesto como propiedad<br /><br /> Estilo de guión expuesto como propiedad<br /><br /> Grosor expuesto como propiedad<br /><br /> Expone el color del texto|Si es `True` , el usuario puede establecer la propiedad indicada de una forma. Para establecer esto, haga clic con el botón secundario en la definición de la forma y haga clic en **Agregar expuesto**.|Falso|
|Descripción|Se usa para documentar el diseñador generado.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se mostrará en el diseñador generado para este conector.|\<none>|
|Texto de información sobre herramientas corregido|Texto que se usa para una información sobre herramientas fija.|\<none>|
|Help Keyword|Palabra clave que se usa para indizar la ayuda de F1 para este elemento.|\<none>|

## <a name="see-also"></a>Consulte también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))