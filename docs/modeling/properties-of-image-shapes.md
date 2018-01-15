---
title: Propiedades de las formas de imagen | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords: Domain-Specific Language, image shape
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e3ab33282c89617a74cc80623040ffc9176b761a
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="properties-of-image-shapes"></a>Propiedades de las formas de imagen
Puede usar formas de imagen para especificar cómo aparecen las clases de dominio en un diseñador generado. Define una forma de imagen, estableciendo el `Image` propiedad de la clase a un archivo de imagen predefinida. Se admiten los siguientes formatos:  
  
-   .gif  
  
-   .jpg  
  
-   .JPEG  
  
-   .bmp  
  
-   .wmf  
  
-   .emf  
  
-   .png  
  
 De forma predeterminada, los archivos de recursos del diseñador, como archivos de imagen, se encuentran en el **recursos**carpeta en el **Dsl** proyecto.  
  
 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información acerca de cómo utilizar estas propiedades, vea [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Formas de imagen tienen las propiedades que se muestran en la tabla siguiente.  
  
|Property|Descripción|Default|  
|--------------|-----------------|-------------|  
|Color de relleno|El color de relleno de esta forma.|Blanco|  
|Modo degradado de relleno|El modo de degradado de relleno de esta forma.|Horizontal|  
|Tiene puntos de conexión predeterminados|Si `True`, la forma usará superior, inferior, izquierda y puntos de conexión adecuada en el diseñador generado.|False|  
|Color del contorno|El color del contorno de esta forma.|Negro|  
|Estilo de guión de esquema|El estilo de guión de esquema de esta forma (sólido, guión, punto, línea mixta, DashDotDot o personalizado).|Sólido|  
|Grosor del contorno|El grosor del contorno de esta forma.|0.03125|  
|Color del texto|El color que se usa para decoradores de texto que están asociados con esta forma.|Negro|  
|Modificador de acceso|El modificador de acceso de la forma de geometría (pública o interna).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código de origen que se genera a partir de esta forma.|\<Ninguno >|  
|Genera doble derivadas|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tiene un Constructor personalizado|Si `True`, se proporciona un constructor personalizado en el código fuente. Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herencia|Describe el tipo de herencia de la clase de código de origen que se genera a partir de la forma de imagen (`none`, `abstract` o `sealed`).|ninguna|  
|Forma de la imagen base|La clase base de esta forma.|(ninguno)|  
|nombre|El nombre de esta forma.|Nombre actual|  
|Espacio de nombres|El espacio de nombres que está afiliado a esta forma.|Espacio de nombres actual|  
|ToolTip (tipo)|El lugar donde se define la información sobre herramientas (fijo, variable o ninguno). Si, a continuación, corrige el valor de la `Fixed Tooltip Text` propiedad se utiliza como la información sobre herramientas; si la variable, la información sobre herramientas se define en el código personalizado.|ninguna|  
|Notas|Notas informales que están asociadas con esta forma.|\<Ninguno >|  
|Alto inicial|El alto inicial de esta forma, en pulgadas.|1|  
|Ancho inicial|Ancho inicial de esta forma, en pulgadas.|1.5|  
|Color de relleno expuesto como propiedad<br /><br /> Modo degradado de relleno expuesto<br /><br /> Expone el Color del contorno como propiedad<br /><br /> Expone el estilo de guión de esquema como propiedad<br /><br /> Expone el grosor del contorno como propiedad<br /><br /> Expone el Color del texto|Si `True`, el usuario puede establecer la propiedad de una forma indicada. Para definir esta opción, haga clic en la definición de la forma y haga clic en **agregar expone**.|False|  
|Descripción|Se utiliza para documentar el diseñador generado.|\<Ninguno >|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para esta forma.|\<Ninguno >|  
|Texto de información sobre herramientas fijo|El texto que se usa para una información sobre herramientas fijo.|\<Ninguno >|  
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 para este elemento.|\<Ninguno >|  
|Imagen|La ruta de acceso al archivo de imagen que se usa para esta forma.|\<Ninguno >|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)