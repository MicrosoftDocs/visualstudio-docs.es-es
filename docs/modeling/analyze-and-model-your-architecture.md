---
title: Herramientas de modelado y arquitectura
description: Diseñe y modele la aplicación para asegurarse de que cumple los requisitos de la arquitectura.
ms.custom: SEO-VS-2020
ms.date: 06/04/2021
ms.topic: overview
helpviewer_keywords:
- diagrams - modeling
- architecture
- code visualization
- application design
- code exploration
- modeling
- application architecture
- architecture [Visual Studio ALM], modeling
- application modeling
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 542b74e7d3bb73847303fa4215651eea7e110e91
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384881"
---
# <a name="analyze-and-model-your-architecture"></a>Analizar y modelar la arquitectura

Asegúrese de que la aplicación cumple los requisitos de la arquitectura; para ello, use las herramientas de modelado y arquitectura de Visual Studio para diseñar y modelar la aplicación.

1. Comprenda mejor el código de programa existente mediante la [visualización de la estructura del código](visualize-code.md), el comportamiento y las relaciones con mapas de código y diagramas de dependencias.
    - Cree **mapas de código** para ver la organización y las relaciones del código. 
    - Visualice las dependencias entre ensamblados, espacios de nombres, clases, métodos, etcétera.
    - Busque los conflictos entre el código y su diseño mediante la creación de **diagramas de dependencias** para validar el código.
    - Vea la estructura y los miembros de clase de un proyecto específico mediante la [creación de diagramas de clases a partir del código](../ide/class-designer/designing-and-viewing-classes-and-types.md).
    - [Genere texto mediante plantillas T4](../modeling/code-generation-and-t4-text-templates.md) con bloques de texto y controle la lógica dentro de las plantillas para generar archivos basados en texto. 
    
1. Instruya al equipo en la necesidad de respetar las dependencias arquitectónicas.

1. Cree modelos con distintos niveles de detalle a lo largo del ciclo de vida de la aplicación como parte del proceso de desarrollo.

Vea [Escenario: Cambio del diseño mediante modelado y visualización](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="code-maps"></a>Mapas de código

Los mapas de código son un tipo de modelo que le ayuda a ver la organización y las relaciones en el código.

Use los mapas para examinar el código de programa a fin de entender mejor su estructura y sus dependencias, cómo actualizarlo y calcular el costo de los cambios propuestos.

Más información:
- [Instalación de herramientas de código de arquitectura](install-architecture-tools.md)
- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)
- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)
- [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="dependency-diagrams"></a>Diagramas de dependencias

Los diagramas de dependencias permiten definir la estructura de una aplicación como un conjunto de capas o bloques con dependencias explícitas. La validación activa muestra los conflictos entre dependencias del código y las dependencias descritas en un diagrama de dependencias.

Use los diagramas de dependencia para lo siguiente: 
- Estabilizar la estructura de la aplicación a través de numerosos cambios a lo largo de su duración.
- Detectar conflictos de dependencia involuntarios antes de proteger los cambios en el código.

Más información:
- [Instalación de herramientas de código de arquitectura](install-architecture-tools.md)
- [Crear diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)
- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Validación código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)

## <a name="domain-specific-language-dsl-models"></a>Modelos de lenguaje específico del dominio (DSL)

Un DSL es una notación que se diseña con un objetivo concreto. En Visual Studio, suele ser gráfico.

Use el lenguaje específico de dominio para lo siguiente: 
- Generar o configurar partes de la aplicación. Hay que realizar algún trabajo para desarrollar la notación y las herramientas. El resultado puede ser un mejor ajuste al dominio que una personalización UML.
- Para proyectos grandes o en líneas de productos donde la inversión en desarrollo de DSL y sus herramientas se recupera cuando se usa en más de un proyecto.

Más información:
- [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)


## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Compatibilidad de ediciones con las herramientas de arquitectura y modelado

Visual Studio está disponible en varias versiones. No todas son compatibles con las herramientas de arquitectura y modelado. En la tabla siguiente se muestra la disponibilidad de cada herramienta.

|**Característica**|**Enterprise Edition**|**Professional Edition**|**Community Edition**|
|-|-|-|-|
|**Mapas de código**|Sí|Solo admite la lectura y el filtrado de mapas de código, la adición de nuevos nodos genéricos y la creación de un gráfico dirigido a partir de una selección.|-|
|**Diagramas de dependencias**|Sí|Solo admite la lectura de diagramas de dependencias.|Solo admite la lectura de diagramas de dependencias.|
|**Gráficos dirigidos** (diagramas DGML)|Sí|Sí|Sí|
|**Clon de código**|Sí|-|-|
