---
title: Propiedades de los diagramas
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73be8223d661617451d548898164b78a1a1563f0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658228"
---
# <a name="properties-of-diagrams"></a>Propiedades de los diagramas
Puede establecer las propiedades que especifican cómo aparecerán los diagramas en el diseñador generado. Por ejemplo, puede especificar un color predeterminado para el texto del diagrama.

 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 En la tabla siguiente se enumeran las propiedades de los diagramas.

|Propiedad.|Descripción|Predeterminado|
|-|-|-|
|Color de relleno|Color de relleno para el diagrama.|Blanco|
|Color del texto|Color del texto que se muestra en el diagrama.|Negro|
|Modificador de acceso|Modificador de acceso de la clase (pública o interna).|Public|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código generada.|\<none>|
|Genera Double derived|Si `True`, se generarán una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Tiene un constructor personalizado|Si `True`, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Inheritance (modificador)|Describe el tipo de herencia de la clase de código fuente que se genera a partir del diagrama (`none`, `abstract` o `sealed`).|Ninguno|
|Diagrama base|La clase base de este diagrama.|(ninguno)|
|Name|Nombre de este diagrama.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está afiliado a este diagrama.|Espacio de nombres actual|
|Clase representada|La clase de dominio raíz que este diagrama representa.|Clase raíz actual si es aplicable|
|Notas|Notas informales asociadas a este elemento.|\<none>|
|Expone el color de relleno como propiedad|Si `True`, el usuario puede establecer el color de relleno del diagrama del diseñador generado. Para establecer esta propiedad, haga clic con el botón secundario en la forma de diagrama y haga clic en **Agregar exposición**.|False|
|Expone el color del texto como propiedad|Si `True`, el usuario puede establecer el color del texto del diagrama en el diseñador generado. Para establecer esta propiedad, haga clic con el botón secundario en la forma de diagrama y haga clic en **Agregar exposición**.|False|
|Descripción|La descripción que se usa para documentar el diseñador generado.|\<none>|
|Display Name|El nombre que se mostrará en el diseñador generado para este diagrama.|\<none>|
|Help Keyword|Palabra clave que se usa para indizar la ayuda de F1 para este diagrama.|\<none>|

## <a name="see-also"></a>Vea también

[Glosario de herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
