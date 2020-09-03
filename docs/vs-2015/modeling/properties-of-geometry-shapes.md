---
title: Propiedades de las formas de geometría | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
ms.assetid: 3993a23e-eab3-4ceb-b475-c395d5992bfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10b6d282475d3298f15319d89684f9b042bee5f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671397"
---
# <a name="properties-of-geometry-shapes"></a>Propiedades de las formas geométricas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar formas de geometría para especificar cómo se muestran las instancias de las clases de dominio en un lenguaje específico del dominio. Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Las formas de geometría tienen las propiedades que se enumeran en la tabla siguiente.

|Propiedad|Descripción|Valor predeterminado|
|--------------|-----------------|-------------|
|Color de relleno|Color de relleno de esta forma.|Blanco|
|Modo de degradado de relleno|El modo de degradado de relleno de esta forma (horizontal, vertical, diagonal hacia delante, diagonal hacia atrás o ninguno).|Horizontal|
|Geometría|Geometría de esta forma (rectángulo, rectángulo redondeado, elipse o círculo).|Rectángulo|
|Tiene puntos de conexión predeterminados|Si es `True` , la forma usará los puntos de conexión superior, inferior, izquierdo y derecho en el diseñador generado.|Falso|
|Color del contorno|Color del contorno de esta forma.|Negro|
|Estilo de guión del contorno|El estilo de guión del contorno de esta forma (sólido, guión, punto, DashDot, DashDotDot o personalizado).|Sólido|
|Grosor del contorno|Grosor del contorno de esta forma.|0,03125|
|Color del texto|Color que se usa para los decoradores de texto que están asociados a esta forma.|Negro|
|Modificador de acceso|Modificador de acceso de la clase (pública o interna).|Público|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código fuente que se genera para esta forma.|\<none>|
|Genera Double derived|Si `True` es, se generarán una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Tiene un constructor personalizado|Si `True` es, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Inheritance (modificador)|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la forma ( `none` , `abstract` o `sealed` ).|None|
|Forma de geometría base|Clase base de esta forma.|(ninguno)|
|Nombre|Nombre de esta forma.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está asociado con esta forma.|Espacio de nombres actual|
|Tipo de información sobre herramientas|Cómo se define la información sobre herramientas (Fixed, variable o None). Si es Fixed, el valor de la `Fixed Tooltip Text` propiedad se usa como información sobre herramientas; si es variable, la información sobre herramientas se define en código personalizado.|Ninguno|
|Notas|Notas informales asociadas a este elemento.|\<none>|
|Alto inicial|Alto inicial de esta forma, en pulgadas.|1|
|Ancho inicial|Ancho inicial de esta forma, en pulgadas.|1.5|
|Color de relleno expuesto como propiedad<br /><br /> Modo de degradado de relleno expuesto<br /><br /> Color de esquema expuesto como propiedad<br /><br /> Estilo de guión del contorno expuesto como propiedad<br /><br /> Grosor del contorno expuesto como propiedad<br /><br /> Expone el color del texto|Si es `True` , el usuario puede establecer la propiedad indicada de una forma. Para establecer esto, haga clic con el botón secundario en la definición de la forma y haga clic en **Agregar expuesto**.|Falso|
|Descripción|La descripción que se usa para documentar el diseñador generado.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se mostrará en el diseñador generado para esta forma.|\<none>|
|Texto de información sobre herramientas corregido|Texto que se usa para una información sobre herramientas fija.|\<none>|
|Help Keyword|Palabra clave que se usa para indizar la ayuda de F1 para esta forma.|\<none>|

## <a name="see-also"></a>Consulte también
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
