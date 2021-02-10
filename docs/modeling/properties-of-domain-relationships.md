---
title: Propiedades de las relaciones de dominio
description: Obtenga información sobre las propiedades que están asociadas a un relationshop de dominio, como el modificador de acceso, los atributos personalizados y genera Double derived.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6fb50018dccbe03512c8ab6e5f07c17dbcee307d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941338"
---
# <a name="properties-of-domain-relationships"></a>Propiedades de las relaciones de dominio
Las propiedades de la tabla siguiente están asociadas a una relación de dominio. Para obtener información sobre las relaciones de dominio, vea Descripción de los [modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|Modificador de acceso|El nivel de acceso de la relación de dominio ( `public` o `internal` ).|`public`|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código fuente que se genera a partir de la relación de dominio.|\<none>|
|Genera Double derived|Si `True` es, se genera una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Tiene un constructor personalizado|Si `True` es, indica que se proporciona un constructor personalizado en el código fuente. Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Inheritance (modificador)|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la relación de dominio ( `none` `abstract` o `sealed` ).|\<none>|
|Permite duplicados|Si `True` es, se pueden crear vínculos duplicados de la relación de dominio entre los mismos dos elementos.|`False`|
|Relaciones base|Si se deriva la relación de dominio, la relación base de la relación de dominio.|\<none>|
|Se está incrustando|Si `True` es, la relación de dominio es una relación de incrustación. Si `False` es, la relación es una relación de referencia.|\<both>|
|Nombre|Nombre de la relación de dominio.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está afiliado a la relación de dominio.|Espacio de nombres actual|
|Notas|Notas informales asociadas a la relación de dominio.|\<none>|
|Descripción|La descripción que se usa para documentar el código y se usa en la interfaz de usuario del diseñador generado.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se muestra en el diseñador generado para la relación de dominio.|\<none>|
|Help Keyword|Palabra clave opcional que se usa para indizar la ayuda de F1 para la relación de dominio.|\<none>|

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))