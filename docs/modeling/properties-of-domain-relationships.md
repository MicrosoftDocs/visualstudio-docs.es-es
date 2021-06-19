---
title: Propiedades de las relaciones de dominio
description: Obtenga información sobre las propiedades asociadas a una relación de dominioshop, como Modificador de acceso, Atributos personalizados y Genera doble derivado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fc92bbc32a454208f3d455734b7697a2e69037b4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390664"
---
# <a name="properties-of-domain-relationships"></a>Propiedades de las relaciones de dominio
Las propiedades de la tabla siguiente están asociadas a una relación de dominio. Para obtener información sobre las relaciones de dominio, vea [Descripción de modelos, clases y relaciones.](../modeling/understanding-models-classes-and-relationships.md) Para obtener más información sobre cómo usar estas propiedades, vea [Personalizar y extender un Domain-Specific lenguaje .](../modeling/customizing-and-extending-a-domain-specific-language.md)

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|Modificador de acceso|Nivel de acceso de la relación de dominio ( `public` o `internal` ).|`public`|
|Atributos personalizados|Se usa para agregar atributos a la clase de código fuente que se genera a partir de la relación de dominio.|\<none>|
|Genera una doble derivada|Si es , se genera una clase base y una clase parcial (para admitir la personalización mediante `True` invalidaciones). Para obtener más información, [vea Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|`False`|
|Tiene un constructor personalizado|Si es , indica que se proporciona un `True` constructor personalizado en el código fuente. Para obtener más información, [vea Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|`False`|
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la relación de dominio ( `none` , `abstract` o `sealed` ).|\<none>|
|Permite duplicados|Si `True` es , se pueden crear vínculos duplicados de la relación de dominio entre los mismos dos elementos.|`False`|
|Relaciones base|Si se deriva la relación de dominio, la relación base de la relación de dominio.|\<none>|
|Es la inserción|Si `True` es , la relación de dominio es una relación de inserción. Si `False` es , la relación es una relación de referencia.|\<both>|
|Nombre|Nombre de la relación de dominio.|Nombre actual|
|Espacio de nombres|Espacio de nombres que está asociado a la relación de dominio.|Espacio de nombres actual|
|Notas|Notas informales asociadas a la relación de dominio.|\<none>|
|Descripción|Descripción que se usa para documentar el código y que se usa en la interfaz de usuario del diseñador generado.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se muestra en el diseñador generado para la relación de dominio.|\<none>|
|Help Keyword|Palabra clave opcional que se usa para indexar la ayuda F1 para la relación de dominio.|\<none>|

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))