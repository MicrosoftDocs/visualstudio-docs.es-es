---
title: Propiedades de los decoradores
description: Aprenda que los elementos Decorator son iconos, texto o comillas angulares de expansión o contracción que pueden aparecer en formas o conectores en el diagrama.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef863d0d3dab394c2ca427a27d039c19e5921a51
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360838"
---
# <a name="properties-of-decorators"></a>Propiedades de los decoradores
Los elementos Decorator son iconos, texto o cheurones de expansión/contracción que pueden aparecer en formas o conectores en el diagrama. En las tablas siguientes se muestran las propiedades de los tres tipos de Decorator. Algunas de las propiedades solo aparecen en los decoradores de forma o solo en los elementos Decorator del conector.

 Para obtener más información, consulte [definición de un lenguaje Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Expandir o contraer Decorator

|Propiedad.|Descripción|Default|
|-|-|-|
|DisplayName|Nombre del elemento Decorator que se mostrará en el diseñador generado.|Expandir decorador de contracción|
|Nombre|Nombre del elemento Decorator.|ExpandCollapseDecorator|
|Notas|Notas informales asociadas a este elemento Decorator.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, en pulgadas, relativo a la posición predeterminada del elemento Decorator. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, relativo a la posición predeterminada del elemento Decorator, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del elemento Decorator desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del elemento Decorator a partir de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del elemento Decorator.|SourceTop|

## <a name="icon-decorator"></a>Icono Decorator

|Propiedad.|Descripción|Default|
|-|-|-|
|DefaultIcon|Ruta de acceso del archivo de icono o imagen que se va a mostrar.|\<none>|
|DisplayName|Nombre del elemento Decorator que se va a mostrar en el diseñador generado.|Icono Decorator|
|Nombre|Nombre del elemento Decorator.|IconDecorator|
|Notas|Notas informales asociadas al elemento Decorator.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, en pulgadas, relativo a la posición predeterminada del elemento Decorator. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, relativo a la posición predeterminada del elemento Decorator, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del elemento Decorator desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del elemento Decorator a partir de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del elemento Decorator.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Propiedad.|Descripción|Default|
|-|-|-|
|DefaultText|Texto predeterminado que se va a mostrar.|Etiqueta|
|DisplayName|Nombre del elemento Decorator que se va a mostrar en el diseñador generado.|Etiqueta|
|FontSize|Tamaño de fuente para el texto que se muestra en el elemento Decorator.|8|
|FontStyle|Estilo de fuente para el texto que se muestra en el elemento Decorator.|Normal|
|Nombre|Nombre del elemento Decorator.|Etiqueta|
|Notas|Notas informales asociadas al elemento Decorator.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, en pulgadas, relativo a la posición predeterminada del elemento Decorator. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, relativo a la posición predeterminada del elemento Decorator, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del elemento Decorator desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del elemento Decorator a partir de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del elemento Decorator.|TargetBottom|

## <a name="see-also"></a>Consulta también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))