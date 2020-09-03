---
title: Propiedades de las calles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b76bef291e23bc570534aa79f9471453c59491c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671339"
---
# <a name="properties-of-swimlanes"></a>Propiedades de las calles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede Agregar calles a un diagrama. Las calles dividen un diagrama en áreas verticales u horizontales. Puede definir otras formas para que se muestren en calles. Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Las calles tienen las propiedades que se enumeran en la tabla siguiente.

|Propiedad|Descripción|Valor predeterminado|
|--------------|-----------------|-------------|
|Color de relleno del cuerpo|Color de relleno para el cuerpo de la calle.|Blanco|
|Color de relleno del encabezado|Color de relleno para el encabezado de la calle.|Gris oscuro|
|Color del separador|Color de la línea de separación.|LightGray|
|Estilo de línea de separador|Estilo de la línea del separador ( `Solid` , `Dash` , `Dot` , `DashDot` , `DashDotDot` o `Custom` ).|`Dash`|
|Grosor del separador|Grosor de la línea de separación en pulgadas.|0,03125|
|Color del texto|Color que se usa para los decoradores de texto que están asociados a esta calle.|Negro|
|Modificador de acceso|Nivel de acceso de la clase ( `public` o `internal` ).|Público|
|Atributos personalizados|Se usa para agregar atributos a la clase de código que se genera a partir de esta calle.|\<none>|
|Genera Double derived|Si `True` es, se generarán una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Tiene un constructor personalizado|Si `True` es, se proporcionará un constructor personalizado en el código fuente. Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|Falso|
|Inheritance (modificador)|Describe el tipo de herencia de la clase de código fuente que se genera a partir de la calle ( `none` , `abstract` o `sealed` ).|None|
|Calle base|La clase base de esta calle.|(ninguno)|
|Nombre|El nombre de esta calle.|Nombre actual|
|Espacio de nombres|El espacio de nombres que está afiliado a esta calle.|Espacio de nombres actual|
|Tipo de información sobre herramientas|Cómo se define la información sobre herramientas ( `fixed` , `variable` o `none` ). Si `fixed` es, se usa el valor de la `Fixed Tooltip Text` propiedad; si es `variable` , la información sobre herramientas se define en código personalizado.|\<none>|
|Notas|Notas informales asociadas a esta calle.|\<none>|
|Alignment|Alineación horizontal o vertical.|Vertical|
|Alto inicial|Alto inicial de esta calle, en pulgadas. Solo se aplica a las calles horizontales.|0|
|Ancho inicial|Ancho inicial de esta calle, en pulgadas. Solo se aplica a las calles verticales.|0|
|Expone el color del texto|Si es `True` , el usuario puede establecer el color de una calle en el diseñador generado. Para establecer esto, haga clic con el botón secundario en la forma calle y haga clic en **Agregar expuesto**.|Falso|
|Descripción|Se usa para documentar el diseñador generado.|\<none>|
|Display Name (Nombre para mostrar)|Nombre que se mostrará en el diseñador generado para hacer referencia a esta clase calle.|\<none>|
|Texto de información sobre herramientas corregido|Texto que se usa para una información sobre herramientas fija.|\<none>|
|Help Keyword|Palabra clave que se usa para indizar la ayuda de F1 para esta calle.|\<none>|

## <a name="see-also"></a>Consulte también
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
