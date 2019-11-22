---
title: Analyze and model your architecture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 49c421af5aa6c91535b05f0beca88099ea7a2eaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297948"
---
# <a name="analyze-and-model-your-architecture"></a>Analizar y modelar la arquitectura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Asegúrese de que la aplicación cumple los requisitos de usuario: use la arquitectura de Visual Studio y las herramientas de modelado para diseñar y modelar la aplicación. Use Visual Studio para visualizar la estructura, el comportamiento y las relaciones del código, y así comprender más fácilmente el código actual del programa.

 Cree modelos con distintos niveles de detalle a lo largo del ciclo de vida de la aplicación como parte del proceso de desarrollo. Vincule elementos del modelo a elementos de trabajo de Team Foundation Server y su plan de desarrollo. De este modo, podrá realizar un seguimiento de los requisitos, las tareas, los casos de prueba, los errores y otros trabajos asociados con los modelos. See [Scenario: Change your design using visualization and modeling](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Para ver qué versiones de Visual Studio admite cada característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="to"></a>En

|||
|-|-|
|**Visualizar el código**:<br /><br /> -   See the code's organization and relationships by creating code maps. Visualice las dependencias entre ensamblados, espacios de nombres, clases, métodos, etcétera.<br />-   See the class structure and members for a specific project by creating class diagrams from code.<br />-   Find conflicts between your code and its design by creating layer diagrams to validate code.<br /><br /> **Nota**: en esta versión de Visual Studio, se usa el término *mapa de código* en lugar de *gráfico de dependencias*. El término *gráfico* , cuando se usa solo, suele hacer referencia a un gráfico dirigido o a un diagrama DGML (o documento). Los mapas de código son un tipo especializado de diagrama DGML.|-   [Visualizar el código](../modeling/visualize-code.md)<br />-   [Working with Classes and Other Types (Class Designer)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: Understand your code dependencies through visualization (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [Video: Visualize the impact of a change (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252068)|
|**Describir y comunicar requisitos de usuario**:<br /><br /> -   Clarify user stories, business rules, and other requirements and help ensure their consistency by drawing UML diagrams such as use case, activity, and class diagrams.|-   [Create models for your app](../modeling/create-models-for-your-app.md)<br />-   [Model user requirements](../modeling/model-user-requirements.md)<br />-   [Video: Improve architecture through modeling (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252078)|
|**Definir la arquitectura**:<br /><br /> -   Model the large-scale structure of your software system and the design patterns by drawing UML component, class, and sequence diagrams.<br />-   Define and enforce constraints on dependencies between the components of your code by creating layer diagrams.|-   [Create models for your app](../modeling/create-models-for-your-app.md)<br />-   [Model your app's architecture](../modeling/model-your-app-s-architecture.md)<br />-   [Video: Improve architecture through modeling (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [Video: Use layer diagrams to design and validate your architecture (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**Validar el sistema con los requisitos y el diseño previsto:**<br /><br /> -   Define acceptance tests or system tests based on the requirements models. De este modo, establecerá una fuerte relación entre las pruebas y los requisitos del usuario, y costará menos actualizar el sistema cuando cambien los requisitos.<br />-   Validate code dependencies with layer diagrams that describe the intended architecture and prevent changes that might conflict with the design.|-   [Validate your system during development](../modeling/validate-your-system-during-development.md)<br />-   [Video: Use layer diagrams to design and validate your architecture (Channel 9)](https://go.microsoft.com/fwlink/?LinkID=252073)|
|**Compartir modelos, diagramas y mapas de código mediante el control de versiones de Team Foundation**:<br /><br /> -   Put code maps, modeling projects, UML diagrams, and layer diagrams under Team Foundation version control so you can share them.|Cuando haya varios usuarios que trabajen con estos elementos en el control de versiones de Team Foundation, use estas instrucciones para evitar problemas con el control de versiones:<br /><br /> -   [Manage models and diagrams under version control](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**Generar o configurar partes de la aplicación a partir de UML o de los lenguajes específicos de dominio**:<br /><br /> -   Make your design more responsive to requirements changes and easily variable across a product line.|-   [Generate and configure your app from models](../modeling/generate-and-configure-your-app-from-models.md)|
|**Personalizar modelos y diagramas**:<br /><br /> -   Adapt models to how your project uses them by defining additional properties for UML elements, validation constraints to make sure that your models conform to your business rules, and additional menu commands and toolbox items.<br />-   Create your own domain-specific languages.|-   [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Modeling SDK for Visual Studio - Domain-Specific Languages](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generación de texto usando plantillas T4**:<br /><br /> -   Use text blocks and control logic inside templates to generate text-based files.|-   [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>Tipos de modelos y usos

|**Tipo y modelo y usos habituales**|
|-------------------------------------|
|**Mapas de código**<br /><br /> Los mapas de código ayudan a ver la organización y las relaciones existentes en el código.<br /><br /> Usos típicos:<br /><br /> -   Examine program code so you can better understand its structure and its dependencies, how to update it, and estimate the cost of proposed changes.<br /><br /> Vea:<br /><br /> -   [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Layer diagram**<br /><br /> Los diagramas de capas permiten definir la estructura de una aplicación como un conjunto de capas o bloques con dependencias explícitas. Puede ejecutar la validación para detectar conflictos entre dependencias del código y las dependencias descritas en un diagrama de capas.<br /><br /> Usos típicos:<br /><br /> -   Stabilize the structure of the application through numerous changes over its life.<br />-   Discover unintentional dependency conflicts before checking in changes to the code.<br /><br /> Vea:<br /><br /> -   [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md)<br />-   [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md)|
|**UML model**<br /><br /> Un modelo UML incluye varias vistas, como son los diagramas de secuencias, clases, componentes, casos de uso y actividades. Puede personalizar el modelo UML para que se ajuste al dominio de la aplicación. Por ejemplo, puede adjuntar etiquetas, información adicional y restricciones a los elementos del modelo. También puede definir herramientas que actúen en los modelos. See [Create models for your app](../modeling/create-models-for-your-app.md).<br /><br /> Usos típicos:<br /><br /> -   Describe requirements and design. Puede aplicar rápidamente UML al desarrollo de cualquier aplicación. See [Use models in your development process](../modeling/use-models-in-your-development-process.md).<br />-   Generate or configure tests or parts of an application. Es necesario realizar algún trabajo para personalizar la notación y desarrollar las plantillas de generación o la aplicación configurable. See [Generate and configure your app from models](../modeling/generate-and-configure-your-app-from-models.md).<br />-   For general description and for code generation or configuration in smaller projects.|
|**Lenguaje específico del dominio (DSL)**<br /><br /> Un DSL es una notación que se diseña con un objetivo concreto. En Visual Studio, suele ser un objetivo gráfico.<br /><br /> Usos típicos:<br /><br /> -   Generate or configure parts of the application. Hay que realizar algún trabajo para desarrollar la notación y las herramientas. El resultado puede ser un mejor ajuste al dominio que una personalización UML.<br />-   For large projects or in product lines where the investment in developing the DSL and its tools is returned by its use in more than one project.<br /><br /> Vea:<br /><br /> -   [Modeling SDK for Visual Studio - Domain-Specific Languages](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>¿Dónde puedo obtener más información?

|||
|-|-|
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas ADSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>Vea también

- [What's new for modeling in Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps y administración del ciclo de vida de las aplicaciones](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
