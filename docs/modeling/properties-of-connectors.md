---
title: Propiedades de los conectores
description: Obtenga información sobre que los conectores representan relaciones de dominio en un diseñador generado y que usa estas propiedades para personalizar y ampliar un lenguaje específico del dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 43f55aecf134bf8e4d043a4fc7f6ffa2201f8e95
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390820"
---
# <a name="properties-of-connectors"></a>Propiedades de los conectores
Los conectores representan relaciones de dominio en un diseñador generado.

 Para obtener más información, [vea How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [Personalizar y extender un Domain-Specific language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Los conectores tienen las propiedades que se enumeran en la tabla siguiente.

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|Color|Color de este conector.|Negro|
|Estilo de guion|Estilo de guion para la línea de este conector (Solid, Dash, Dot, DashDot, DashDotDot o Custom).|Sólido|
|Estilo de extremo de origen|Estilo final de origen para este conector (EmptyArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|Ninguno|
|Estilo final de destino|Estilo final de destino para este conector (EmptyArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|Ninguno|
|Color de texto|Color que se usa para los decoradores de texto asociados a este conector.|Negro|
|Thickness|El grosor de la línea para este conector, medido en pulgadas.|0.03125|
|Modificador de acceso|Nivel de acceso de la clase ( `public` o `internal` ).|Público|
|Atributos personalizados|Se usa para agregar atributos a la clase de código fuente que se genera a partir de este conector.|\<none>|
|Genera una doble derivada|Si es , se generarán una clase base y una clase parcial (para admitir la personalización mediante `True` invalidaciones). Para obtener más información, [vea Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|False|
|Tiene un constructor personalizado|Si `True` es , se proporciona un constructor personalizado en el código fuente. Para obtener más información, [vea Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|False|
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir del conector ( `none` , `abstract` o `sealed` ).|ninguno|
|Conector base|Clase base de este conector.|(ninguno)|
|Nombre|Nombre de este conector.|Nombre actual|
|Espacio de nombres|Espacio de nombres que está asociado a este conector.|Espacio de nombres actual|
|Tipo de información sobre herramientas|Cómo se define la información sobre herramientas (fija, variable o ninguna). Si es fijo, el valor de la propiedad se usa como información sobre herramientas; si es variable, la información sobre herramientas `Fixed Tooltip Text` se define en código personalizado.|\<none>|
|Notas|Notas informales asociadas a este conector.|\<none>|
|Estilo de enrutamiento|Estilo que se usa para enrutar el conector. Un `Rectilinear` conector realiza turnos angulares a la derecha según sea necesario; `Straight` un conector no.|Rectilíneo|
|Color expuesto como propiedad<br /><br /> Estilo de guion expuesto como propiedad<br /><br /> Grosor expuesto como propiedad<br /><br /> Expone el color del texto|Si `True` es , el usuario puede establecer la propiedad indicada de una forma. Para establecer esto, haga clic con el botón derecho en la definición de forma y haga clic **en Agregar expuesto.**|False|
|Descripción|Se usa para documentar el diseñador generado.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se mostrará en el diseñador generado para este conector.|\<none>|
|Texto de información sobre herramientas corregido|Texto que se usa para una información sobre herramientas fija.|\<none>|
|Help Keyword|Palabra clave que se usa para indexar la ayuda F1 para este elemento.|\<none>|

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))