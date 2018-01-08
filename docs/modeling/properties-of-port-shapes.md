---
title: Propiedades de puerto formas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.port
helpviewer_keywords: Domain-Specific Language, port shape
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 3cc8f57b0615be6255425e396f0fc4ea3e763810
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="properties-of-port-shapes"></a>Propiedades de las formas de puerto
Puede usar formas de puerto para representar las clases de dominio en el diseñador generado.  
  
 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información acerca de cómo utilizar estas propiedades, vea [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Formas de puerto tienen las propiedades que se muestran en la tabla siguiente.  
  
|Property|Descripción|Default|  
|--------------|-----------------|-------------|  
|Color de relleno|El color de relleno de esta forma.|Blanco|  
|Modo degradado de relleno|El modo de degradado de relleno de esta forma.|Horizontal|  
|Geometría|La geometría de esta forma (rectángulo, rectángulo redondeado, elipse o círculo).|Rectángulo|  
|Tiene puntos de conexión predeterminados|Si `True`, la forma usará superior, inferior, izquierda y puntos de conexión adecuada en el diseñador generado.|False|  
|Color del contorno|El color del contorno de esta forma.|Negro|  
|Estilo de guión de esquema|El estilo de guión de esquema de esta forma (sólido, guión, punto, línea mixta, DashDotDot o personalizado).|Sólido|  
|Grosor del contorno|El grosor del contorno de esta forma.|0.03125|  
|Color del texto|El color que se usa para decoradores de texto que están asociados con esta forma.|Negro|  
|Modificador de acceso|El nivel de acceso de la clase (`public` o `internal`).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código de origen que se genera a partir de esta forma.|\<Ninguno >|  
|Genera doble derivadas|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, vea [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md)|False|  
|Tiene un Constructor personalizado|Si `True`, se proporciona un constructor personalizado en el código fuente. Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herencia|Describe el tipo de herencia de la clase de código de origen que se genera a partir del puerto (`none`, `abstract` o `sealed`).|ninguna|  
|Puerto de base|La clase base de esta forma.|(ninguno)|  
|nombre|El nombre de esta forma.|Nombre actual|  
|Espacio de nombres|El espacio de nombres que está afiliado a esta forma.|Espacio de nombres actual|  
|Tipo de sugerencia de herramienta|Cómo se define la información sobre herramientas (fijo, variable o ninguno). Si, a continuación, corrige el valor de la `Fixed Tooltip Text` propiedad se utiliza como la información sobre herramientas; si la variable, la información sobre herramientas se define en el código personalizado.|ninguna|  
|Notas|Notas informales que están asociadas con esta forma.|\<Ninguno >|  
|Alto inicial|El alto inicial de esta forma, en pulgadas.|1|  
|Ancho inicial|Ancho inicial de esta forma, en pulgadas.|1.5|  
|Color de relleno expuesto como propiedad<br /><br /> Modo degradado de relleno expuesto<br /><br /> Expone el Color del contorno como propiedad<br /><br /> Expone el estilo de guión de esquema como propiedad<br /><br /> Expone el grosor del contorno como propiedad<br /><br /> Expone el Color del texto|Si `True`, el usuario puede establecer la propiedad de una forma indicada. Para definir esta opción, haga clic en la definición de la forma y haga clic en **agregar expone**.|False|  
|Descripción|Se utiliza para documentar el diseñador generado.|\<Ninguno >|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para esta forma.|\<Ninguno >|  
|Texto de sugerencia fijo|El texto que se usa para una información sobre herramientas fijo.|\<Ninguno >|  
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 de esta forma.|\<Ninguno >|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)