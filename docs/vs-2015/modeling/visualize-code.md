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
ms.openlocfilehash: 665dc76126eac964f405be06605c40b5b30cc9a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532943"
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

|Escenario|Artículos|
|-|-|
|**Entender el código y sus relaciones:**<br /><br /> Asigne relaciones entre elementos de código específicos.<br /><br /> Vea una introducción sobre las relaciones del código para toda la solución.<br /><br /> **Nota**: en esta versión de Visual Studio, se usa el término *mapa de código* en lugar de *gráfico de dependencias*.|-   [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Usar mapas de código para depurar las aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Entender las estructuras de clases:**<br /><br /> Visualice la estructura de las clases de un proyecto mediante la creación de diagramas de clases desde el código.|[Cómo: Agregar diagramas de clases a proyectos (Diseñador de clases)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Describir el diseño de alto nivel del sistema y validar el código con este diseño:**<br /><br /> Describa el diseño de alto nivel del sistema y sus dependencias previstas mediante la creación de diagramas de capas. Valide el código con este diseño para asegurarse de que las dependencias del código siguen siendo coherentes con el diseño.|-   [Crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramas de capas: referencia](../modeling/layer-diagrams-reference.md)<br />-   [Diagramas de capas: instrucciones](../modeling/layer-diagrams-guidelines.md)<br />-   [Validar el código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)|
|**Comunicar los requisitos del usuario y la arquitectura:**<br /><br /> Para modelar los requisitos del usuario y la arquitectura del sistema de software, dibuje los siguientes diagramas UML: actividad, componente, clase, secuencia y caso de uso.|-   [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)<br />-   [Requisitos de usuario de modelo](../modeling/model-user-requirements.md)<br />-   [Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Recursos externos

|**Categoría**|**Vínculos**|
|------------------|---------------|
|**Foros**|-   [Herramientas de visualización y modelado de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [SDK de visualización y modelado de Visual Studio (Herramientas ADSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogs**|[Blog de Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Artículos y diarios técnicos**|[Foro de arquitectura de MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Consulte también
 [Escenario: cambiar el diseño mediante la visualización y el modelado](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [análisis y modelado arquitectura](../modeling/analyze-and-model-your-architecture.md) [crear modelos para la aplicación](../modeling/create-models-for-your-app.md) modelo [requisitos de usuario](../modeling/model-user-requirements.md) [modelo la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md) [usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)
