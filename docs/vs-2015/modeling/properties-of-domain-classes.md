---
title: Propiedades de las clases de dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 91599e17fc132001de9fbb1a62a62918321a2dea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652007"
---
# <a name="properties-of-domain-classes"></a>Propiedades de las clases de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las clases de dominio tienen las propiedades de la tabla siguiente. Para obtener información sobre las clases de dominio, vea Descripción de los [modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propiedad|Descripción|Valor predeterminado|
|--------------|-----------------|-------------|
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
|Display Name (Nombre para mostrar)|Nombre que se mostrará en el diseñador generado para esta clase de dominio.|\<none>|
|Help Keyword|Palabra clave opcional que se usa para indizar la ayuda de F1 para esta clase de dominio.|\<none>|

## <a name="see-also"></a>Consulte también
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
