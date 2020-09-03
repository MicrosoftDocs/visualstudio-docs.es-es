---
title: Propiedades de las relaciones de dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95372b2bc7537e017a4eeca9b414ef054d82046d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671539"
---
# <a name="properties-of-domain-relationships"></a>Propiedades de las relaciones de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las propiedades de la tabla siguiente están asociadas a una relación de dominio. Para obtener información sobre las relaciones de dominio, vea Descripción de los [modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propiedad|Descripción|Valor predeterminado|
|--------------|-----------------|-------------|
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

## <a name="see-also"></a>Consulte también
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
