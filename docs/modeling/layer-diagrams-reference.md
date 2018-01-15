---
title: 'Diagramas de dependencia: Hacer referencia | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d11e02e9218d86e0e971c685ab496a2b85b2be21
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="dependency-diagrams-reference"></a>Diagramas de dependencia: referencia
En Visual Studio, puede usar un *diagrama de dependencia* para visualizar la arquitectura lógica de alto nivel del sistema. Un diagrama de dependencia organiza los artefactos físicos en el sistema en grupos lógicos y abstractos denominados *capas*. Estas capas describen las tareas principales que realizan los artefactos o los componentes principales del sistema. Cada capa también puede contener capas anidadas que describen tareas más detalladas.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Se pueden especificar las dependencias planeadas o existentes entre las capas. Estas dependencias, que se representan como flechas, indican qué capas pueden usar o usan actualmente la funcionalidad representada por otras capas. El sistema se organizan en capas que se describen los distintos roles y funciones, un diagrama de dependencia puede ayudar a que sea más fácil para que pueda entender y mantener el código.  
  
 Utilizar un diagrama de dependencia para ayudarle a realizar las tareas siguientes:  
  
-   Comunicar la arquitectura lógica existente o planeada del sistema.  
  
-   Detectar conflictos entre el código existente y la arquitectura planeada.  
  
-   Visualizar el impacto de los cambios en la arquitectura planeada al refactorizar, actualizar o desarrollar el sistema.  
  
-   Reforzar la arquitectura planeada durante el desarrollo y el mantenimiento del código incluyendo la validación en las operaciones de protección y compilación.  
  
 En este tema se describe los elementos que puede usar en un diagrama de dependencia. Para obtener más información acerca de cómo crear y dibujar diagramas de dependencia, vea [diagramas de dependencia: directrices](../modeling/layer-diagrams-guidelines.md). Para obtener más información acerca de los patrones de capas, visite la [sitio Patterns & Practices](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
## <a name="reading-dependency-diagrams"></a>Leer diagramas de dependencia  
 ![Elementos de diagramas de dependencia](../modeling/media/uml_layerrefreading.png "UML_LayerRefReading")  
  
 La tabla siguiente describen los elementos que puede usar en un diagrama de dependencia.  
  
|**Forma**|**Element**|**Descripción**|  
|---------------|-----------------|---------------------|  
|1|**Capa**|Grupo lógico de artefactos físicos del sistema. Estos artefactos pueden ser espacios de nombres, proyectos, clases, métodos, etc.<br /><br /> Para ver los artefactos que están vinculados a una capa, abra el menú contextual de la capa y, a continuación, elija **ver vínculos** para abrir **Explorador de capas**.<br /><br /> Para obtener más información, consulte [Explorador de capas](#Explorer).<br /><br /> -   **Prohibido Namespace dependencias** -especifica qué artefactos asociados a esta capa no pueden depender de los espacios de nombres especificados.<br />-   **Prohibido espacios de nombres** -especifica qué artefactos asociados a esta capa no deben pertenecer a los espacios de nombres especificados.<br />-   **Requiere los espacios de nombres** -especifica qué artefactos asociados a esta capa deben pertenecer a uno de los espacios de nombres especificados.|  
|2|**Dependencia**|Indica que una capa puede usar la funcionalidad de otra capa, pero no viceversa.<br /><br /> -   **Dirección** -especifica la dirección de la dependencia.|  
|3|**Dependencia bidireccional**|Indica que una capa puede usar la funcionalidad de otra capa, y viceversa.<br /><br /> -   **Dirección** -especifica la dirección de la dependencia.|  
|4|**Comentario**|Use esta opción para agregar notas generales al diagrama o elementos del diagrama.|  
|5|**Vínculo de comentario**|Se usa para vincular comentarios a elementos del diagrama.|  
  
##  <a name="Explorer"></a>Explorador de capas  
 Puede vincular cada capa a artefactos de la solución, como proyectos, clases, espacios de nombres, archivos de proyecto y otros elementos del software. El número de una capa muestra el número de artefactos vinculados a ella. Sin embargo, cuando lea el número de artefactos de una capa, recuerde lo siguiente:  
  
-   Si una capa se vincula a un artefacto que contiene otros artefactos, pero no se vincula directamente a estos otros artefactos, el número incluye únicamente el artefacto vinculado. Sin embargo, los demás artefactos se incluyen para el análisis durante la validación de capas.  
  
     Por ejemplo, si una capa está vinculada a un solo espacio de nombres, el número de artefactos vinculados es 1, aunque el espacio de nombres contenga clases. Si la capa tiene también vínculos a cada clase del espacio de nombres, el número incluirá las clases vinculadas.  
  
-   Si una capa contiene otras que están vinculadas a artefactos, la capa contenedora también está vinculada a esos artefactos, incluso aunque el número de la capa contenedora no los incluya.  
  
 Para obtener más información sobre cómo vincular capas y artefactos, vea:  
  
-   [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)  
  
-   [Creación de diagramas de dependencia a partir del código](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>Para examinar los artefactos vinculados  
  
-   En el diagrama de dependencia, abra el menú contextual para una o varias capas y, a continuación, elija **ver vínculos**.  
  
     **Explorador de capas** se abre y muestra los artefactos que están vinculados a las capas seleccionadas. **Explorador de capas** tiene una columna que muestra cada una de las propiedades de los vínculos de artefacto.  
  
    > [!NOTE]
    >  Si no ve todas estas propiedades, expanda el **Explorador de capas** ventana.  
  
    |**Columna en el Explorador de capas**|**Descripción**|  
    |----------------------------------|---------------------|  
    |**Categorías**|Tipo de artefacto, como una clase, espacio de nombres, archivo de código fuente, etcétera|  
    |**Capa**|Capa que se vincula al artefacto|  
    |**Admite la validación**|Si **True**, a continuación, el proceso de validación de capas puede comprobar que el proyecto se ajusta a las dependencias a o desde este elemento.<br /><br /> Si **False**, a continuación, el vínculo no participa en el proceso de validación de capas.<br /><br /> Para obtener más información, consulte [diagramas de dependencia: directrices](../modeling/layer-diagrams-guidelines.md).|  
    |**Identificador**|Referencia al artefacto vinculado|  
  
## <a name="see-also"></a>Vea también  
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)
