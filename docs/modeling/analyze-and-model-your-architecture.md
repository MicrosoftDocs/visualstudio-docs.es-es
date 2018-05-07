---
title: Analizar y modelar la arquitectura
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be58a86ec6c3b87954ff5b5be012ce636ad52204
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="analyze-and-model-your-architecture"></a>Analizar y modelar la arquitectura
Asegúrese de que la aplicación cumple los requisitos de la arquitectura mediante la arquitectura de Visual Studio y herramientas para diseñar y modelar la aplicación de modelado.

* Use Visual Studio para visualizar la estructura, el comportamiento y las relaciones del código, y así comprender más fácilmente el código actual del programa.

* Formar a su equipo en la necesidad de respeta dependencias arquitectónicas.

* Cree modelos con distintos niveles de detalle a lo largo del ciclo de vida de la aplicación como parte del proceso de desarrollo.

Vea [escenario: cambiar el diseño usando modelado y visualización](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="to"></a>En

|||
|-|-|
|**Visualizar el código**:<br /><br /> : Vea el código de la organización y las relaciones mediante la creación de mapas de código. Visualice las dependencias entre ensamblados, espacios de nombres, clases, métodos, etcétera.<br />: Vea la estructura de clases y miembros de un proyecto específico creando diagramas de clases desde el código.<br />-Encontrar los conflictos entre el código y su diseño creando diagramas de dependencia para validar el código.|-   [Visualizar el código](../modeling/visualize-code.md)<br />-   [Trabajar con clases y otros tipos (Diseñador de clases)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Vídeo: Comprender el diseño de código con mapas de código de Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Vídeo: Validar las dependencias de arquitectura en tiempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Definir la arquitectura**:<br /><br /> -Defina y aplique restricciones a las dependencias entre los componentes del código creando diagramas de dependencia.|-   [Vídeo: Valide las dependencias de la arquitectura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Validar el sistema con los requisitos y el diseño previsto:**<br /><br /> -Valide las dependencias de código con los diagramas de dependencia que describen la arquitectura planeada y evite los cambios que puedan entrar en conflicto con el diseño.|-   [Vídeo: Valide las dependencias de la arquitectura con Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Personalizar modelos y diagramas**:<br /><br /> -Crear sus propios lenguajes específicos de dominio.|-   [Modelado del SDK de Visual Studio - lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generación de texto usando plantillas T4**:<br /><br /> -Usar bloques de texto y lógica de control dentro de las plantillas para generar archivos de texto.<br /> -Compilación de la plantilla de T4 con MSBuild incluido en Visual Studio|-   [Generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md)|
|**Compartir modelos, diagramas y mapas de código mediante el control de versiones de Team Foundation**:<br /><br /> -Coloque los mapas de código, proyectos y diagramas de dependencia en el control de versiones de Team Foundation para poder compartirlos.| |

Para ver qué versiones de Visual Studio admite cada característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="types-of-models-and-typical-uses"></a>Tipos de modelos y usos típicos

### <a name="code-maps"></a>Mapas de código
Los mapas de código ayudan a ver la organización y las relaciones existentes en el código.

**Usos típicos:**

-   Examine el código de programa a fin de entender mejor su estructura y sus dependencias, cómo actualizarlo y calcular el costo de los cambios propuestos.

**Vea:**

-   [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)
-   [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)
-   [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagram"></a>Diagrama de dependencia
Diagramas de dependencia le permiten definir la estructura de una aplicación como un conjunto de capas o bloques con dependencias explícitas. Puede ejecutar la validación para detectar conflictos entre dependencias del código y las dependencias descritas en un diagrama de dependencia.

**Usos típicos:**

-   Estabilizar la estructura de la aplicación a través de numerosos cambios a lo largo de su duración.
-   Detectar conflictos de dependencia involuntarios antes de proteger los cambios en el código.

**Vea:**

-   [Creación de diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)
-   [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
-   [Validación de código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Lenguaje específico del dominio (DSL)
Un DSL es una notación que se diseña con un objetivo concreto. En Visual Studio, suele ser un objetivo gráfico.

**Usos típicos:**

-   Generar o configurar partes de la aplicación. Hay que realizar algún trabajo para desarrollar la notación y las herramientas. El resultado puede ser un mejor ajuste al dominio que una personalización UML.
-   Para proyectos grandes o en líneas de productos donde la inversión en desarrollo de DSL y sus herramientas se recupera cuando se usa en más de un proyecto.

**Vea:**

-   [Modelar el SDK de Visual Studio: lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="where-can-i-get-more-information"></a>¿Dónde puedo obtener más información?

[Visualización y modelado foro de herramientas de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)

## <a name="see-also"></a>Vea también

- [' S new](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps y Application Lifecycle Management](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
