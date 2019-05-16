---
title: Propiedades de las formas de imagen | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
ms.assetid: 9ce00ccd-07f2-4640-ac96-2a60481d0d72
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d51801c1be56504fa4bf4ed2046d463db0e99aae
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701501"
---
# <a name="properties-of-image-shapes"></a>Propiedades de las formas de imagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar formas de imagen para especificar cómo aparecen las clases de dominio en un diseñador generado. Definir una forma de imagen estableciendo el `Image` propiedad de la clase a un archivo de imagen predefinidos. Se admiten los siguientes formatos:  
  
- .gif  
  
- .jpg  
  
- .jpeg  
  
- .bmp  
  
- .wmf  
  
- .emf  
  
- .png  
  
  De forma predeterminada, los archivos de recursos del diseñador, como archivos de imagen, se encuentran en el **recursos** carpeta en el **Dsl** proyecto.  
  
  Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
  Las formas de imagen tienen las propiedades que aparecen en la tabla siguiente.  
  
|Propiedad|Descripción|Default|  
|--------------|-----------------|-------------|  
|Color de relleno|El color de relleno de esta forma.|Blanco|  
|Modo de degradado de relleno|El modo de degradado de relleno de esta forma.|Horizontal|  
|Tiene puntos de conexión predeterminada|Si `True`, la forma usará superior, inferior, izquierda y de puntos de conexión adecuado en el diseñador generado.|False|  
|Color del contorno|El color del contorno de esta forma.|Negro|  
|Estilo de guión del contorno|El estilo de guión del contorno de esta forma (sólido, guión, punto, DashDot, DashDotDot o personalizado).|Sólido|  
|Grosor del contorno|El grosor del contorno de esta forma.|0.03125|  
|Color del texto|El color que se usa para los elementos Decorator de texto que están asociados con esta forma.|Negro|  
|Modificador de acceso|El modificador de acceso de la forma de geometría (pública o interna).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código fuente que se genera a partir de esta forma.|\<none>|  
|Genera doble derivada|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|No tiene Constructor personalizado|Si `True`, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la forma de imagen (`none`, `abstract` o `sealed`).|ninguna|  
|Forma de imagen base|La clase base de esta forma.|(ninguno)|  
|Name|El nombre de esta forma.|Nombre actual|  
|Espacio de nombres|El espacio de nombres que está asociado a esta forma.|Espacio de nombres actual|  
|Tipo de información sobre herramientas|El lugar donde se define la información sobre herramientas (fijo, variable o ninguno). Si se ha corregido, a continuación, el valor de la `Fixed Tooltip Text` propiedad se utiliza como la información sobre herramientas; si la variable, la información sobre herramientas se define mediante código personalizado.|ninguna|  
|Notas|Notas informales que están asociadas con esta forma.|\<none>|  
|Alto inicial|Alto inicial de esta forma, en pulgadas.|1|  
|Ancho inicial|Ancho inicial de esta forma, en pulgadas.|1.5|  
|Color de relleno expuestos como propiedad<br /><br /> Modo de degradado de relleno expuestos<br /><br /> Color del contorno puede exponer como propiedad<br /><br /> Estilo de guión del contorno puede exponer como propiedad<br /><br /> Expone el grosor del contorno como propiedad<br /><br /> Expone el Color del texto|Si `True`, el usuario puede establecer la propiedad indicada de una forma. Para ello, haga clic en la definición de la forma y haga clic en **agregar expuestos**.|False|  
|Descripción|Se usa para documentar el diseñador generado.|\<none>|  
|Display Name|El nombre que se mostrará en el diseñador generado para esta forma.|\<none>|  
|Texto de información sobre herramientas fijo|El texto que se usa para una información sobre herramientas fija.|\<none>|  
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 para este elemento.|\<none>|  
|Imagen|La ruta de acceso al archivo de imagen que se usa para esta forma.|\<none>|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
