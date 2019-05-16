---
title: Propiedades de los diagramas | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7d669d01339b92c64cfe03ccb3ae897a1816aeac
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701758"
---
# <a name="properties-of-diagrams"></a>Propiedades de los diagramas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede establecer las propiedades que especifican cómo aparecerán los diagramas del diseñador generado. Por ejemplo, puede especificar un color predeterminado para el texto en el diagrama.  
  
 Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 En la tabla siguiente se enumera las propiedades de los diagramas.  
  
|Propiedad|Descripción|Default|  
|--------------|-----------------|-------------|  
|Color de relleno|El color de relleno para el diagrama.|Blanco|  
|Color del texto|El color del texto que se muestra en el diagrama.|Negro|  
|Modificador de acceso|El modificador de acceso de la clase (pública o interna).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código generado.|\<none>|  
|Genera doble derivada|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|No tiene Constructor personalizado|Si `True`, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir del diagrama (`none`, `abstract` o `sealed`).|Ninguna|  
|Diagrama base|La clase base de este diagrama.|(ninguno)|  
|Name|El nombre de este diagrama.|Nombre actual|  
|Espacio de nombres|El espacio de nombres que está asociado a este diagrama.|Espacio de nombres actual|  
|Clase representada|La clase de dominio raíz que representa este diagrama.|Clase raíz actual si es aplicable|  
|Notas|Notas informales que están asociadas con este elemento.|\<none>|  
|Color de relleno expone como propiedad|Si `True`, el usuario puede establecer el color de relleno del diagrama del diseñador generado. Para ello, a la derecha, haga clic en la forma de diagrama y haga clic en **Explosed agregar**.|False|  
|Expone el Color del texto como propiedad|Si `True`, el usuario puede establecer el color del texto del diagrama en el diseñador generado. Para ello, a la derecha, haga clic en la forma de diagrama y haga clic en **Explosed agregar**.|False|  
|Descripción|La descripción que se usa para documentar el diseñador generado.|\<none>|  
|Display Name|El nombre que se mostrará en el diseñador generado para este diagrama.|\<none>|  
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 para este diagrama.|\<none>|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
