---
title: Propiedades de las calles
description: Obtenga información sobre cómo las calles dividen un diagrama en áreas verticales u horizontales, y cómo puede definir otras formas que se mostrarán dentro de las calles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9c171bda2670b698297dd876a8a4403a91cd4af7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386493"
---
# <a name="properties-of-swimlanes"></a>Propiedades de las calles
Puede agregar calles a un diagrama. Las calles dividen un diagrama en áreas verticales u horizontales. Puede definir otras formas que se mostrarán dentro de las calles. Para obtener más información, [vea How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [Personalizar y extender un Domain-Specific language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Las calles tienen las propiedades que se enumeran en la tabla siguiente.

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|Color de relleno del cuerpo|Color de relleno para el cuerpo de la calle.|Blanco|
|Color de relleno de encabezado|Color de relleno del encabezado de la calle.|Gris oscuro|
|Color separador|Color de la línea separadora.|LightGray|
|Estilo de línea separadora|Estilo de la línea separadora ( `Solid` , , , , o `Dash` `Dot` `DashDot` `DashDotDot` `Custom` ).|`Dash`|
|Grosor del separador|Grosor de la línea separadora en pulgadas.|0.03125|
|Color de texto|Color que se usa para los decoradores de texto asociados a esta calle.|Negro|
|Modificador de acceso|Nivel de acceso de la clase ( `public` o `internal` ).|Público|
|Atributos personalizados|Se usa para agregar atributos a la clase de código que se genera a partir de esta calle.|\<none>|
|Genera una doble derivada|Si es , se generarán una clase base y una clase parcial (para admitir la personalización mediante `True` invalidaciones). Para obtener más información, [vea Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|False|
|Tiene un constructor personalizado|Si `True` es , se proporciona un constructor personalizado en el código fuente. Para obtener más información, [vea Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|False|
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la calle ( `none` , `abstract` o `sealed` ).|ninguno|
|Calle base|Clase base de esta calle.|(ninguno)|
|Nombre|Nombre de esta calle.|Nombre actual|
|Espacio de nombres|Espacio de nombres que está asociado a esta calle.|Espacio de nombres actual|
|Tipo de información sobre herramientas|Cómo se define la información sobre herramientas ( `fixed` `variable` , o `none` ). Si es , se usa el valor de la propiedad ; si es , la información sobre herramientas `fixed` se define en código `Fixed Tooltip Text` `variable` personalizado.|\<none>|
|Notas|Notas informales asociadas a esta calle.|\<none>|
|Alignment|Alineación horizontal o vertical.|Vertical|
|Alto inicial|Alto inicial de esta calle, en pulgadas. Solo se aplica a las calles horizontales.|0|
|Ancho inicial|Ancho inicial de esta calle, en pulgadas. Solo se aplica a las calles verticales.|0|
|Expone el color del texto|Si `True` es , el usuario puede establecer el color de una calle en el diseñador generado. Para establecer esto, haga clic con el botón derecho en la forma de calle y haga clic **en Agregar expuesto.**|False|
|Descripción|Se usa para documentar el diseñador generado.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se mostrará en el diseñador generado para hacer referencia a esta clase de calle.|\<none>|
|Texto de información sobre herramientas corregido|Texto que se usa para una información sobre herramientas fija.|\<none>|
|Help Keyword|Palabra clave que se usa para indexar la ayuda F1 para esta calle.|\<none>|

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))