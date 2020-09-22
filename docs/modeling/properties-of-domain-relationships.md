---
title: Propiedades de las relaciones de dominio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e432e9738009c84b6930b0363ae4048c925d0a6
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810007"
---
# <a name="properties-of-domain-relationships"></a>Propiedades de las relaciones de dominio
Las propiedades de la tabla siguiente están asociadas a una relación de dominio. Para obtener información sobre las relaciones de dominio, vea Descripción de los [modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propiedad.|Descripción|Default|
|-|-|-|
|Modificador de acceso|El nivel de acceso de la relación de dominio ( `public` o `internal` ).|`public`|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código fuente que se genera a partir de la relación de dominio.|\<none>|
|Genera Double derived|Si `True` es, se genera una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Tiene un constructor personalizado|Si `True` es, indica que se proporciona un constructor personalizado en el código fuente. Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Inheritance (modificador)|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la relación de dominio ( `none` `abstract` o `sealed` ).|\<none>|
|Permite duplicados|Si `True` es, se pueden crear vínculos duplicados de la relación de dominio entre los mismos dos elementos.|`False`|
|Relaciones base|Si se deriva la relación de dominio, la relación base de la relación de dominio.|\<none>|
|Se está incrustando|Si `True` es, la relación de dominio es una relación de incrustación. Si `False` es, la relación es una relación de referencia.|\<both>|
|NOMBRE|Nombre de la relación de dominio.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está afiliado a la relación de dominio.|Espacio de nombres actual|
|Notas|Notas informales asociadas a la relación de dominio.|\<none>|
|Descripción|La descripción que se usa para documentar el código y se usa en la interfaz de usuario del diseñador generado.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se muestra en el diseñador generado para la relación de dominio.|\<none>|
|Help Keyword|Palabra clave opcional que se usa para indizar la ayuda de F1 para la relación de dominio.|\<none>|

## <a name="see-also"></a>Consulte también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))