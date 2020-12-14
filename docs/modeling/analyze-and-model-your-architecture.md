---
title: Analizar y modelar la arquitectura
description: Aprenda a usar las herramientas de modelado y arquitectura de Visual Studio para diseñar y modelar la aplicación para asegurarse de que la aplicación cumple los requisitos arquitectónicos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71296b9ccb2e442d1bd9bc13865e0086821bf030
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361162"
---
# <a name="analyze-and-model-your-architecture"></a>Analizar y modelar la arquitectura

Asegúrese de que la aplicación cumple los requisitos de la arquitectura; para ello, use las herramientas de modelado y arquitectura de Visual Studio para diseñar y modelar la aplicación.

* Use Visual Studio para visualizar la estructura, el comportamiento y las relaciones del código, y así comprender más fácilmente el código actual del programa.

* Instruya al equipo en la necesidad de respetar las dependencias arquitectónicas.

* Cree modelos con distintos niveles de detalle a lo largo del ciclo de vida de la aplicación como parte del proceso de desarrollo.

Vea [Escenario: Cambio del diseño mediante modelado y visualización](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="article-reference"></a>Referencia de artículos

|Escenario|Artículos|
|-|-|
|**Visualizar el código**:<br /><br />- Cree mapas de código para ver la organización y las relaciones del código. Visualice las dependencias entre ensamblados, espacios de nombres, clases, métodos, etcétera.<br />- Vea la estructura y los miembros de clase de un proyecto específico mediante la creación de diagramas de clases desde el código.<br />- Busque los conflictos entre el código y su diseño mediante la creación de diagramas de dependencias para validar el código.|- [Visualizar el código](../modeling/visualize-code.md)<br />- [Trabajo con clases y otros tipos (Diseñador de clases)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />- [Vídeo: Descripción del diseño de código con mapas de código de Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />- [Vídeo: Validación de las dependencias de la arquitectura en tiempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Definir la arquitectura**:<br /><br />- Defina y aplique restricciones a las dependencias entre los componentes del código mediante la creación de diagramas de dependencias.|- [Vídeo: Validación de las dependencias de arquitectura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Validar el sistema con los requisitos y el diseño previsto:**<br /><br />- Valide las dependencias del código con diagramas de dependencias en los que se describe la arquitectura planeada y evite los cambios que puedan entrar en conflicto con el diseño.|- [Vídeo: Validación de las dependencias de arquitectura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Personalizar modelos y diagramas**:<br /><br />- Cree lenguajes específicos de dominio propios.|- [Modelado del SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generación de texto usando plantillas T4**:<br /><br />- Use bloques de texto y lógica de control dentro de plantillas para generar archivos de texto.<br /> - Generación de plantillas T4 con MSBuild incluida en Visual Studio|- [Generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md)|
|**Compartir modelos, diagramas y mapas de código mediante el control de versiones de Team Foundation**:<br /><br />- Coloque mapas de código y diagramas de dependencias bajo el control de versiones de Team Foundation para poder compartirlos.| |

Para saber qué ediciones de Visual Studio admiten cada característica, vea [Compatibilidad de ediciones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="types-of-models-and-typical-uses"></a>Tipos de modelos y usos habituales

### <a name="code-maps"></a>Mapas de código

Los mapas de código ayudan a ver la organización y las relaciones existentes en el código.

**Usos habituales:**

- Examine el código de programa a fin de entender mejor su estructura y sus dependencias, cómo actualizarlo y calcular el costo de los cambios propuestos.

**Consulte:**

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)
- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)
- [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagrams"></a>Diagramas de dependencias

Los diagramas de dependencias permiten definir la estructura de una aplicación como un conjunto de capas o bloques con dependencias explícitas. La validación activa muestra los conflictos entre dependencias del código y las dependencias descritas en un diagrama de dependencias.

**Usos habituales:**

- Estabilizar la estructura de la aplicación a través de numerosos cambios a lo largo de su duración.
- Detectar conflictos de dependencia involuntarios antes de proteger los cambios en el código.

**Consulte:**

- [Crear diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)
- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Validación código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Lenguaje específico del dominio (DSL)

Un DSL es una notación que se diseña con un objetivo concreto. En Visual Studio, suele ser gráfico.

**Usos habituales:**

- Generar o configurar partes de la aplicación. Hay que realizar algún trabajo para desarrollar la notación y las herramientas. El resultado puede ser un mejor ajuste al dominio que una personalización UML.
- Para proyectos grandes o en líneas de productos donde la inversión en desarrollo de DSL y sus herramientas se recupera cuando se usa en más de un proyecto.

**Consulte:**

- [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="see-also"></a>Consulte también

- [Novedades de modelado en Visual Studio 2017](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps y administración del ciclo de vida de las aplicaciones](/azure/devops/user-guide/devops-alm-overview)
