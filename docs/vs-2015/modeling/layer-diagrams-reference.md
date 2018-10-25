---
title: 'Diagramas de capas: Referencia | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b1136cc4e55ebbdf3a5ff1b38b5802b058e9c69c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895748"
---
# <a name="layer-diagrams-reference"></a>Diagramas de capas: Referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede usar un *diagrama de capas* para visualizar la arquitectura lógica de alto nivel del sistema. Un diagrama de capas organiza los artefactos físicos del sistema en grupos lógicos abstractos, denominados *capas*. Estas capas describen las tareas principales que realizan los artefactos o los componentes principales del sistema. Cada capa también puede contener capas anidadas que describen tareas más detalladas.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Se pueden especificar las dependencias planeadas o existentes entre las capas. Estas dependencias, que se representan como flechas, indican qué capas pueden usar o usan actualmente la funcionalidad representada por otras capas. Al organizar el sistema en capas que describen roles y funciones distintos, un diagrama de capas le ayudará a entender, reutilizar y mantener el código más fácilmente.  
  
 Use un diagrama de capas para realizar las siguientes tareas:  
  
- Comunicar la arquitectura lógica existente o planeada del sistema.  
  
- Detectar conflictos entre el código existente y la arquitectura planeada.  
  
- Visualizar el impacto de los cambios en la arquitectura planeada al refactorizar, actualizar o desarrollar el sistema.  
  
- Reforzar la arquitectura planeada durante el desarrollo y el mantenimiento del código incluyendo la validación en las operaciones de protección y compilación.  
  
  En este tema se describen los elementos que puede usar en un diagrama de capas. Para obtener más información acerca de cómo crear y dibujar diagramas de capas, vea [diagramas de capas: instrucciones](../modeling/layer-diagrams-guidelines.md). Para obtener más información sobre los patrones de capas, visite la [sitio Patterns & Practices](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
## <a name="reading-layer-diagrams"></a>Leer diagramas de capas  
 ![Los elementos de diagramas de capas](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")  
  
 En la tabla siguiente se describen los elementos que puede usar en un diagrama de capas.  
  
|**Forma**|**Element**|**Descripción**|  
|---------------|-----------------|---------------------|  
|1|**Capa**|Grupo lógico de artefactos físicos del sistema. Estos artefactos pueden ser espacios de nombres, proyectos, clases, métodos, etc.<br /><br /> Para ver los artefactos que están vinculados a una capa, abra el menú contextual para la capa y, a continuación, elija **ver vínculos** para abrir **Explorador de capas**.<br /><br /> Para obtener más información, consulte [Explorador de capas](#Explorer).<br /><br /> -   **Forbidden Namespace dependencias** : Especifica que los artefactos asociados a esta capa no pueden depender de los espacios de nombres especificado.<br />-   **Espacios de nombres prohibidos** : Especifica que los artefactos asociados a esta capa no deben pertenecer a los espacios de nombres especificado.<br />-   **Espacios de nombres requeridos** : Especifica que los artefactos asociados a esta capa deben pertenecer a uno de los espacios de nombres especificado.|  
|2|**dependencia**|Indica que una capa puede usar la funcionalidad de otra capa, pero no viceversa.<br /><br /> -   **Dirección** -especifica la dirección de la dependencia.|  
|3|**Dependencia bidireccional**|Indica que una capa puede usar la funcionalidad de otra capa, y viceversa.<br /><br /> -   **Dirección** -especifica la dirección de la dependencia.|  
|4|**Comentario**|Use esta opción para agregar notas generales al diagrama o elementos del diagrama.|  
|5|**Vínculo de comentario**|Se usa para vincular comentarios a elementos del diagrama.|  
  
##  <a name="Explorer"></a> Explorador de capas  
 Puede vincular cada capa a artefactos de la solución, como proyectos, clases, espacios de nombres, archivos de proyecto y otros elementos del software. El número de una capa muestra el número de artefactos vinculados a ella. Sin embargo, cuando lea el número de artefactos de una capa, recuerde lo siguiente:  
  
- Si una capa se vincula a un artefacto que contiene otros artefactos, pero no se vincula directamente a estos otros artefactos, el número incluye únicamente el artefacto vinculado. Sin embargo, los demás artefactos se incluyen para el análisis durante la validación de capas.  
  
   Por ejemplo, si una capa está vinculada a un solo espacio de nombres, el número de artefactos vinculados es 1, aunque el espacio de nombres contenga clases. Si la capa tiene también vínculos a cada clase del espacio de nombres, el número incluirá las clases vinculadas.  
  
- Si una capa contiene otras que están vinculadas a artefactos, la capa contenedora también está vinculada a esos artefactos, incluso aunque el número de la capa contenedora no los incluya.  
  
  Para obtener más información sobre cómo vincular capas y artefactos, vea:  
  
- [Diagrama de capas: instrucciones](../modeling/layer-diagrams-guidelines.md)  
  
- [Crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>Para examinar los artefactos vinculados  
  
-   En el diagrama de capas, abra el menú contextual para uno o más capas y, a continuación, elija **ver vínculos**.  
  
     **Explorador de capas** se abre y muestra los artefactos que están vinculados a las capas seleccionadas. **Explorador de capas** tiene una columna que muestra cada una de las propiedades de los vínculos de artefacto.  
  
    > [!NOTE]
    >  Si no ve todas estas propiedades, expanda el **Explorador de capas** ventana.  
  
    |**Columna en el Explorador de capas**|**Descripción**|  
    |----------------------------------|---------------------|  
    |**Categorías**|Tipo de artefacto, como una clase, espacio de nombres, archivo de código fuente, etcétera|  
    |**Capa**|Capa que se vincula al artefacto|  
    |**Admite la validación**|Si **True**, a continuación, el proceso de validación de capas puede comprobar que el proyecto se ajusta a las dependencias a o desde este elemento.<br /><br /> Si **False**, a continuación, el vínculo no participa en el proceso de validación de capas.<br /><br /> Para obtener más información, consulte [diagramas de capas: instrucciones](../modeling/layer-diagrams-guidelines.md).|  
    |**Identificador**|Referencia al artefacto vinculado|  
  
## <a name="see-also"></a>Vea también  
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)



