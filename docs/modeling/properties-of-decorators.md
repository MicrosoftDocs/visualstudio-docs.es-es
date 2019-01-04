---
title: Propiedades de los decoradores
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: fc0f6e3fe8078675792109c41ee75272b44ca714
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865367"
---
# <a name="properties-of-decorators"></a>Propiedades de los decoradores
Los elementos Decorator son iconos, texto o expandir o contraer comillas angulares que pueden aparecer en formas o conectores en el diagrama. Las siguientes tablas muestran las propiedades de los tres tipos de elemento decorator. Algunas de las propiedades aparecen sólo en shape elementos Decorator o sólo en los elementos Decorator del conector.

 Para obtener más información, consulte [cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md). Para obtener más información sobre cómo usar estas propiedades, vea [personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Expandir o contraer el elemento Decorator

|Property|Descripción|Default|
|-|-|-|
|DisplayName|El nombre del elemento decorator que se mostrará en el diseñador generado.|Expanda el elemento Decorator de contraer|
|nombre|El nombre del elemento decorator.|ExpandCollapseDecorator|
|Notas|Notas informales que están asociadas con este elemento decorator.|\<Ninguno >|
|HorizontalOffset|El desplazamiento horizontal, en relación con la posición predeterminada del elemento decorator, en pulgadas. (En formas sólo.)|0|
|VerticalOffset|El desplazamiento vertical, en relación con la posición predeterminada del elemento decorator, en pulgadas. (En formas sólo.)|0|
|OffsetFromLine|El desplazamiento del elemento decorator desde la línea, en relación con su posición predeterminada, en pulgadas. (En los conectores solo.)|0|
|OffsetFromShape|El desplazamiento del elemento decorator desde la forma respecto a su posición predeterminada, en pulgadas. (En los conectores solo.)|0|
|Posición|La posición predeterminada del decorador.|SourceTop|

## <a name="icon-decorator"></a>Elemento Decorator de icono

|Property|Descripción|Default|
|-|-|-|
|DefaultIcon|La ruta de acceso del archivo de icono o imagen que se mostrará.|\<Ninguno >|
|DisplayName|El nombre del elemento decorator que se mostrará en el diseñador generado.|Elemento Decorator de icono|
|nombre|El nombre del elemento decorator.|IconDecorator|
|Notas|Notas informales que están asociadas con el elemento decorator.|\<Ninguno >|
|HorizontalOffset|El desplazamiento horizontal, en relación con la posición predeterminada del elemento decorator, en pulgadas. (En formas sólo.)|0|
|VerticalOffset|El desplazamiento vertical, en relación con la posición predeterminada del elemento decorator, en pulgadas. (En formas sólo.)|0|
|OffsetFromLine|El desplazamiento del elemento decorator desde la línea, en relación con su posición predeterminada, en pulgadas. (En los conectores solo.)|0|
|OffsetFromShape|El desplazamiento del elemento decorator desde la forma respecto a su posición predeterminada, en pulgadas. (En los conectores solo.)|0|
|Posición|La posición predeterminada del decorador.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Property|Descripción|Default|
|-|-|-|
|DefaultText|El texto predeterminado que se mostrará.|Etiqueta|
|DisplayName|El nombre del elemento decorator que se mostrará en el diseñador generado.|Etiqueta|
|FontSize|El tamaño de fuente del texto que se muestra en el elemento decorator.|8|
|FontStyle|El estilo de fuente del texto que se muestra en el elemento decorator.|Estándar|
|nombre|El nombre del elemento decorator.|Etiqueta|
|Notas|Notas informales que están asociadas con el elemento decorator.|\<Ninguno >|
|HorizontalOffset|El desplazamiento horizontal, en relación con la posición predeterminada del elemento decorator, en pulgadas. (En formas sólo.)|0|
|VerticalOffset|El desplazamiento vertical, en relación con la posición predeterminada del elemento decorator, en pulgadas. (En formas sólo.)|0|
|OffsetFromLine|El desplazamiento del elemento decorator desde la línea, en relación con su posición predeterminada, en pulgadas. (En los conectores solo.)|0|
|OffsetFromShape|El desplazamiento del elemento decorator desde la forma respecto a su posición predeterminada, en pulgadas. (En los conectores solo.)|0|
|Posición|La posición predeterminada del decorador.|TargetBottom|

## <a name="see-also"></a>Vea también

- [Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)