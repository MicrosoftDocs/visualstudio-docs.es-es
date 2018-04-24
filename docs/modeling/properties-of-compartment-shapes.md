---
title: Propiedades de las formas de compartimiento
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 95af639a6874aac79d96693dcf58a8d6b2088f80
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="properties-of-compartment-shapes"></a>Propiedades de las formas de compartimiento
Formas de compartimiento son una de las formas en que se puede usar para mostrar una clase de dominio en un lenguaje específico de dominio. Puede expandir y contraer los compartimientos.

 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información acerca de cómo utilizar estas propiedades, vea [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Formas de compartimiento tienen las propiedades que se muestran en la tabla siguiente.

|Property|Descripción|Default|
|--------------|-----------------|-------------|
|Valor predeterminado expandir el estado de contracción|Si `Expanded`, se muestran los compartimientos durante la creación. Si `Collapsed`, no lo son.|Expandido|
|Color de relleno|El color de relleno de esta forma.|Blanco|
|Modo degradado de relleno|El modo de degradado de relleno de esta forma.|Horizontal|
|Geometría|La geometría de esta forma (rectángulo o rectángulo redondeado).|Rectángulo|
|Tiene puntos de conexión predeterminados|Si `True`, la forma usará superior, inferior, izquierda y puntos de conexión adecuada en el diseñador generado.|False|
|Está Visible compartimiento único encabezado|Si `False`y la forma tiene un compartimento único, el encabezado del compartimiento no está visible.|True|
|Color del contorno|El color del contorno de esta forma.|Negro|
|Estilo de guión de esquema|El estilo de guión de esquema de esta forma (sólido, guión, punto, línea mixta, DashDotDot, personalizado).|Sólido|
|Grosor del contorno|El grosor del contorno de esta forma.|0.03125|
|Color del texto|El color usado para decoradores de texto que están asociados con esta forma.|Negro|
|Modificador de acceso|El nivel de acceso de la forma de compartimiento (`public` o `internal`).|Public|
|Atributos personalizados|Usar para agregar atributos a la clase de código de origen que se genera a partir de esta forma de compartimiento|\<Ninguno >|
|Genera doble derivadas|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Tiene un Constructor personalizado|Si `True`, se proporciona un constructor personalizado en el código fuente. Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificador de herencia|Describe el tipo de herencia de la clase de código de origen que se genera a partir de la forma de compartimiento (`none`, `abstract` o `sealed`).|Ninguna|
|Forma de compartimiento base|La clase base de esta forma.|(ninguno)|
|nombre|El nombre de esta forma.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está afiliado a esta forma.|Espacio de nombres actual|
|ToolTip (tipo)|Cómo se define la información sobre herramientas (fijo, variable o ninguno). Si, a continuación, corrige el valor de la `Fixed Tooltip Text` propiedad se utiliza como la información sobre herramientas; si la variable, la información sobre herramientas se define en el código personalizado.|ninguna|
|Notas|Notas informales que están asociadas con esta forma.|\<Ninguno >|
|Alto inicial|El alto inicial de esta forma, en pulgadas. Formas de compartimiento, esto es el alto de la sección de encabezado solo y no puede cambiarse.|1|
|Ancho inicial|Ancho inicial de esta forma, en pulgadas.|1.5|
|Color de relleno expuesto como propiedad<br /><br /> Modo degradado de relleno expuesto<br /><br /> Expone el Color del contorno como propiedad<br /><br /> Expone el estilo de guión de esquema como propiedad<br /><br /> Expone el grosor del contorno como propiedad<br /><br /> Expone el Color del texto|Si `True`, el usuario puede establecer la propiedad de una forma indicada. Para definir esta opción, haga clic en la definición de la forma y haga clic en **agregar expone**.|False|
|Descripción|Se utiliza para documentar el diseñador generado.|\<Ninguno >|
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para esta forma.|\<Ninguno >|
|Texto de información sobre herramientas fijo|El texto que se usa para una información sobre herramientas fijo.|\<Ninguno >|
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 de esta forma.|\<Ninguno >|

## <a name="see-also"></a>Vea también

- [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)