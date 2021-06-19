---
title: Referencia de diagramas de dependencias
description: Obtenga información sobre Visual Studio, puede usar un diagrama de dependencias para visualizar la arquitectura lógica de alto nivel del sistema.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb138164cfab44778c932a4bcb93572a3053a70
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391041"
---
# <a name="dependency-diagrams-reference"></a>Diagramas de dependencias: referencia

En Visual Studio, puede usar un diagrama *de dependencias* para visualizar la arquitectura lógica de alto nivel del sistema. Un diagrama de dependencias organiza los artefactos físicos del sistema en grupos lógicos y abstractos denominados *capas*. Estas capas describen las tareas principales que realizan los artefactos o los componentes principales del sistema. Cada capa también puede contener capas anidadas que describen tareas más detalladas.

Para ver qué ediciones de Visual Studio admiten esta característica, consulte [Compatibilidad de ediciones con las herramientas de arquitectura y modelado](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

> [!NOTE]
> Los diagramas de dependencias para proyectos de .NET Core se admiten a partir Visual Studio versión 16.2 de 2019.

Se pueden especificar las dependencias planeadas o existentes entre las capas. Estas dependencias, que se representan como flechas, indican qué capas pueden usar o usan actualmente la funcionalidad representada por otras capas. Al organizar el sistema en capas que describen roles y funciones distintos, un diagrama de dependencias puede ayudarle a comprender, reutilizar y mantener el código más fácilmente.

Use un diagrama de dependencias para ayudarle a realizar las siguientes tareas:

- Comunicar la arquitectura lógica existente o planeada del sistema.

- Detectar conflictos entre el código existente y la arquitectura planeada.

- Visualizar el impacto de los cambios en la arquitectura planeada al refactorizar, actualizar o desarrollar el sistema.

- Reforzar la arquitectura planeada durante el desarrollo y el mantenimiento del código incluyendo la validación en las operaciones de protección y compilación.

En este tema se describen los elementos que puede usar en un diagrama de dependencias. Para obtener información más detallada sobre cómo crear y dibujar diagramas de dependencia, vea [Diagramas de dependencia: directrices.](../modeling/layer-diagrams-guidelines.md) Para obtener más información sobre los patrones de capas, visite el sitio [patterns & Practices](https://archive.codeplex.com/?p=apparch).

## <a name="reading-dependency-diagrams"></a>Leer diagramas de dependencias

![Elementos en diagramas de dependencia](../modeling/media/uml_layerrefreading.png)

En la tabla siguiente se describen los elementos que puede usar en un diagrama de dependencias.

|**Forma**|**Element**|**Descripción**|
|-|-|-|
|1|**Nivel**|Grupo lógico de artefactos físicos del sistema. Estos artefactos pueden ser espacios de nombres, proyectos, clases, métodos, etc.<br /><br /> Para ver los artefactos vinculados a una capa, abra el menú contextual de la capa y, a continuación, elija Ver vínculos **para** abrir el Explorador **de capas.**<br /><br /> Para obtener más información, vea [Layer Explorer](#Explorer).<br /><br /> -   **Dependencias de espacio de nombres** prohibido: especifica que los artefactos asociados a esta capa no pueden depender de los espacios de nombres especificados.<br />-   **Espacios de nombres prohibidos:** especifica que los artefactos asociados a esta capa no deben pertenecer a los espacios de nombres especificados.<br />-   **Espacios de nombres necesarios:** especifica que los artefactos asociados a esta capa deben pertenecer a uno de los espacios de nombres especificados.|
|2|**Dependencia**|Indica que una capa puede usar la funcionalidad de otra capa, pero no viceversa.<br /><br /> -   **Dirección:** especifica la dirección de la dependencia.|
|3|**Dependencia bidireccional**|Indica que una capa puede usar la funcionalidad de otra capa, y viceversa.<br /><br /> -   **Dirección:** especifica la dirección de la dependencia.|
|4|**Comentario**|Use esta opción para agregar notas generales al diagrama o elementos del diagrama.|
|5|**Vínculo de comentario**|Se usa para vincular comentarios a elementos del diagrama.|

## <a name="layer-explorer"></a><a name="Explorer"></a> Explorador de capas

Puede vincular cada capa a artefactos de la solución, como proyectos, clases, espacios de nombres, archivos de proyecto y otros elementos del software. El número de una capa muestra la cantidad de artefactos vinculados a ella. Sin embargo, cuando lea el número de artefactos de una capa, recuerde lo siguiente:

- Si una capa se vincula a un artefacto que contiene otros artefactos, pero no se vincula directamente a estos otros artefactos, el número incluye únicamente el artefacto vinculado. Sin embargo, los demás artefactos se incluyen para el análisis durante la validación de capas.

     Por ejemplo, si una capa está vinculada a un solo espacio de nombres, el número de artefactos vinculados es 1, aunque el espacio de nombres contenga clases. Si la capa tiene también vínculos a cada clase del espacio de nombres, el número incluirá las clases vinculadas.

- Si una capa contiene otras que están vinculadas a artefactos, la capa contenedora también está vinculada a esos artefactos, incluso aunque el número de la capa contenedora no los incluya.

Para obtener más información sobre cómo vincular capas y artefactos, vea:

- [Diagramas de dependencias: Directrices](../modeling/layer-diagrams-guidelines.md)

- [Crear diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Examen de los artefactos vinculados

En el diagrama de dependencias, abra el menú contextual de una o varias capas y, a continuación, elija **Ver vínculos.**

**El Explorador de** capas se abre y muestra los artefactos que están vinculados a las capas seleccionadas. **El Explorador de** capas tiene una columna que muestra cada una de las propiedades de los vínculos de artefacto.

> [!NOTE]
> Si no puede ver todas estas propiedades, expanda la ventana **Explorador de** capas.

|**Columna del Explorador de capas**|**Descripción**|
|-|-|
|**Categorías**|Tipo de artefacto, como una clase, espacio de nombres, archivo de código fuente, etcétera|
|**Nivel**|Capa que se vincula al artefacto|
|**Admite validación**|Si **es True**, el proceso de validación de capas puede comprobar que el proyecto se ajusta a las dependencias hacia o desde este elemento.<br /><br /> Si **es False**, el vínculo no participa en el proceso de validación de capas.<br /><br /> Para obtener más información, vea [Diagramas de dependencias: instrucciones](../modeling/layer-diagrams-guidelines.md).|
|**Identificador**|Referencia al artefacto vinculado|

## <a name="see-also"></a>Vea también

- [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)
