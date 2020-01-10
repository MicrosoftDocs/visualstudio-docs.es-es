---
title: Visualizar código | Microsoft Docs
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
ms.openlocfilehash: 9dcb6edf8ce69d48805c3ad8c3c25ef9cc0ed591
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851346"
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
|**Entender el código y sus relaciones:**<br /><br /> Asigne relaciones entre elementos de código específicos.<br /><br /> Vea una introducción sobre las relaciones del código para toda la solución.<br /><br /> **Nota**: en esta versión de Visual Studio, se usa el término *mapa de código* en lugar de *gráfico de dependencias*.|-   [asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)<br />-   [usar mapas de código para depurar las aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Comprender las estructuras de clase:**<br /><br /> Visualice la estructura de las clases de un proyecto mediante la creación de diagramas de clases desde el código.|[Cómo: Agregar diagramas de clase a proyectos (Diseñador de clases)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Describa el diseño del sistema de alto nivel y valide el código con este diseño:**<br /><br /> Describa el diseño de alto nivel del sistema y sus dependencias previstas mediante la creación de diagramas de capas. Valide el código con este diseño para asegurarse de que las dependencias del código siguen siendo coherentes con el diseño.|-   [crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)<br />[diagramas de capas de -   : referencia](../modeling/layer-diagrams-reference.md)<br />[diagramas de capas de -   : instrucciones](../modeling/layer-diagrams-guidelines.md)<br />-   [validar el código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)|
|**Comunicar los requisitos del usuario y la arquitectura:**<br /><br /> Para modelar los requisitos del usuario y la arquitectura del sistema de software, dibuje los siguientes diagramas UML: actividad, componente, clase, secuencia y caso de uso.|-   [crear modelos para la aplicación](../modeling/create-models-for-your-app.md)<br />[requisitos de usuario del modelo](../modeling/model-user-requirements.md) de -   <br />-   [modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Links**|
|------------------|---------------|
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas ADSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogs**|[Blog de Visual Studio ALM + Team Foundation Server](https://blogs.msdn.com/b/visualstudioalm)|
|**Artículos y diarios técnicos**|[Foro de arquitectura de MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Vea también
 [Escenario: cambiar el diseño mediante la visualización y el modelado](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [análisis y modelado arquitectura](../modeling/analyze-and-model-your-architecture.md) [crear modelos para la aplicación](../modeling/create-models-for-your-app.md) modelo [requisitos de usuario](../modeling/model-user-requirements.md) [modelo la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md) [usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)
