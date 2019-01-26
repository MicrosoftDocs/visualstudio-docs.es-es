---
title: Propiedades de las relaciones de dominio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: f4922bf82b343b6756e64e658bb36be22170f786
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985479"
---
# <a name="properties-of-domain-relationships"></a>Propiedades de las relaciones de dominio
Las propiedades en la tabla siguiente se asocian con una relación de dominio. Para obtener información acerca de las relaciones de dominio, consulte [descripción de los modelos, las clases y relaciones](../modeling/understanding-models-classes-and-relationships.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Property|Descripción|Default|
|-|-|-|
|Modificador de acceso|El nivel de acceso de la relación de dominio (`public` o `internal`).|`public`|
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código fuente que se genera a partir de la relación de dominio.|\<none>|
|Genera doble derivada|Si `True`, se genera una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|No tiene Constructor personalizado|Si `True`, indica que se proporciona un constructor personalizado en el código fuente. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificador de herencia|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la relación de dominio (`none`, `abstract` o `sealed`).|\<none>|
|Permite duplicados|Si `True`, se pueden crear vínculos duplicados de la relación de dominio entre dos mismos elementos.|`False`|
|Relaciones bases|Si se deriva la relación de dominio, la relación base de la relación de dominio.|\<none>|
|Incrustación de se|Si `True`, la relación de dominio es una relación de incrustación. Si `False`, la relación es una relación de referencia.|\<both>|
|nombre|El nombre de la relación de dominio.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está asociado a la relación de dominio.|Espacio de nombres actual|
|Notas|Notas informales que están asociadas con la relación de dominio.|\<none>|
|Descripción|La descripción que se usa para documentar código y se usa en la interfaz de usuario del diseñador generado.|\<none>|
|Nombre para mostrar|El nombre que se muestra en el diseñador generado para la relación de dominio.|\<none>|
|Help Keyword|La palabra clave opcional que se utiliza para indizar la Ayuda F1 para la relación de dominio.|\<none>|

## <a name="see-also"></a>Vea también

- [Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)