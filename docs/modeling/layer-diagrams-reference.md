---
title: 'Diagramas de dependencia: Referencia | Documentos de Microsoft'
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
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 33
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 74829877befa9f48988d42e04a58e2a418e7d82b
ms.lasthandoff: 02/22/2017

---
# <a name="dependency-diagrams-reference"></a>Diagramas de dependencia: referencia
En Visual Studio, puede utilizar un *diagrama de dependencia* para visualizar la arquitectura lógica de alto nivel del sistema. Un diagrama de dependencia organiza los artefactos físicos del sistema en grupos lógicos abstractos denominados *capas*. Estas capas describen las tareas principales que realizan los artefactos o los componentes principales del sistema. Cada capa también puede contener capas anidadas que describen tareas más detalladas.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, consulte [compatibilidad con la versión de arquitectura y herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Se pueden especificar las dependencias planeadas o existentes entre las capas. Estas dependencias, que se representan como flechas, indican qué capas pueden usar o usan actualmente la funcionalidad representada por otras capas. Al organizar el sistema en capas que describen los distintos roles y funciones, un diagrama de dependencia le resultará más fácil entender, reutilizar y mantener el código.  
  
 Utilice un diagrama de dependencia para ayudarle a realizar las tareas siguientes:  
  
-   Comunicar la arquitectura lógica existente o planeada del sistema.  
  
-   Detectar conflictos entre el código existente y la arquitectura planeada.  
  
-   Visualizar el impacto de los cambios en la arquitectura planeada al refactorizar, actualizar o desarrollar el sistema.  
  
-   Reforzar la arquitectura planeada durante el desarrollo y el mantenimiento del código incluyendo la validación en las operaciones de protección y compilación.  
  
 En este tema se describe los elementos que puede usar en un diagrama de dependencia. Para obtener más información acerca de cómo crear y dibujar diagramas de dependencia, vea [diagramas de dependencia: directrices](../modeling/layer-diagrams-guidelines.md). Para obtener más información acerca de los patrones de capas, visite la [sitio de modelos y prácticas aspecto](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
## <a name="reading-dependency-diagrams"></a>Leer diagramas de dependencia  
 ![Elementos de diagramas de dependencia](~/docs/modeling/media/uml_layerrefreading.png "UML_LayerRefReading")  
  
 En la tabla siguiente describe los elementos que puede usar en un diagrama de dependencia.  
  
|**Forma**|**Elemento**|**Descripción**|  
|---------------|-----------------|---------------------|  
|1|**Capa**|Grupo lógico de artefactos físicos del sistema. Estos artefactos pueden ser espacios de nombres, proyectos, clases, métodos, etc.<br /><br /> Para ver los artefactos que están vinculados a una capa, abra el menú contextual para la capa y, a continuación, elija **ver vínculos** para abrir **Explorador de capas**.<br /><br /> Para obtener más información, consulte [Explorador de capas](#Explorer).<br /><br /> -   **Forbidden Namespace dependencias** -especifica qué artefactos asociados a esta capa no pueden depender de los espacios de nombres especificados.<br />-   **Espacios de nombres prohibidos** -especifica que los artefactos asociados a esta capa no deben pertenecer a los espacios de nombres especificados.<br />-   **Espacios de nombres requeridos** -especifica que los artefactos asociados a esta capa deben pertenecer a uno de los espacios de nombres especificados.|  
|2|**Dependencia**|Indica que una capa puede usar la funcionalidad de otra capa, pero no viceversa.<br /><br /> -   **Dirección** -especifica la dirección de la dependencia.|  
|3|**Dependencia bidireccional**|Indica que una capa puede usar la funcionalidad de otra capa, y viceversa.<br /><br /> -   **Dirección** -especifica la dirección de la dependencia.|  
|4|**Comentario**|Use esta opción para agregar notas generales al diagrama o elementos del diagrama.|  
|5|**Vínculo de comentario**|Se usa para vincular comentarios a elementos del diagrama.|  
  
##  <a name="a-nameexplorera-layer-explorer"></a><a name="Explorer"></a>Explorador de capas  
 Puede vincular cada capa a artefactos de la solución, como proyectos, clases, espacios de nombres, archivos de proyecto y otros elementos del software. El número de una capa muestra el número de artefactos vinculados a ella. Sin embargo, cuando lea el número de artefactos de una capa, recuerde lo siguiente:  
  
-   Si una capa se vincula a un artefacto que contiene otros artefactos, pero no se vincula directamente a estos otros artefactos, el número incluye únicamente el artefacto vinculado. Sin embargo, los demás artefactos se incluyen para el análisis durante la validación de capas.  
  
     Por ejemplo, si una capa está vinculada a un solo espacio de nombres, el número de artefactos vinculados es 1, aunque el espacio de nombres contenga clases. Si la capa tiene también vínculos a cada clase del espacio de nombres, el número incluirá las clases vinculadas.  
  
-   Si una capa contiene otras que están vinculadas a artefactos, la capa contenedora también está vinculada a esos artefactos, incluso aunque el número de la capa contenedora no los incluya.  
  
 Para obtener más información sobre cómo vincular capas y artefactos, vea:  
  
-   [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)  
  
-   [Crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>Para examinar los artefactos vinculados  
  
-   En el diagrama de dependencia, abra el menú contextual para una o varias capas y, a continuación, elija **ver vínculos**.  
  
     **Explorador de capas** se abre y muestra los artefactos que están vinculados a las capas seleccionadas. **Explorador de capas** tiene una columna que muestra cada una de las propiedades de los vínculos de artefacto.  
  
    > [!NOTE]
    >  Si no puede ver todas estas propiedades, expanda el **Explorador de capas** ventana.  
  
    |**Columna en el Explorador de capas**|**Descripción**|  
    |----------------------------------|---------------------|  
    |**Categorías**|Tipo de artefacto, como una clase, espacio de nombres, archivo de código fuente, etcétera|  
    |**Capa**|Capa que se vincula al artefacto|  
    |**Admite validación**|Si **True**, a continuación, el proceso de validación de capas puede comprobar que el proyecto se ajusta a las dependencias a o desde este elemento.<br /><br /> Si **False**, a continuación, el vínculo no participa en el proceso de validación de capas.<br /><br /> Para obtener más información, consulte [diagramas de dependencia: directrices](../modeling/layer-diagrams-guidelines.md).|  
    |**Identificador**|Referencia al artefacto vinculado|  
  
## <a name="see-also"></a>Vea también  
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)

