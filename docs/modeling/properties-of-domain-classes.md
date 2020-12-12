---
title: Propiedades de las clases de dominio
description: Obtenga información sobre las distintas propiedades de las clases de dominio, como el modificador de acceso, los atributos personalizados y la generación de Double derived.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd36973a9c355dcaec32b6da4149e6efd88282da
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360798"
---
# <a name="properties-of-domain-classes"></a>Propiedades de las clases de dominio
Las clases de dominio tienen las propiedades de la tabla siguiente. Para obtener información sobre las clases de dominio, vea Descripción de los [modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propiedad.|Descripción|Default|
|-|-|-|
|Modificador de acceso|Nivel de acceso de la clase de dominio (`public` o `internal`).|`public`|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código fuente que se genera a partir de esta clase de dominio.|\<none>|
|Genera Double derived|Si `True` es, se generarán una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Tiene un constructor personalizado|Si `True` es, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Inheritance (modificador)|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la clase de dominio ( `none` , `abstract` o `sealed` ).|`none`|
|Clase base|Si se deriva esta clase de dominio, el nombre de la clase base.|\<none>|
|Nombre|Nombre de esta clase de dominio.|Nombre actual|
|Espacio de nombres|Espacio de nombres de esta clase de dominio.|Espacio de nombres actual|
|Notas|Notas informales asociadas a esta clase de dominio.|\<none>|
|Descripción|La descripción que se usa para documentar la interfaz de usuario del diseñador generado.|\<none>|
|Nombre para mostrar|Nombre que se mostrará en el diseñador generado para esta clase de dominio.|\<none>|
|Help Keyword|Palabra clave opcional que se usa para indizar la ayuda de F1 para esta clase de dominio.|\<none>|

## <a name="see-also"></a>Consulta también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))