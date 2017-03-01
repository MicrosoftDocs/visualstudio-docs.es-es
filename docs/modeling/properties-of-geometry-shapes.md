---
title: "Propiedades de las formas geométricas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
ms.assetid: 3993a23e-eab3-4ceb-b475-c395d5992bfc
caps.latest.revision: 21
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 54e600e5d626828824d5a2584e1ff4f7fdc09810
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-geometry-shapes"></a>Propiedades de las formas geométricas
Puede usar formas geométricas para especificar cómo se muestran las instancias de clases de dominio en un lenguaje específico de dominio. Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información acerca de cómo utilizar estas propiedades, consulte [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Formas geométricas tienen las propiedades que se muestran en la tabla siguiente.  
  
|Propiedad|Descripción|Default|  
|--------------|-----------------|-------------|  
|Color de relleno|El color de relleno de esta forma.|Blanco|  
|Modo degradado de relleno|El modo de degradado de relleno de la forma (Horizontal, Vertical, Diagonal hacia delante, hacia atrás Diagonal o ninguno).|Horizontal|  
|Geometría|La geometría de esta forma (rectángulo, rectángulo redondeado, elipse o círculo).|Rectángulo|  
|Tiene puntos de conexión predeterminada|Si `True`, la forma usará superior, inferior, izquierda y puntos de conexión adecuada en el diseñador generado.|False|  
|Color del contorno|El color del contorno de esta forma.|Negro|  
|Estilo de guión de esquema|El estilo de guión de esquema de esta forma (sólido, guión, punto, línea mixta, DashDotDot o personalizado).|Sólido|  
|Grosor del contorno|El grosor del contorno de esta forma.|0.03125|  
|Color del texto|El color que se utiliza para los elementos Decorator de texto que están asociado con esta forma.|Negro|  
|Modificador de acceso|El modificador de acceso de la clase (pública o interna).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código de origen que se genera para esta forma.|\<Ninguno >|  
|Genera doble derivada|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tiene un Constructor personalizado|Si `True`, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Inheritance Modifier|Describe el tipo de herencia de la clase de código de origen que se genera a partir de la forma (`none`, `abstract` o `sealed`).|ninguna|  
|Forma geométrica base|La clase base de esta forma.|(ninguno)|  
|Nombre|El nombre de esta forma.|Nombre actual|  
|Espacio de nombres|El espacio de nombres que está asociado a esta forma.|Espacio de nombres actual|  
|ToolTip (tipo)|Cómo se define la información sobre herramientas (fijo, variable o ninguno). Si, a continuación, el valor fijo de la `Fixed Tooltip Text` propiedad se utiliza como la información sobre herramientas; si la variable, la información sobre herramientas se define en el código personalizado.|Ninguna|  
|Notas|Notas informales que están asociados a este elemento.|\<Ninguno >|  
|Alto inicial|Alto inicial de esta forma, en pulgadas.|1|  
|Ancho inicial|Ancho inicial de esta forma, en pulgadas.|1.5|  
|Color de relleno expuesta como propiedad<br /><br /> Modo de degradado de relleno expuesto<br /><br /> Expone el Color del contorno como propiedad<br /><br /> Expone el estilo de guión de esquema como propiedad<br /><br /> Expone el grosor del contorno como propiedad<br /><br /> Expone el Color del texto|Si `True`, el usuario puede establecer la propiedad de la forma indicada. Para ello, haga clic en la definición de la forma y haga clic en **agregar expone**.|False|  
|Descripción|La descripción que se usa para documentar el diseñador generado.|\<Ninguno >|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para esta forma.|\<Ninguno >|  
|Texto de información sobre herramientas fijo|El texto que se usa para una información sobre herramientas fijo.|\<Ninguno >|  
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 para esta forma.|\<Ninguno >|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de herramientas de lenguajes específicos de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
