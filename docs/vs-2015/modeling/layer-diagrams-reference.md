---
title: 'Diagramas de capas: referencia | Microsoft Docs'
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
ms.openlocfilehash: 448a74b739bbb339d5f3b3e56c0ba59072994109
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850614"
---
# <a name="layer-diagrams-reference"></a>Diagramas de capas: Referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede usar un *Diagrama de capas* para visualizar la arquitectura lógica de alto nivel del sistema. Un diagrama de capas organiza los artefactos físicos del sistema en grupos lógicos abstractos denominados *capas*. Estas capas describen las tareas principales que realizan los artefactos o los componentes principales del sistema. Cada capa también puede contener capas anidadas que describen tareas más detalladas.

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Se pueden especificar las dependencias planeadas o existentes entre las capas. Estas dependencias, que se representan como flechas, indican qué capas pueden usar o usan actualmente la funcionalidad representada por otras capas. Al organizar el sistema en capas que describen roles y funciones distintos, un diagrama de capas le ayudará a entender, reutilizar y mantener el código más fácilmente.

 Use un diagrama de capas para realizar las siguientes tareas:

- Comunicar la arquitectura lógica existente o planeada del sistema.

- Detectar conflictos entre el código existente y la arquitectura planeada.

- Visualizar el impacto de los cambios en la arquitectura planeada al refactorizar, actualizar o desarrollar el sistema.

- Reforzar la arquitectura planeada durante el desarrollo y el mantenimiento del código incluyendo la validación en las operaciones de protección y compilación.

  En este tema se describen los elementos que puede usar en un diagrama de capas. Para obtener información más detallada sobre cómo crear y dibujar diagramas de capas, vea [diagramas de capas: instrucciones](../modeling/layer-diagrams-guidelines.md). Para obtener más información sobre los patrones de capas, visite el [sitio patterns & Practices](https://apparch.codeplex.com/Wiki/View.aspx?title=Application Patterns&referringTitle=Home).

## <a name="reading-layer-diagrams"></a>Leer diagramas de capas
 ![Elementos en diagramas de capas](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")

 En la tabla siguiente se describen los elementos que puede usar en un diagrama de capas.

|**Forma**|**Element**|**Descripción**|
|---------------|-----------------|---------------------|
|1|**Nivel**|Grupo lógico de artefactos físicos del sistema. Estos artefactos pueden ser espacios de nombres, proyectos, clases, métodos, etc.<br /><br /> Para ver los artefactos que están vinculados a una capa, abra el menú contextual de la capa y, a continuación, elija **ver vínculos** para abrir el **Explorador de capas**.<br /><br /> Para obtener más información, vea [Explorador de capas](#Explorer).<br /><br /> -   **Dependencias de espacios de nombres prohibidos** : especifica que los artefactos asociados a esta capa no pueden depender de los espacios de nombres especificados.<br />-   **Espacios de nombres prohibidos** : especifica que los artefactos asociados a esta capa no deben pertenecer a los espacios de nombres especificados.<br />-   **Espacios de nombres necesarios** : especifica que los artefactos asociados a esta capa deben pertenecer a uno de los espacios de nombres especificados.|
|2|**Dependencia**|Indica que una capa puede usar la funcionalidad de otra capa, pero no viceversa.<br /><br /> -   **Direction** : especifica la dirección de la dependencia.|
|3|**Dependencia bidireccional**|Indica que una capa puede usar la funcionalidad de otra capa, y viceversa.<br /><br /> -   **Direction** : especifica la dirección de la dependencia.|
|4|**Comment**|Use esta opción para agregar notas generales al diagrama o elementos del diagrama.|
|5|**Vínculo de comentario**|Se usa para vincular comentarios a elementos del diagrama.|

## <a name="layer-explorer"></a><a name="Explorer"></a> Explorador de capas
 Puede vincular cada capa a artefactos de la solución, como proyectos, clases, espacios de nombres, archivos de proyecto y otros elementos del software. El número de una capa muestra la cantidad de artefactos vinculados a ella. Sin embargo, cuando lea el número de artefactos de una capa, recuerde lo siguiente:

- Si una capa se vincula a un artefacto que contiene otros artefactos, pero no se vincula directamente a estos otros artefactos, el número incluye únicamente el artefacto vinculado. Sin embargo, los demás artefactos se incluyen para el análisis durante la validación de capas.

   Por ejemplo, si una capa está vinculada a un solo espacio de nombres, el número de artefactos vinculados es 1, aunque el espacio de nombres contenga clases. Si la capa tiene también vínculos a cada clase del espacio de nombres, el número incluirá las clases vinculadas.

- Si una capa contiene otras que están vinculadas a artefactos, la capa contenedora también está vinculada a esos artefactos, incluso aunque el número de la capa contenedora no los incluya.

  Para obtener más información sobre cómo vincular capas y artefactos, vea:

- [Diagrama de capas: instrucciones](../modeling/layer-diagrams-guidelines.md)

- [Crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)

#### <a name="to-examine-the-linked-artifacts"></a>Para examinar los artefactos vinculados

- En el diagrama de capas, abra el menú contextual de una o varias capas y, a continuación, elija **ver vínculos**.

     El **Explorador de capas** se abre y muestra los artefactos que están vinculados a las capas seleccionadas. El **Explorador de capas** tiene una columna que muestra cada una de las propiedades de los vínculos de artefacto.

    > [!NOTE]
    > Si no puede ver todas estas propiedades, expanda la ventana **Explorador de capas** .

    |**Columna del Explorador de capas**|**Descripción**|
    |----------------------------------|---------------------|
    |**Categorías**|Tipo de artefacto, como una clase, espacio de nombres, archivo de código fuente, etcétera|
    |**Nivel**|Capa que se vincula al artefacto|
    |**Admite validación**|Si **es true**, el proceso de validación de capas puede comprobar que el proyecto se ajusta a las dependencias de este elemento o de este.<br /><br /> Si **es false**, el vínculo no participa en el proceso de validación de capas.<br /><br /> Para obtener más información, vea [diagramas de capas: instrucciones](../modeling/layer-diagrams-guidelines.md).|
    |**Identificador**|Referencia al artefacto vinculado|

## <a name="see-also"></a>Consulte también
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)
