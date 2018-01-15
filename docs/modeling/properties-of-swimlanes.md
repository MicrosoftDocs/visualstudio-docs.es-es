---
title: Propiedades de las calles | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.swimlane
helpviewer_keywords: Domain-Specific Language, swimlane
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fdbd94abdaa3a1acb460a3b2a5b276d169c20269
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="properties-of-swimlanes"></a>Propiedades de las calles
Puede agregar las calles a un diagrama. Calles dividen un diagrama en áreas verticales u horizontales. Puede definir otras formas que se mostrará dentro de las calles. Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información acerca de cómo utilizar estas propiedades, vea [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Calles tienen las propiedades que se muestran en la tabla siguiente.  
  
|Property|Descripción|Default|  
|--------------|-----------------|-------------|  
|Color de relleno de cuerpo|El color de relleno para el cuerpo de la calle.|Blanco|  
|Color de relleno de encabezado|El color de relleno para el encabezado de la calle.|Gris oscuro|  
|Color del separador|El color de la línea de separación.|LightGray|  
|Estilo del separador de línea|El estilo de la línea de separación (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, o `Custom`).|`Dash`|  
|Grosor del separador|El grosor de la línea de separación en pulgadas.|0.03125|  
|Color del texto|El color que se usa para decoradores de texto que están asociados a esta calle.|Negro|  
|Modificador de acceso|El nivel de acceso de la clase (`public` o `internal`).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código que se genera a partir de esta calle.|\<Ninguno >|  
|Genera doble derivadas|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tiene un Constructor personalizado|Si `True`, se proporciona un constructor personalizado en el código fuente. Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herencia|Describe el tipo de herencia de la clase de código de origen que se genera a partir de la calle (`none`, `abstract` o `sealed`).|ninguna|  
|Calle base|La clase base de esta calle.|(ninguno)|  
|nombre|El nombre de esta calle.|Nombre actual|  
|Espacio de nombres|El espacio de nombres que está afiliado a este calle.|Espacio de nombres actual|  
|ToolTip (tipo)|¿Cómo se define la información sobre herramientas (`fixed`, `variable`, o `none`). Si `fixed`, a continuación, el valor de la `Fixed Tooltip Text` propiedad se utiliza; si `variable`, a continuación, la información sobre herramientas se define en el código personalizado.|\<Ninguno >|  
|Notas|Notas informales que están asociadas a esta calle.|\<Ninguno >|  
|Alineación|Alineación horizontal o vertical.|Vertical|  
|Alto inicial|El alto inicial de esta calle, en pulgadas. Aplicable únicamente a las calles horizontales.|0|  
|Ancho inicial|Ancho inicial de esta calle, en pulgadas. Aplicable únicamente a las calles verticales.|0|  
|Expone el Color del texto|Si `True`, el usuario puede establecer el color de una calle en el diseñador generado. Para definir esta opción, haga clic en la forma de calle y haga clic en **agregar expone**.|False|  
|Descripción|Se utiliza para documentar el diseñador generado.|\<Ninguno >|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para hacer referencia a esta clase de calle.|\<Ninguno >|  
|Texto de información sobre herramientas fijo|El texto que se usa para una información sobre herramientas fijo.|\<Ninguno >|  
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 para esta calle.|\<Ninguno >|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)