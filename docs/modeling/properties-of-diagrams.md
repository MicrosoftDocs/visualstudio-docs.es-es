---
title: Propiedades de diagramas
description: Obtenga información sobre los diagramas y cómo puede establecer propiedades que especifiquen cómo aparecerán los diagramas en el diseñador generado.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8a060c79866d1746135f8a29aef15ca96dd51f63
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390677"
---
# <a name="properties-of-diagrams"></a>Propiedades de diagramas
Puede establecer propiedades que especifiquen cómo aparecerán los diagramas en el diseñador generado. Por ejemplo, puede especificar un color predeterminado para el texto en el diagrama.

 Para obtener más información, [vea How to define a domain-specific language](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [Personalizar y ampliar un lenguaje específico del dominio.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 En la tabla siguiente se enumeran las propiedades de los diagramas.

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|Color de relleno|Color de relleno del diagrama.|Blanco|
|Color del texto|Color del texto que se muestra en el diagrama.|Negro|
|Modificador de acceso|Modificador de acceso de la clase (pública o interna).|Público|
|Atributos personalizados|Se usa para agregar atributos a la clase de código generada.|\<none>|
|Genera una doble derivada|Si es , se generarán una clase base y una clase parcial (para admitir la personalización mediante `True` invalidaciones). Para obtener más información, vea [Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|False|
|Tiene un constructor personalizado|Si `True` es , se proporciona un constructor personalizado en el código fuente. Para obtener más información, vea [Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|False|
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir del diagrama ( `none` `abstract` , o `sealed` ).|Ninguno|
|Diagrama base|Clase base de este diagrama.|(ninguno)|
|Nombre|Nombre de este diagrama.|Nombre actual|
|Espacio de nombres|Espacio de nombres que está asociado a este diagrama.|Espacio de nombres actual|
|Clase representada|Clase de dominio raíz que representa este diagrama.|Clase raíz actual, si procede|
|Notas|Notas informales asociadas a este elemento.|\<none>|
|Expone el color de relleno como propiedad|Si `True` es , el usuario puede establecer el color de relleno del diagrama del diseñador generado. Para establecer esta propiedad, haga clic con el botón derecho en la forma del diagrama y haga clic **en Agregar expuesto.**|False|
|Expone el color del texto como propiedad|Si `True` es , el usuario puede establecer el color del texto del diagrama en el diseñador generado. Para establecer esta propiedad, haga clic con el botón derecho en la forma del diagrama y haga clic **en Agregar expuesto.**|False|
|Descripción|Descripción que se usa para documentar el diseñador generado.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se mostrará en el diseñador generado para este diagrama.|\<none>|
|Help Keyword|Palabra clave que se usa para indexar la ayuda F1 para este diagrama.|\<none>|

## <a name="see-also"></a>Vea también

[Glosario de herramientas de lenguaje específico del dominio](/previous-versions/bb126564(v=vs.100))