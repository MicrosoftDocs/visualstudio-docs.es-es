---
title: Propiedades de los diagramas de | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords: Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: "25"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: fcd30a30bdae896be5aceb9dc685a5fb762ee4af
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-diagrams"></a>Propiedades de los diagramas
Puede establecer propiedades que especifican cómo los diagramas aparecerá en el diseñador generado. Por ejemplo, puede especificar un color predeterminado para el texto en el diagrama.  
  
 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información acerca de cómo utilizar estas propiedades, vea [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 En la tabla siguiente se enumera las propiedades de diagramas.  
  
|Propiedad|Descripción|Default|  
|--------------|-----------------|-------------|  
|Color de relleno|El color de relleno para el diagrama.|Blanco|  
|Color del texto|El color del texto que se muestra en el diagrama.|Negro|  
|Modificador de acceso|El modificador de acceso de la clase (pública o interna).|Público|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código generado.|\<Ninguno >|  
|Genera doble derivadas|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tiene un Constructor personalizado|Si `True`, se proporciona un constructor personalizado en el código fuente. Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Modificador de herencia|Describe el tipo de herencia de la clase de código de origen que se genera a partir del diagrama (`none`, `abstract` o `sealed`).|Ninguna|  
|Diagrama de base|La clase base de este diagrama.|(ninguno)|  
|Name|El nombre de este diagrama.|Nombre actual|  
|Espacio de nombres|El espacio de nombres que está afiliado a este diagrama.|Espacio de nombres actual|  
|Clase que representa|La clase de dominio raíz que representa este diagrama.|Clase raíz actual si es aplicable|  
|Notas|Notas informales que están asociadas a este elemento.|\<Ninguno >|  
|Expone el Color de relleno como propiedad|Si `True`, el usuario puede establecer el color de relleno del diagrama del diseñador generado. Para definir esta opción, haga clic en la forma de diagrama y haga clic en **Explosed agregar**.|False|  
|Expone el Color del texto como propiedad|Si `True`, el usuario puede establecer el color del texto del diagrama en el diseñador generado. Para definir esta opción, haga clic en la forma de diagrama y haga clic en **Explosed agregar**.|False|  
|Descripción|La descripción que se utiliza para documentar el diseñador generado.|\<Ninguno >|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para este diagrama.|\<Ninguno >|  
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 de este diagrama.|\<Ninguno >|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)