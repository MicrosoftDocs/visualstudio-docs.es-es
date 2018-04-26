---
title: Propiedades de los diagramas
ms.date: 11/04/2016
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
ms.openlocfilehash: f66c4597116c2dd27320a8ae0bf69314bbb558b4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="properties-of-diagrams"></a>Propiedades de los diagramas
Puede establecer propiedades que especifican cómo los diagramas aparecerá en el diseñador generado. Por ejemplo, puede especificar un color predeterminado para el texto en el diagrama.

 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información acerca de cómo utilizar estas propiedades, vea [personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 En la tabla siguiente se enumera las propiedades de diagramas.

|Property|Descripción|Default|
|--------------|-----------------|-------------|
|Color de relleno|El color de relleno para el diagrama.|Blanco|
|Color del texto|El color del texto que se muestra en el diagrama.|Negro|
|Modificador de acceso|El modificador de acceso de la clase (pública o interna).|Public|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código generado.|\<Ninguno >|
|Genera doble derivadas|Si `True`, se generará una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Tiene un Constructor personalizado|Si `True`, se proporciona un constructor personalizado en el código fuente. Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md)...|False|
|Modificador de herencia|Describe el tipo de herencia de la clase de código de origen que se genera a partir del diagrama (`none`, `abstract` o `sealed`).|Ninguna|
|Diagrama de base|La clase base de este diagrama.|(ninguno)|
|nombre|El nombre de este diagrama.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está afiliado a este diagrama.|Espacio de nombres actual|
|Clase que representa|La clase de dominio raíz que representa este diagrama.|Clase raíz actual si es aplicable|
|Notas|Notas informales que están asociadas a este elemento.|\<Ninguno >|
|Expone el Color de relleno como propiedad|Si `True`, el usuario puede establecer el color de relleno del diagrama del diseñador generado. Para definir esta opción, haga clic en la forma de diagrama y haga clic en **Explosed agregar**.|False|
|Expone el Color del texto como propiedad|Si `True`, el usuario puede establecer el color del texto del diagrama en el diseñador generado. Para definir esta opción, haga clic en la forma de diagrama y haga clic en **Explosed agregar**.|False|
|Descripción|La descripción que se utiliza para documentar el diseñador generado.|\<Ninguno >|
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para este diagrama.|\<Ninguno >|
|Help Keyword|La palabra clave que se utiliza para indizar la Ayuda F1 de este diagrama.|\<Ninguno >|

## <a name="see-also"></a>Vea también

- [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)