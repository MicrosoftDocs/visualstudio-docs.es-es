---
title: Propiedades de los decoradores
description: Obtenga información sobre que los elementos decorator son iconos, texto o elementos de contenido adicional de expansión o contraer que pueden aparecer en formas o conectores en el diagrama.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f3436bb800142e7c85594f4b05cef6fb45c4489
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390807"
---
# <a name="properties-of-decorators"></a>Propiedades de los decoradores
Los elementos decorator son iconos, texto o elementos de contenido adicional de expansión o conexiones que pueden aparecer en formas o conectores en el diagrama. En las tablas siguientes se muestran las propiedades de los tres tipos de decorador. Algunas de las propiedades solo aparecen en los decoradores de formas o solo en los decoradores del conector.

 Para obtener más información, [vea How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [Personalizar y extender un Domain-Specific lenguaje .](../modeling/customizing-and-extending-a-domain-specific-language.md)

## <a name="expandcollapse-decorator"></a>Expandir o contraer decorator

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|DisplayName|Nombre del decorador que se mostrará en el diseñador generado.|Expandir Decorator de contraer|
|Nombre|Nombre del decorador.|ExpandCollapseDecorator|
|Notas|Notas informales asociadas a este decorador.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, con respecto a la posición predeterminada del decorador, en pulgadas. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, con respecto a la posición predeterminada del decorador, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del decorador desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del decorador de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del decorador.|SourceTop|

## <a name="icon-decorator"></a>Icono Decorator

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|DefaultIcon|Ruta de acceso del icono o archivo de imagen que se va a mostrar.|\<none>|
|DisplayName|Nombre del decorador que se va a mostrar en el diseñador generado.|Icono Decorator|
|Nombre|Nombre del decorador.|IconDecorator|
|Notas|Notas informales asociadas al decorador.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, con respecto a la posición predeterminada del decorador, en pulgadas. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, con respecto a la posición predeterminada del decorador, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del decorador desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del decorador de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del decorador.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Propiedad|Descripción|Valor predeterminado|
|-|-|-|
|DefaultText|Texto predeterminado que se va a mostrar.|Etiqueta|
|DisplayName|Nombre del decorador que se va a mostrar en el diseñador generado.|Etiqueta|
|FontSize|Tamaño de fuente del texto que se muestra en el decorador.|8|
|FontStyle|Estilo de fuente del texto que se muestra en el decorador.|Normal|
|Nombre|Nombre del decorador.|Etiqueta|
|Notas|Notas informales asociadas al decorador.|\<none>|
|HorizontalOffset|Desplazamiento horizontal, con respecto a la posición predeterminada del decorador, en pulgadas. (Solo en formas).|0|
|VerticalOffset|Desplazamiento vertical, con respecto a la posición predeterminada del decorador, en pulgadas. (Solo en formas).|0|
|OffsetFromLine|Desplazamiento del decorador desde la línea, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|OffsetFromShape|Desplazamiento del decorador de la forma, con respecto a su posición predeterminada, en pulgadas. (Solo en conectores).|0|
|Posición|Posición predeterminada del decorador.|TargetBottom|

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))