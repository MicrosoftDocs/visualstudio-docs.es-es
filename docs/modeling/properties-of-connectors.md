---
title: Propiedades de los conectores
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e8954727d7ee38b81ba5993b41e300ef1c6d66fc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="properties-of-connectors"></a>Propiedades de los conectores
Los conectores representan las relaciones de dominio en un diseñador generado.

 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información acerca de cómo utilizar estas propiedades, vea [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Conectores tienen las propiedades que se muestran en la tabla siguiente.

|Property|Descripción|Default|
|--------------|-----------------|-------------|
|Color|El color de este conector.|Negro|
|Estilo de guión|El estilo de guión para la línea para este conector (sólido, guión, punto, línea mixta, DashDotDot o personalizado).|Sólido|
|Estilo de extremo de origen|El estilo de extremo de origen para este conector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o ninguno).|Ninguna|
|Estilo de extremo de destino|El estilo de extremo de destino para este conector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o ninguno).|Ninguna|
|Color del texto|El color que se usa para decoradores de texto que están asociados a este conector.|Negro|
|Thickness|El grosor de la línea para este conector, se mide en pulgadas.|0.03125|
|Modificador de acceso|El nivel de acceso de la clase (`public` o `internal`).|Public|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código de origen que se genera a partir de este conector.|\<Ninguno >|
|Genera doble derivadas|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Tiene un Constructor personalizado|Si `True`, se proporciona un constructor personalizado en el código fuente. Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificador de herencia|Describe el tipo de herencia de la clase de código de origen que se genera a partir del conector (`none`, `abstract` o `sealed`).|ninguna|
|Conector de base|La clase base de este conector.|(ninguno)|
|nombre|El nombre de este conector.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está afiliado a este conector.|Espacio de nombres actual|
|ToolTip (tipo)|Cómo se define la información sobre herramientas (fijo, variable o ninguno). Si, a continuación, corrige el valor de la `Fixed Tooltip Text` propiedad se utiliza como la información sobre herramientas; si la variable, la información sobre herramientas se define en el código personalizado.|\<Ninguno >|
|Notas|Notas informales que están asociadas a este conector.|\<Ninguno >|
|Estilo de enrutamiento|El estilo que se utiliza para el conector de enrutamiento. A `Rectilinear` conector hace ángulo recto activa según sea necesario; un `Straight` conector no lo hace.|Rectos|
|Color expuesta como propiedad<br /><br /> Estilo de guión expuesto como propiedad<br /><br /> Grosor expuesto como propiedad<br /><br /> Expone el Color del texto|Si `True`, el usuario puede establecer la propiedad de una forma indicada. Para definir esta opción, haga clic en la definición de la forma y haga clic en **agregar expone**.|False|
|Descripción|Se utiliza para documentar el diseñador generado.|\<Ninguno >|
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para este conector.|\<Ninguno >|
|Texto de información sobre herramientas fijo|El texto que se usa para una información sobre herramientas fijo.|\<Ninguno >|
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 para este elemento.|\<Ninguno >|

## <a name="see-also"></a>Vea también

- [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)