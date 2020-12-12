---
title: Propiedades de los diagramas
description: Obtenga información sobre los diagramas y cómo puede establecer las propiedades que especifican cómo aparecerán los diagramas en el diseñador generado.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe27eb7dcfb8a984fceaee0700e1df44b6de4ef1
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361955"
---
# <a name="properties-of-diagrams"></a>Propiedades de los diagramas
Puede establecer las propiedades que especifican cómo aparecerán los diagramas en el diseñador generado. Por ejemplo, puede especificar un color predeterminado para el texto del diagrama.

 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 En la tabla siguiente se enumeran las propiedades de los diagramas.

|Propiedad.|Descripción|Default|
|-|-|-|
|Color de relleno|Color de relleno para el diagrama.|Blanco|
|Color del texto|Color del texto que se muestra en el diagrama.|Negro|
|Modificador de acceso|Modificador de acceso de la clase (pública o interna).|Público|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código generada.|\<none>|
|Genera Double derived|Si `True` es, se generarán una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Tiene un constructor personalizado|Si `True` es, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Inheritance (modificador)|Describe el tipo de herencia de la clase de código fuente que se genera a partir del diagrama ( `none` , `abstract` o `sealed` ).|Ninguno|
|Diagrama base|La clase base de este diagrama.|(ninguno)|
|Nombre|Nombre de este diagrama.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está afiliado a este diagrama.|Espacio de nombres actual|
|Clase representada|La clase de dominio raíz que este diagrama representa.|Clase raíz actual si es aplicable|
|Notas|Notas informales asociadas a este elemento.|\<none>|
|Expone el color de relleno como propiedad|Si es `True` , el usuario puede establecer el color de relleno del diagrama del diseñador generado. Para establecer esta propiedad, haga clic con el botón secundario en la forma de diagrama y haga clic en **Agregar exposición**.|Falso|
|Expone el color del texto como propiedad|Si es `True` , el usuario puede establecer el color del texto del diagrama en el diseñador generado. Para establecer esta propiedad, haga clic con el botón secundario en la forma de diagrama y haga clic en **Agregar exposición**.|Falso|
|Descripción|La descripción que se usa para documentar el diseñador generado.|\<none>|
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para este diagrama.|\<none>|
|Help Keyword|Palabra clave que se usa para indizar la ayuda de F1 para este diagrama.|\<none>|

## <a name="see-also"></a>Consulta también

[Glosario de herramientas de lenguajes específicos de dominio](/previous-versions/bb126564(v=vs.100))