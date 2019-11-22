---
title: Visualize code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 955103b6d28e90321fb45c23825f0c2a25362208
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301313"
---
# <a name="visualize-code"></a>Visualizar el código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar las herramientas de visualización y modelado de Visual Studio para ayudarle a entender el código existente y describir la aplicación. Esto le permite aprender de forma visual cómo pueden afectar los cambios al código y le ayudará a evaluar el esfuerzo y los riesgos que conllevan dichos cambios. Por ejemplo:

- Para entender las relaciones del código, asigne las relaciones de forma visual.

- Para describir la arquitectura del sistema y mantener el código coherente con el diseño, cree diagramas de capas y valide el código con dichos diagramas.

- Para describir las estructuras de clases, cree diagramas de clases.

- Para modelar y comunicar distintos aspectos del sistema, dibuje diagramas de Lenguaje de modelos unificado (UML). Por ejemplo, puede modelar componentes, tipos, interacciones y procesos de un sistema.

  Estas herramientas también le ayudan a comunicarse con más facilidad con las personas implicadas en el proyecto. Por ejemplo, puede usar diagramas de clases UML para crear un glosario común para analizar el sistema con las partes interesadas, los usuarios y los miembros del equipo.

  Para ver qué versiones de Visual Studio admite cada característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

|||
|-|-|
|**Understand code and its relationships:**<br /><br /> Asigne relaciones entre elementos de código específicos.<br /><br /> Vea una introducción sobre las relaciones del código para toda la solución.<br /><br /> **Nota**: en esta versión de Visual Studio, se usa el término *mapa de código* en lugar de *gráfico de dependencias*.|-   [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Map methods on the call stack while debugging](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Understand class structures:**<br /><br /> Visualice la estructura de las clases de un proyecto mediante la creación de diagramas de clases desde el código.|[Cómo: Agregar diagramas de clase a proyectos (Diseñador de clases)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Describe the high-level system design and validate code against this design:**<br /><br /> Describa el diseño de alto nivel del sistema y sus dependencias previstas mediante la creación de diagramas de capas. Valide el código con este diseño para asegurarse de que las dependencias del código siguen siendo coherentes con el diseño.|-   [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md)<br />-   [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md)<br />-   [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md)|
|**Communicate the user requirements and architecture:**<br /><br /> Para modelar los requisitos del usuario y la arquitectura del sistema de software, dibuje los siguientes diagramas UML: actividad, componente, clase, secuencia y caso de uso.|-   [Create models for your app](../modeling/create-models-for-your-app.md)<br />-   [Model user requirements](../modeling/model-user-requirements.md)<br />-   [Model your app's architecture](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Links**|
|------------------|---------------|
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas ADSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogs**|[Blog de Visual Studio ALM + Team Foundation Server](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**Artículos y diarios técnicos**|[MSDN Architecture Forum](https://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Vea también
 [Scenario: Change your design using visualization and modeling](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [Analyzing and Modeling Architecture](../modeling/analyze-and-model-your-architecture.md) [Create models for your app](../modeling/create-models-for-your-app.md) [Model user requirements](../modeling/model-user-requirements.md) [Model your app's architecture](../modeling/model-your-app-s-architecture.md) [Use models in your development process](../modeling/use-models-in-your-development-process.md)
