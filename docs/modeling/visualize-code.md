---
title: Visualizar el código
description: Obtenga información sobre cómo puede usar las herramientas de visualización y modelado Visual Studio para comprender el código existente y describir la aplicación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90c180bf9d910227013c2e089001ce5332cd1bd3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388352"
---
# <a name="visualize-code"></a>Visualizar el código

Puede usar las herramientas de visualización y modelado de Visual Studio para ayudarle a entender el código existente y describir la aplicación. Esto le permite aprender de forma visual cómo pueden afectar los cambios al código y le ayudará a evaluar el esfuerzo y los riesgos que conllevan dichos cambios. Por ejemplo:

- Para entender las relaciones del código, asigne las relaciones de forma visual.

- Para describir la arquitectura del sistema y mantener el código coherente con su diseño, cree diagramas de dependencias y valide el código con estos diagramas.

- Para describir las estructuras de clases, cree diagramas de clases.

Estas herramientas también le ayudan a comunicarse con más facilidad con las personas implicadas en el proyecto.

Para saber qué ediciones de Visual Studio admiten cada característica, vea [Compatibilidad de ediciones con las herramientas de arquitectura y modelado](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

|Escenario|Artículos|
|-|-|
|**Entender el código y sus relaciones:**<br /><br /> Asigne relaciones entre elementos de código específicos.<br /><br /> Vea una introducción sobre las relaciones del código para toda la solución.|- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)<br />- [Uso de mapas de código para depurar las aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Buscar posibles problemas mediante analizadores de mapa de código](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Entender las estructuras de clases:**<br /><br /> Visualice la estructura de las clases de un proyecto mediante la creación de diagramas de clases desde el código.|[Cómo: Agregar diagramas de clases a proyectos (Diseñador de clases)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Describir el diseño de alto nivel del sistema y validar el código con este diseño:**<br /><br /> Describa el diseño del sistema de alto nivel y sus dependencias previstas mediante la creación de diagramas de dependencias. Valide el código con este diseño para asegurarse de que las dependencias del código siguen siendo coherentes con el diseño.|- [Creación de diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)<br />- [Diagramas de dependencia: directrices](../modeling/layer-diagrams-guidelines.md)<br />- [Validación de código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Vea también

- [Instalación de herramientas de código de arquitectura](install-architecture-tools.md)
- [Escenario: Cambiar el diseño usando modelado y visualización](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analizar y modelar arquitectura](../modeling/analyze-and-model-your-architecture.md)
- [Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)
- [Usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
