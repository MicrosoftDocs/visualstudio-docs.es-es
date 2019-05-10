---
title: Novedades de diseño en Visual Studio 2017
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
ms.openlocfilehash: dc75c7414e0fff18f76d14f8f9a4e0779a9e7a2b
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476538"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novedades de diseño en Visual Studio 2017

## <a name="live-dependency-validation"></a>Validación de dependencias en vivo

Quitar las dependencias no deseadas es una parte importante de la administración de su deuda técnica. Visual Studio proporciona la validación en vivo de las dependencias, incluidas información precisa acerca de temas, como dónde se encuentran. Activo de dependencias validación toma todas las ventajas de las nuevas características de la lista de errores y el editor.

![Validación de dependencias en vivo en acción](media/dep-validation-whatsnew-01.png)

Ha cambiado la experiencia de creación para realizar la validación de dependencias sean más reconocibles y sea más accesible. La terminología ha cambiado de "Diagrama de capas" a "Diagrama de dependencia".

El **arquitectura** menú ahora contiene un comando para crear directamente un diagrama de dependencia:

![Elemento activo de dependencias en el menú de arquitectura](media/dep-validation-whatsnew-02.png)

Se han cambiado los nombres de propiedad de capa y descripciones para que tuvieran más sentido:

![Nombres de propiedad de dependencia en vivo actualizado](media/dep-validation-whatsnew-03.png)

Verá inmediatamente el impacto de los cambios en los resultados del análisis para el código de la solución actual cada vez que guarde el diagrama. No tiene que esperar la finalización de la **validar dependencias** comando.

Para obtener más información, consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Se han quitado los diseñadores UML

Se quitaron los diseñadores de UML de Visual Studio.

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

Soporte técnico para visualizar la arquitectura de .NET y C++ código está disponible a través de [mapas de código](map-dependencies-across-your-solutions.md).

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