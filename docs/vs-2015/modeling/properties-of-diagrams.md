---
title: Propiedades de los diagramas | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 43d5804f1a80b2616e209c47e594b29ad84911a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576246"
---
# <a name="properties-of-diagrams"></a>Propiedades de los diagramas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [propiedades de diagramas](https://docs.microsoft.com/visualstudio/modeling/properties-of-diagrams).  
  
Puede establecer las propiedades que especifican cómo aparecerán los diagramas del diseñador generado. Por ejemplo, puede especificar un color predeterminado para el texto en el diagrama.  
  
 Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 En la tabla siguiente se enumera las propiedades de los diagramas.  
  
|Property|Descripción|Default|  
|--------------|-----------------|-------------|  
|Color de relleno|El color de relleno para el diagrama.|Blanco|  
|Color del texto|El color del texto que se muestra en el diagrama.|Negro|  
|Modificador de acceso|El modificador de acceso de la clase (pública o interna).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código generado.|\<Ninguno >|  
|Genera doble derivada|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|No tiene Constructor personalizado|Si `True`, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir del diagrama (`none`, `abstract` o `sealed`).|Ninguna|  
|Diagrama base|La clase base de este diagrama.|(ninguno)|  
|nombre|El nombre de este diagrama.|Nombre actual|  
|Espacio de nombres|El espacio de nombres que está asociado a este diagrama.|Espacio de nombres actual|  
|Clase representada|La clase de dominio raíz que representa este diagrama.|Clase raíz actual si es aplicable|  
|Notas|Notas informales que están asociadas con este elemento.|\<Ninguno >|  
|Color de relleno expone como propiedad|Si `True`, el usuario puede establecer el color de relleno del diagrama del diseñador generado. Para ello, a la derecha, haga clic en la forma de diagrama y haga clic en **Explosed agregar**.|False|  
|Expone el Color del texto como propiedad|Si `True`, el usuario puede establecer el color del texto del diagrama en el diseñador generado. Para ello, a la derecha, haga clic en la forma de diagrama y haga clic en **Explosed agregar**.|False|  
|Descripción|La descripción que se usa para documentar el diseñador generado.|\<Ninguno >|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para este diagrama.|\<Ninguno >|  
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 para este diagrama.|\<Ninguno >|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de las herramientas de lenguajes específicos de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



