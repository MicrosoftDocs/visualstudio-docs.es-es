---
title: Propiedades de los decoradores
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3374c07cac01104354b2ce41abddbeabbec0a373
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566142"
---
# <a name="properties-of-decorators"></a>Propiedades de los decoradores
Los elementos Decorator son iconos, texto o cheurones de expansión/contracción que pueden aparecer en formas o conectores en el diagrama. En las tablas siguientes se muestran las propiedades de los tres tipos de Decorator. Algunas de las propiedades solo aparecen en los decoradores de forma o solo en los elementos Decorator del conector.

 Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y extender un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Expandir o contraer Decorator

|La propiedad|Descripción|Predeterminado|
|-|-|-|
|DisplayName|Nombre del elemento Decorator que se mostrará en el diseñador generado.|Expandir decorador de contracción|
|Name|Nombre del elemento Decorator.|ExpandCollapseDecorator|
|Notas|Notas informales asociadas a este elemento Decorator.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, en pulgadas, relativo a la posición predeterminada del elemento Decorator. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, relativo a la posición predeterminada del elemento Decorator, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del elemento Decorator desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del elemento Decorator a partir de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del elemento Decorator.|SourceTop|

## <a name="icon-decorator"></a>Icono Decorator

|La propiedad|Descripción|Predeterminado|
|-|-|-|
|DefaultIcon|Ruta de acceso del archivo de icono o imagen que se va a mostrar.|\<none>|
|DisplayName|Nombre del elemento Decorator que se va a mostrar en el diseñador generado.|Icono Decorator|
|Name|Nombre del elemento Decorator.|IconDecorator|
|Notas|Notas informales asociadas al elemento Decorator.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, en pulgadas, relativo a la posición predeterminada del elemento Decorator. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, relativo a la posición predeterminada del elemento Decorator, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del elemento Decorator desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del elemento Decorator a partir de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del elemento Decorator.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|La propiedad|Descripción|Predeterminado|
|-|-|-|
|DefaultText|Texto predeterminado que se va a mostrar.|Etiqueta|
|DisplayName|Nombre del elemento Decorator que se va a mostrar en el diseñador generado.|Etiqueta|
|FontSize|Tamaño de fuente para el texto que se muestra en el elemento Decorator.|8|
|FontStyle|Estilo de fuente para el texto que se muestra en el elemento Decorator.|Regular|
|Name|Nombre del elemento Decorator.|Etiqueta|
|Notas|Notas informales asociadas al elemento Decorator.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, en pulgadas, relativo a la posición predeterminada del elemento Decorator. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, relativo a la posición predeterminada del elemento Decorator, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del elemento Decorator desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del elemento Decorator a partir de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del elemento Decorator.|TargetBottom|

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
