---
title: Propiedades de los diagramas
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 39e3cc044913a592d5f49e685d8075cd43803e55
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966484"
---
# <a name="properties-of-diagrams"></a>Propiedades de los diagramas
Puede establecer las propiedades que especifican cómo aparecerán los diagramas del diseñador generado. Por ejemplo, puede especificar un color predeterminado para el texto en el diagrama.

 Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 En la tabla siguiente se enumera las propiedades de los diagramas.

|Property|Descripción|Default|
|-|-|-|
|Color de relleno|El color de relleno para el diagrama.|Blanco|
|Color del texto|El color del texto que se muestra en el diagrama.|Negro|
|Modificador de acceso|El modificador de acceso de la clase (pública o interna).|Public|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código generado.|\<Ninguno >|
|Genera doble derivada|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|No tiene Constructor personalizado|Si `True`, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md)...|False|
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir del diagrama (`none`, `abstract`, o `sealed`).|Ninguna|
|Diagrama base|La clase base de este diagrama.|(ninguno)|
|nombre|El nombre de este diagrama.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está asociado a este diagrama.|Espacio de nombres actual|
|Clase representada|La clase de dominio raíz que representa este diagrama.|Clase raíz actual si es aplicable|
|Notas|Notas informales que están asociadas con este elemento.|\<Ninguno >|
|Color de relleno expone como propiedad|Si `True`, el usuario puede establecer el color de relleno del diagrama del diseñador generado. Para establecer esta propiedad, haga clic en la forma de diagrama y haga clic en **agregar expuestos**.|False|
|Expone el Color del texto como propiedad|Si `True`, el usuario puede establecer el color del texto del diagrama en el diseñador generado. Para establecer esta propiedad, haga clic en la forma de diagrama y haga clic en **agregar expuestos**.|False|
|Descripción|La descripción que se usa para documentar el diseñador generado.|\<Ninguno >|
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para este diagrama.|\<Ninguno >|
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 para este diagrama.|\<Ninguno >|

## <a name="see-also"></a>Vea también

[Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
