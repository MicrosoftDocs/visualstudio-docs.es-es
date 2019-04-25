---
title: Novedades de diseño en Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: fb7ef710d117318d475e32f19b5ca2511b94f8bc
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869894"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novedades de diseño en Visual Studio 2017

## <a name="live-dependency-validation"></a>Validación de dependencias en vivo

Quitar las dependencias no deseadas es una parte importante de la administración de su deuda técnica. Validación en vivo de las dependencias es ahora se incluyen, que proporciona información precisa sobre problemas y beneficiarse totalmente de las nuevas características en la lista de errores y el editor.

![Validación de dependencias en vivo en acción](media/dep-validation-whatsnew-01.png)

Ha cambiado la experiencia de creación para realizar la validación de dependencias que sean más reconocibles y sea más accesible cambiando la terminología de "Diagrama de capas" a "Diagrama de dependencia".

El **arquitectura** menú ahora contiene un comando para crear directamente un diagrama de dependencia:

![Elemento activo de dependencias en el menú de arquitectura](media/dep-validation-whatsnew-02.png)

... y han cambiado los nombres de propiedad de una capa en un diagrama de dependencias y sus descripciones, para que tuvieran más sentido:

![Nombres de propiedad de dependencia en vivo actualizado](media/dep-validation-whatsnew-03.png)

Ahora verá el impacto de los cambios inmediatamente en los resultados del análisis para el código de la solución actual cada vez que guarde el diagrama. No tienes que esperar más para la finalización del comando "Validar dependencias".

Para obtener más información, consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Se han quitado los diseñadores UML

Los diseñadores de UML se quitaron de esta versión de Visual Studio Enterprise.

* Diagramas de UML ahora aparecen como archivos XML
* El Explorador de modelos UML ya no existe
* Las referencias ya no se usan para la validación de dependencia de proyecto de modelado
* Ya no se muestra el nodo "Capa referencias" en el Explorador de soluciones
* Ya no se usa la acción de compilación "Validar" en un diagrama de dependencia (nivel): se ha quitado la tarea de compilación
* Se mantiene la estructura del proyecto de ida y vuelta entre versiones
* Todavía puede abrir, crear, editar y guardar un diagrama de dependencia (capa) como XML
* Elementos de trabajo TFS vinculados a un diagrama de dependencia (capa) no son accesibles en la superficie de diseño
* Ya no se admite la vinculación atrás de DSL o una capa
* Ya no se admite la extensibilidad UML en el SDK de modelado

Sin embargo, se admiten para visualizar la arquitectura de código .NET y C++ está disponible a través de [mapas de código](map-dependencies-across-your-solutions.md)y las mejoras importantes a la validación de dependencia se ha descrito anteriormente.

Si es un usuario significativa de los diseñadores de UML, aún puede usar Visual Studio 2015 o versiones anteriores, mientras se decide por una herramienta alternativa para sus necesidades UML.

Para obtener más información, consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Compatibilidad con la edición de arquitectura y modelado de herramientas

Visual Studio está disponible en varias ediciones. No todas estas proporcionan compatibilidad con la arquitectura y las herramientas de modelado. En la tabla siguiente se muestra la disponibilidad de cada herramienta.

|**Característica**|**Edición Enterprise**|**Professional edition**|**Edición de comunidad**|
|-|-|-|-|
|**Mapas de código**|Sí|Solo se admite la lectura de mapas de código, filtrado de código asigna, agregar nuevos nodos genéricos y crear un nuevo gráfico dirigido a partir de una selección.|-|
|**Diagramas de dependencia**|Sí|Solo admite la lectura de diagramas de dependencia.|Solo admite la lectura de diagramas de dependencia.|
|**Gráficos dirigidos** (diagramas DGML)|Sí|Sí|Sí|
|**Clon de código**|Sí|-|-|