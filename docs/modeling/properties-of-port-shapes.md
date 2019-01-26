---
title: Propiedades de las formas de puerto
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5559bd3b27f66ab54a05ca7be184b8aff34ae636
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938411"
---
# <a name="properties-of-port-shapes"></a>Propiedades de las formas de puerto
Puede usar formas de puerto que representen clases de dominio en el diseñador generado.

 Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Formas de puerto tienen las propiedades que aparecen en la tabla siguiente.

|Property|Descripción|Default|
|-|-|-|
|Color de relleno|El color de relleno de esta forma.|Blanco|
|Modo de degradado de relleno|El modo de degradado de relleno de esta forma.|Horizontal|
|geometría|La geometría de esta forma (rectángulo, rectángulo redondeado, círculo o elipse).|Rectángulo|
|Tiene puntos de conexión predeterminada|Si `True`, la forma usará superior, inferior, izquierda y de puntos de conexión adecuado en el diseñador generado.|False|
|Color del contorno|El color del contorno de esta forma.|Negro|
|Estilo de guión del contorno|El estilo de guión del contorno de esta forma (sólido, guión, punto, DashDot, DashDotDot o personalizado).|Sólido|
|Grosor del contorno|El grosor del contorno de esta forma.|0.03125|
|Color del texto|El color que se usa para los elementos Decorator de texto que están asociados con esta forma.|Negro|
|Modificador de acceso|El nivel de acceso de la clase (`public` o `internal`).|Public|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código fuente que se genera a partir de esta forma.|\<none>|
|Genera doble derivada|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md)|False|
|No tiene Constructor personalizado|Si `True`, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificador de herencia|Describe el tipo de herencia de la clase de código de origen que se genera a partir del puerto (`none`, `abstract` o `sealed`).|ninguna|
|Puerto base|La clase base de esta forma.|(ninguno)|
|nombre|El nombre de esta forma.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está asociado a esta forma.|Espacio de nombres actual|
|Tipo de información sobre herramientas|Cómo se define la información sobre herramientas (fijo, variable o ninguno). Si se ha corregido, a continuación, el valor de la `Fixed Tooltip Text` propiedad se utiliza como la información sobre herramientas; si la variable, la información sobre herramientas se define mediante código personalizado.|ninguna|
|Notas|Notas informales que están asociadas con esta forma.|\<none>|
|Alto inicial|Alto inicial de esta forma, en pulgadas.|1|
|Ancho inicial|Ancho inicial de esta forma, en pulgadas.|1.5|
|Color de relleno expuestos como propiedad<br /><br /> Modo de degradado de relleno expuestos<br /><br /> Color del contorno puede exponer como propiedad<br /><br /> Estilo de guión del contorno puede exponer como propiedad<br /><br /> Expone el grosor del contorno como propiedad<br /><br /> Expone el Color del texto|Si `True`, el usuario puede establecer la propiedad indicada de una forma. Para ello, haga clic en la definición de la forma y haga clic en **agregar expuestos**.|False|
|Descripción|Se usa para documentar el diseñador generado.|\<none>|
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para esta forma.|\<none>|
|Texto de información sobre herramientas fija|El texto que se usa para una información sobre herramientas fija.|\<none>|
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 para esta forma.|\<none>|

## <a name="see-also"></a>Vea también

- [Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)