---
title: Novedades de diseño en Visual Studio 2017
description: Obtenga información sobre las nuevas características para el diseño de código, como la validación de dependencias en vivo, que están disponibles en Visual Studio 2017.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: ed67836507d8328a4ba394986564820c6af7308f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388105"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novedades de diseño en Visual Studio 2017

## <a name="live-dependency-validation"></a>Validación de dependencias en directo

La eliminación de dependencias no deseadas es una parte importante de la administración de la deuda técnica. Visual Studio proporciona validación en vivo de las dependencias, incluida información precisa sobre los problemas, como dónde se encuentran. La validación de dependencias en vivo aprovecha todas las ventajas de las nuevas características de la lista de errores y el editor.

![Validación de dependencias en directo en acción](media/dep-validation-whatsnew-01.png)

La experiencia de creación ha cambiado para que la validación de dependencias sea más reconocible y más accesible. La terminología ha cambiado de "Diagrama de capas" a "Diagrama de dependencias".

El **menú** Arquitectura ahora contiene un comando para crear directamente un diagrama de dependencias:

![Elemento de dependencias en directo en el menú Arquitectura](media/dep-validation-whatsnew-02.png)

Se han cambiado los nombres y descripciones de las propiedades de capa para que tengan más sentido:

![Nombres de propiedades actualizadas de dependencias en directo](media/dep-validation-whatsnew-03.png)

Verá inmediatamente el impacto de los cambios en los resultados del análisis para el código actual de la solución cada vez que guarde el diagrama. No tiene que esperar a que finalice el comando **Validar dependencias.**

Consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/) para obtener más información.

## <a name="uml-designers-have-been-removed"></a>Se han quitado los diseñadores UML

Los diseñadores UML se han quitado de Visual Studio.

* Los diagramas UML ahora se presentan como archivos XML
* El Explorador de modelos UML ya no existe
* Las referencias de proyecto de modelado ya no se usan para la validación de dependencias
* El nodo "Referencias de capa" de Explorador de soluciones ya no se muestra
* Ya no se usa la acción de compilación "Validar" en un diagrama de dependencia (capa): se ha quitado la tarea Compilar.
* La estructura del proyecto se mantiene para el viaje de ida y vuelta entre versiones
* Todavía puede abrir, crear, editar y guardar un diagrama de dependencias (capa) como XML.
* Los elementos de trabajo de TFS vinculados a un diagrama de dependencia (capa) no son accesibles en la superficie de diseño
* Ya no se admite la vinculación de back-link desde a DSL o a una capa
* Ya no se admite la extensibilidad UML en el SDK de modelado

La compatibilidad con la visualización de la arquitectura del código de .NET y C++ está disponible a través de [mapas de código](map-dependencies-across-your-solutions.md).

Si es un usuario significativo de los diseñadores UML, puede seguir usando Visual Studio 2015 o versiones anteriores mientras decide una herramienta alternativa para sus necesidades uml.

Consulte [esta entrada de blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/) para obtener más información.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Compatibilidad de edición con herramientas de arquitectura y modelado

Visual Studio está disponible en varias ediciones. No todos estos proporcionan compatibilidad con la arquitectura y las herramientas de modelado. En la tabla siguiente se muestra la disponibilidad de cada herramienta.

|**Característica**|**Enterprise Edition**|**Professional Edition**|**Community Edition**|
|-|-|-|-|
|**Mapas de código**|Sí|Solo admite la lectura de mapas de código, el filtrado de mapas de código, la adición de nuevos nodos genéricos y la creación de un nuevo gráfico dirigido a partir de una selección.|-|
|**Diagramas de dependencias**|Sí|Solo admite la lectura de diagramas de dependencias.|Solo admite la lectura de diagramas de dependencias.|
|**Gráficos dirigidos** (diagramas DGML)|Sí|Sí|Sí|
|**Clonación de código**|Sí|-|-|
