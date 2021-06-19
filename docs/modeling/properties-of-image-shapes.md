---
title: Propiedades de las formas de imagen
description: Obtenga información sobre las formas de imagen y cómo puede usar formas de imagen para especificar cómo aparecen las clases de dominio en un diseñador generado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98198b1197de6f5fda6a05a5bae58378a323f718
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390560"
---
# <a name="properties-of-image-shapes"></a>Propiedades de las formas de imagen

Puede usar formas de imagen para especificar cómo aparecen las clases de dominio en un diseñador generado. Defina una forma de imagen estableciendo la `Image` propiedad de la clase en un archivo de imagen predefinido. Se admiten los siguientes formatos:

- .gif

- .jpg

- .jpeg

- .bmp

- .wmf

- .emf

- .png

De forma predeterminada, los archivos de recursos del diseñador, como los archivos de imagen, se encuentran en la **carpeta Recursos** del **proyecto Dsl.**

Para obtener más información, [vea How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [Personalizar y extender un Domain-Specific language](../modeling/customizing-and-extending-a-domain-specific-language.md).

Las formas de imagen tienen las propiedades que se enumeran en la tabla siguiente.

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|Color de relleno|Color de relleno de esta forma.|Blanco|
|Modo de degradado de relleno|Modo de degradado de relleno de esta forma.|Horizontal|
|Tiene puntos de conexión predeterminados|Si `True` es , la forma usará puntos de conexión superior, inferior, izquierdo y derecho en el diseñador generado.|False|
|Color de contorno|Color del contorno de esta forma.|Negro|
|Estilo de guión de esquema|Estilo de guion de esquema de esta forma (Solid, Dash, Dot, DashDot, DashDotDot o Custom).|Sólido|
|Grosor del contorno|Grosor del contorno de esta forma.|0.03125|
|Color de texto|Color que se usa para los decoradores de texto asociados a esta forma.|Negro|
|Modificador de acceso|Modificador de acceso de la forma de geometría (pública o interna).|Público|
|Atributos personalizados|Se usa para agregar atributos a la clase de código fuente que se genera a partir de esta forma.|\<none>|
|Genera una doble derivada|Si es , se generarán una clase base y una clase parcial (para admitir la personalización mediante `True` invalidaciones). Para obtener más información, [vea Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|False|
|Tiene un constructor personalizado|Si `True` es , se proporciona un constructor personalizado en el código fuente. Para obtener más información, [vea Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|False|
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la forma de imagen ( `none` , `abstract` o `sealed` ).|ninguno|
|Forma de imagen base|Clase base de esta forma.|(ninguno)|
|Nombre|Nombre de esta forma.|Nombre actual|
|Espacio de nombres|Espacio de nombres que está asociado a esta forma.|Espacio de nombres actual|
|Tipo de información sobre herramientas|Lugar donde se define la información sobre herramientas (fija, variable o ninguna). Si es fijo, el valor de la propiedad se usa como información sobre herramientas; si es variable, la información sobre herramientas `Fixed Tooltip Text` se define en código personalizado.|ninguno|
|Notas|Notas informales asociadas a esta forma.|\<none>|
|Alto inicial|Alto inicial de esta forma, en pulgadas.|1|
|Ancho inicial|Ancho inicial de esta forma, en pulgadas.|1.5|
|Color de relleno expuesto como propiedad<br /><br /> Modo degradado de relleno expuesto<br /><br /> Color de contorno expuesto como propiedad<br /><br /> Estilo de guión de esquema expuesto como propiedad<br /><br /> Grosor del contorno expuesto como propiedad<br /><br /> Expone el color del texto|Si `True` es , el usuario puede establecer la propiedad indicada de una forma. Para establecer esto, haga clic con el botón derecho en la definición de forma y haga clic **en Agregar expuesto.**|False|
|Descripción|Se usa para documentar el diseñador generado.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se mostrará en el diseñador generado para esta forma.|\<none>|
|Texto de información sobre herramientas corregido|Texto que se usa para una información sobre herramientas fija.|\<none>|
|Help Keyword|Palabra clave que se usa para indexar la ayuda F1 para este elemento.|\<none>|
|Imagen|Ruta de acceso al archivo de imagen que se usa para esta forma.|\<none>|

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))