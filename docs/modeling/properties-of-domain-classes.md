---
title: Propiedades de las clases de dominio
description: Obtenga información sobre las distintas propiedades de las clases de dominio, como Modificador de acceso, Atributos personalizados y Genera doble derivada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eaaae0028d574a521319ae045cdb4f7f1bdafaa2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390013"
---
# <a name="properties-of-domain-classes"></a>Propiedades de las clases de dominio
Las clases de dominio tienen las propiedades de la tabla siguiente. Para obtener información sobre las clases de dominio, vea [Descripción de modelos, clases y relaciones.](../modeling/understanding-models-classes-and-relationships.md) Para obtener más información sobre cómo usar estas propiedades, vea [Personalizar y extender un Domain-Specific language](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|Modificador de acceso|Nivel de acceso de la clase de dominio (`public` o `internal`).|`public`|
|Atributos personalizados|Se usa para agregar atributos a la clase de código fuente que se genera a partir de esta clase de dominio.|\<none>|
|Genera una doble derivada|Si es , se generarán una clase base y una clase parcial (para admitir la personalización mediante `True` invalidaciones). Para obtener más información, [vea Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|`False`|
|Tiene un constructor personalizado|Si `True` es , se proporciona un constructor personalizado en el código fuente. Para obtener más información, [vea Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)|`False`|
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la clase de dominio ( `none` , `abstract` o `sealed` ).|`none`|
|Clase base|Si se deriva esta clase de dominio, el nombre de la clase base.|\<none>|
|Nombre|Nombre de esta clase de dominio.|Nombre actual|
|Espacio de nombres|Espacio de nombres de esta clase de dominio.|Espacio de nombres actual|
|Notas|Notas informales asociadas a esta clase de dominio.|\<none>|
|Descripción|Descripción que se usa para documentar la interfaz de usuario del diseñador generado.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se mostrará en el diseñador generado para esta clase de dominio.|\<none>|
|Help Keyword|Palabra clave opcional que se usa para indexar la ayuda F1 para esta clase de dominio.|\<none>|

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))