---
title: "Linting de código de R con Herramientas de R para Visual Studio | Microsoft Docs"
description: "Describe cómo trabajar con la compatibilidad con linting integrado en Visual Studio para R, incluidas las opciones de detección de errores correspondientes."
ms.custom: 
ms.date: 01/15/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 30f508fbaa6de816f8b0adb336fea66b82f992a6
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="linting-r-code-in-visual-studio"></a>Linting de código de R en Visual Studio

Linting es un proceso que analiza el código para mostrar posibles errores, problemas de formato y otros ruidos en el código (por ejemplo, espacio en blanco falso). El linting también ayuda a promover ciertas convenciones de codificación (por ejemplo, cómo se denominan los identificadores) lo que es muy útil en equipos y otras situaciones de colaboración.

Las herramientas de R para Visual Studio (RTVS) proporcionan linting integrado para R, cuyo comportamiento se controla a través de una serie de opciones descritas en este artículo. Estas opciones se encuentran en **Herramientas > Opciones > Editor de texto > R > Lint**.

El linting está deshabilitado de manera predeterminada. Para habilitar el linting, establezca la opción **Todos > Habilitar lint** en true.

Cuando se habilita, el linting se aplica en el editor mientras se escribe. Los problemas aparecen como líneas onduladas de color verde. En el gráfico siguiente, por ejemplo, RTVS ha identificado seis problemas de linting, incluido el uso de `=` en lugar de `<-` para una asignación, la falta de espacio alrededor de los argumentos de función, el uso de identificadores en Pascal Case y mayúsculas, y el uso de punto y coma. Al mantener el puntero sobre un problema, se proporciona una descripción.

![Ejemplos de linting para código de R](media/linting-01.png)

Las opciones de linting se cambian a menudo en función de las necesidades de un archivo o proyecto. El código de ejemplo de un curso en línea podría utilizar `=` en lugar de `<-` junto con identificadores en mayúsculas y minúsculas (Pascal). Este código muestra advertencias de linting frecuentes porque las opciones predeterminadas de linting marcan estos casos. Así pues, mientras trabaja con ese código puede deshabilitar simplemente las opciones en lugar de dedicar tiempo a la corrección de cada instancia.

## <a name="assignment-group"></a>Grupo de asignación

| Opción | Valor predeterminado | Efecto del linting |
| --- | --- | --- |
| Exigir \<- | `True` | Identifica cuándo no se usa `<-` para la asignación. |

## <a name="naming-group"></a>Grupo de nomenclatura

Estas opciones marcan los identificadores que usan convenciones de nomenclatura diferentes:

| Opción | Valor predeterminado | Efecto del linting |
| --- | --- | --- |
| Marcar camelCase | `False` | Marca los identificadores que usan camelCase. |
| Marcar nombres largos | `False` | Marca los identificadores cuyo nombre supera el valor "Longitud de nombre máxima". |
| Marcar varios puntos | `True` | Marca los identificadores que usan varios puntos. |
| Marcar PascalCase | `True` | Marca los identificadores que usan PascalCase. |
| Marcar snake_case | `False` | Marca los identificadores que usan caracteres de subrayado. |
| Marcar mayúsculas | `True` | Marca los identificadores que usan todo mayúsculas. |
| Longitud máxima de nombre | 32 | La longitud que se aplica con el valor "Marcar nombres largos". |

## <a name="spacing-group"></a>Grupo de espaciado

Estas opciones, que todas se establecen en `True` de forma predeterminada, controlan dónde identifica el linter los problemas de espaciado: después de los nombres de función, alrededor de comas y operadores, posiciones de llaves de apertura y cierre, espacio antes de ( y espacio dentro de ().

## <a name="statements-group"></a>Grupo de instrucciones

| Opción | Valor predeterminado | Efecto del linting |
| --- | --- | --- |
| Múltiple | `True` | Identifica cuándo hay varias instrucciones en la misma línea. |
| Puntos y coma | `True` | Identifica los usos de puntos y coma. |

## <a name="text-group"></a>Grupo de texto

| Opción | Valor predeterminado | Efecto del linting |
| --- | --- | --- |
| Límite de longitud de línea | `False` | Establece si el linter marcas líneas más largas que la opción "Longitud máxima de línea". |
| Longitud máxima de línea | 80 | Establece la longitud de línea que se aplica con la opción "Límite de longitud de línea". |

## <a name="whitespace-group"></a>Grupo de espacio en blanco

Estas opciones, que todas se establecen en `True` de forma predeterminada, controlan dónde identifica el linter los problemas de espacio en blanco: uso de tabulaciones, uso de comillas dobles, líneas vacías al final y espacios en blanco al final.