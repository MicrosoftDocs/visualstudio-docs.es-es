---
title: Visualizar el código
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04614d6b4901ea20dee938b2b2240ef3c05b1a7b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="visualize-code"></a>Visualizar el código
Puede usar las herramientas de visualización y modelado de Visual Studio para ayudarle a entender el código existente y describir la aplicación. Esto le permite aprender de forma visual cómo pueden afectar los cambios al código y le ayudará a evaluar el esfuerzo y los riesgos que conllevan dichos cambios. Por ejemplo:

-   Para entender las relaciones del código, asigne las relaciones de forma visual.

-   Para describir la arquitectura del sistema y mantener la coherencia con el diseño del código, crear diagramas de dependencia y valide el código contra estos diagramas.

-   Para describir las estructuras de clases, cree diagramas de clases.

 Estas herramientas también le ayudan a comunicarse con más facilidad con las personas implicadas en el proyecto.

 Para ver qué versiones de Visual Studio admite cada característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

|||
|-|-|
|**Comprender el código y sus relaciones:**<br /><br /> Asigne relaciones entre elementos de código específicos.<br /><br /> Vea una introducción sobre las relaciones del código para toda la solución.<br /><br /> **Nota**: en esta versión de Visual Studio, se usa el término *mapa de código* en lugar de *gráfico de dependencias*.|-   [Asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Comprender las estructuras de clase:**<br /><br /> Visualice la estructura de las clases de un proyecto mediante la creación de diagramas de clases desde el código.|[Cómo: Agregar diagramas de clase a proyectos (Diseñador de clases)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Describir el diseño de alto nivel del sistema y validar el código comparándolo con este diseño:**<br /><br /> Mediante la creación de diagramas de dependencia se describen el diseño de alto nivel del sistema y sus dependencias previstas. Valide el código con este diseño para asegurarse de que las dependencias del código siguen siendo coherentes con el diseño.|-   [Crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Links**|
|------------------|---------------|
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogs**|[Blog de Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|
|**Artículos y diarios técnicos**|[Foro de arquitectura MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Vea también

- [Escenario: Cambiar el diseño mediante la visualización y el modelado](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)
- [Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)
- [Usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
