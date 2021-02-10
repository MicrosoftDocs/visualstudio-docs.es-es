---
title: Cambio de oleadas
description: Aprenda a habilitar o deshabilitar características en MSBuild que pueden ser perjudiciales.
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 77f93b4741ee987bac871e619ccbe58e2d4d4000
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939531"
---
# <a name="change-waves"></a>Cambio de oleadas

Una *oleada de cambios* es un conjunto de cambios de comportamiento en MSBuild que puede optar por no recibir especificando una marca concreta como variable de entorno. La finalidad de ello es avisarle de cambios potencialmente perjudiciales para que disponga de la flexibilidad de adaptarse a estos antes de que se conviertan en una funcionalidad estándar. Todas las características de una oleada de cambios concreta solo se pueden habilitar o deshabilitar juntas, no de forma individual.

Al actualizar a una nueva versión de MSBuild, se permiten de forma predeterminada cambios que son potencialmente problemáticos, pero si una característica afecta de forma negativa a la compilación, puede deshabilitar fácilmente esa oleada de cambios. Cada oleada de cambios se identifica mediante un número de versión de MSBuild (por ejemplo, 16.8), pero el establecimiento de la oleada de cambios solo controla determinadas características que pueden afectar al proceso de compilación, no todos los cambios de esa versión de MSBuild. [Más adelante en este artículo](#change-waves-and-associated-features) se muestra una lista de las características de cada oleada de cambios. Al deshabilitar una oleada de cambios, también se deshabilitan las oleadas de cambios de versiones superiores.

## <a name="opt-out-of-change-wave-features"></a>Optar por no recibir las características de una oleada de cambios

Para deshabilitar las características de una oleada de cambios, establezca la variable de entorno `MSBuildDisableFeaturesFromVersion` en la oleada de cambios (o versión de MSBuild) que contiene la característica que quiere que se **deshabilite**. Esta es la versión de MSBuild para la que se desarrollaron las características. Consulte la asignación de oleadas de cambios a las características siguientes.

### <a name="msbuilddisablefeaturesfromversion-values"></a>Valores de MSBuildDisableFeaturesFromVersion

Si no establece `MSBuildDisableFeaturesFromVersion` en una oleada de cambios válida, recibirá una advertencia o se establecerá de forma predeterminada una oleada concreta. En la tabla siguiente se muestran los posibles valores:

| Valor de `MSBuildDisableFeaturesFromVersion`                         | Resultado        | ¿Recibir advertencia? |
| :-------------                                                    | :----------   | :----------: |
| Anular                                                             | Se habilitan todas las oleadas de cambios, lo que significa que todas las características que hay detrás de cada oleada de cambios están habilitadas.               | No   |
| Cualquier oleada de cambios válida y actual (por ejemplo, `16.8`)                      | Se deshabilitan todas las características que hay detrás de una oleada de cambios `16.8` **y posteriores**.                                           | No   |
| Valor no válido (por ejemplo, `16.9` cuando las oleadas válidas son `16.8` y `16.10`)| Toma de forma predeterminada el valor válido más cercano (ascendente). Por ejemplo, al establecer `16.9`, se toma como predeterminado `16.10`.               | No   |
| Fuera de rotación (por ejemplo, `17.1` cuando la oleada más alta es la `17.0`)      | Se fija en el valor válido más cercano. Por ejemplo, `17.1` se fija en `17.0` y `16.5` en `16.8`.                    | Sí  |
| Formato no válido (por ejemplo, `16x8`, `17_0`, `garbage`)                    | Se habilitan todas las oleadas de cambios, lo que significa que todas las características que hay detrás de cada oleada de cambios están habilitadas.               | Sí  |

## <a name="change-waves-and-associated-features"></a>Oleadas de cambios y características asociadas

Los vínculos de la lista siguiente llevan a la solicitud de incorporación de cambios de GitHub correspondiente a la característica.

### <a name="168"></a>16.8

- [Habilitación de NoWarn](https://github.com/dotnet/msbuild/pull/5671)
- [Truncamiento de los mensajes de registro omitidos de destino/tarea a 1024 caracteres](https://github.com/dotnet/msbuild/pull/5553)
- [No expandir los globs de unidad completa con una condición falsa](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16.10

- [Error cuando la expansión de una propiedad en una condición tiene un espacio en blanco](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17.0

Todavía no hay entradas en esta oleada de cambios.

## <a name="change-waves-that-are-out-of-rotation"></a>Oleadas de cambios que están fuera de rotación

No hay oleadas de cambios fuera de rotación en este momento.

## <a name="faq"></a>Preguntas más frecuentes

**¿Por qué se dejan fuera de la rotación las demás versiones de las oleadas de cambios?**

Creemos que hay que dar tiempo suficiente para entablar conversaciones con los afectados y ayudarles a adaptarse a los cambios.

**¿Por qué una variable de entorno y no una propiedad de proyecto?**

Hay escenarios en los que queremos colocar una característica en una oleada de cambios antes de que MSBuild haya cargado el proyecto. Por ese motivo, las oleadas de cambios requieren el uso de variables de entorno.

**¿Por qué es mejor optar por no recibir que optar por recibir?**

Para nosotros es mejor optar por no recibir, si no, es probable que recibamos información limitada cuando una característica afecte a las compilaciones de un cliente.

## <a name="see-also"></a>Vea también

- [MSBuild](msbuild.md)
- [Novedades de MSBuild 16](whats-new-msbuild-16-0.md)
