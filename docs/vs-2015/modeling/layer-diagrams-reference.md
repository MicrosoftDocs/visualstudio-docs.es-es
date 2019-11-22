---
title: 'Layer Diagrams: Reference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
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
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd2b2d19e55cbaf9af63ddeafdbdf9f6d677c5bc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301612"
---
# <a name="layer-diagrams-reference"></a>Diagramas de capas: Referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can use a *layer diagram* to visualize the high-level, logical architecture of your system. A layer diagram organizes the physical artifacts in your system into logical, abstract groups called *layers*. Estas capas describen las tareas principales que realizan los artefactos o los componentes principales del sistema. Cada capa también puede contener capas anidadas que describen tareas más detalladas.

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Se pueden especificar las dependencias planeadas o existentes entre las capas. Estas dependencias, que se representan como flechas, indican qué capas pueden usar o usan actualmente la funcionalidad representada por otras capas. Al organizar el sistema en capas que describen roles y funciones distintos, un diagrama de capas le ayudará a entender, reutilizar y mantener el código más fácilmente.

 Use un diagrama de capas para realizar las siguientes tareas:

- Comunicar la arquitectura lógica existente o planeada del sistema.

- Detectar conflictos entre el código existente y la arquitectura planeada.

- Visualizar el impacto de los cambios en la arquitectura planeada al refactorizar, actualizar o desarrollar el sistema.

- Reforzar la arquitectura planeada durante el desarrollo y el mantenimiento del código incluyendo la validación en las operaciones de protección y compilación.

  En este tema se describen los elementos que puede usar en un diagrama de capas. For more detailed information about how to create and draw layer diagrams, see [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md). For more information about layering patterns, visit the [Patterns & Practices site](https://go.microsoft.com/fwlink/?LinkId=145794).

## <a name="reading-layer-diagrams"></a>Leer diagramas de capas
 ![Elements on layer diagrams](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")

 En la tabla siguiente se describen los elementos que puede usar en un diagrama de capas.

|**Shape**|**Element**|**Descripción**|
|---------------|-----------------|---------------------|
|1|**Layer**|Grupo lógico de artefactos físicos del sistema. Estos artefactos pueden ser espacios de nombres, proyectos, clases, métodos, etc.<br /><br /> To see the artifacts that are linked to a layer, open the shortcut menu for the layer, and then choose **View Links** to open **Layer Explorer**.<br /><br /> For more information, see [Layer Explorer](#Explorer).<br /><br /> -   **Forbidden Namespace Dependencies** - Specifies that artifacts associated with this layer cannot depend on the specified namespaces.<br />-   **Forbidden Namespaces** - Specifies that artifacts associated with this layer must not belong to the specified namespaces.<br />-   **Required Namespaces** - Specifies that artifacts associated with this layer must belong to one of the specified namespaces.|
|2|**Dependency**|Indica que una capa puede usar la funcionalidad de otra capa, pero no viceversa.<br /><br /> -   **Direction** - Specifies the direction of the dependency.|
|3|**Bidirectional Dependency**|Indica que una capa puede usar la funcionalidad de otra capa, y viceversa.<br /><br /> -   **Direction** - Specifies the direction of the dependency.|
|4|**Comentario**|Use esta opción para agregar notas generales al diagrama o elementos del diagrama.|
|5|**Comment Link**|Se usa para vincular comentarios a elementos del diagrama.|

## <a name="Explorer"></a> Layer Explorer
 Puede vincular cada capa a artefactos de la solución, como proyectos, clases, espacios de nombres, archivos de proyecto y otros elementos del software. El número de una capa muestra la cantidad de artefactos vinculados a ella. Sin embargo, cuando lea el número de artefactos de una capa, recuerde lo siguiente:

- Si una capa se vincula a un artefacto que contiene otros artefactos, pero no se vincula directamente a estos otros artefactos, el número incluye únicamente el artefacto vinculado. Sin embargo, los demás artefactos se incluyen para el análisis durante la validación de capas.

   Por ejemplo, si una capa está vinculada a un solo espacio de nombres, el número de artefactos vinculados es 1, aunque el espacio de nombres contenga clases. Si la capa tiene también vínculos a cada clase del espacio de nombres, el número incluirá las clases vinculadas.

- Si una capa contiene otras que están vinculadas a artefactos, la capa contenedora también está vinculada a esos artefactos, incluso aunque el número de la capa contenedora no los incluya.

  Para obtener más información sobre cómo vincular capas y artefactos, vea:

- [Diagrama de capas: instrucciones](../modeling/layer-diagrams-guidelines.md)

- [Crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)

#### <a name="to-examine-the-linked-artifacts"></a>Para examinar los artefactos vinculados

- On the layer diagram, open the shortcut menu for one or more layers, and then choose **View Links**.

     **Layer Explorer** opens and shows the artifacts that are linked to the selected layers. **Layer Explorer** has a column that shows each of the properties of the artifact links.

    > [!NOTE]
    > If you cannot see all of these properties, expand the **Layer Explorer** window.

    |**Column in Layer Explorer**|**Descripción**|
    |----------------------------------|---------------------|
    |**Categories**|Tipo de artefacto, como una clase, espacio de nombres, archivo de código fuente, etcétera|
    |**Layer**|Capa que se vincula al artefacto|
    |**Supports Validation**|If **True**, then the layer validation process can verify that the project conforms to dependencies to or from this element.<br /><br /> If **False**, then the link does not participate in the layer validation process.<br /><br /> For more information, see [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md).|
    |**Identificador**|Referencia al artefacto vinculado|

## <a name="see-also"></a>Vea también
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)
