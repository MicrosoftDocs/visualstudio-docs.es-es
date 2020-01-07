---
title: Novedades de diseño en Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 6f81cc32604abe6d90ac0d263574e97df35c63bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593517"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novedades de diseño en Visual Studio 2017

## <a name="live-dependency-validation"></a>Validación de dependencias en vivo

Quitar las dependencias no deseadas es una parte importante de la administración de su deuda técnica. Visual Studio proporciona la validación en vivo de las dependencias, incluida la información precisa sobre problemas, como dónde se encuentran. La validación de dependencias en vivo aprovecha las nuevas características del Lista de errores y el editor.

![Validación de dependencias en vivo en acción](media/dep-validation-whatsnew-01.png)

La experiencia de creación ha cambiado para que la validación de dependencias sea más reconocible y más accesible. La terminología ha cambiado de "diagrama de capas" a "diagrama de dependencias".

El **arquitectura** menú ahora contiene un comando para crear directamente un diagrama de dependencia:

![Elemento activo de dependencias en el menú de arquitectura](media/dep-validation-whatsnew-02.png)

Los nombres y descripciones de las propiedades de capa se han modificado para que sean más significativos:

![Nombres de propiedad de dependencia en vivo actualizado](media/dep-validation-whatsnew-03.png)

Verá inmediatamente el impacto de los cambios en los resultados del análisis para el código actual de la solución cada vez que guarde el diagrama. No es necesario esperar a que se complete el comando de **validación de dependencias** .

Para obtener más información, consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Se han quitado los diseñadores UML

Los diseñadores de UML se han quitado de Visual Studio.

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

La compatibilidad con la visualización de la arquitectura de C++ .net y el código está disponible a través de [mapas de código](map-dependencies-across-your-solutions.md).

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
