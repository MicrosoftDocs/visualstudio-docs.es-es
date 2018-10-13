---
title: 'Diagramas de componentes UML: Referencia | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.componentdiagram.diagram
- vs.teamarch.componentdiagram.toolbox
- vs.teamarch.UMLModelExplorer.componentdiagram
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 5eddff6a-892a-4c3c-9278-687ac1eccc50
caps.latest.revision: 38
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b99188aa069a830d17e31733ad20b0ae727d63f9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206746"
---
# <a name="uml-component-diagrams-reference"></a>Diagramas de componentes de UML: Referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, un *diagrama de componentes* muestra las partes de un diseño de un sistema de software. Un diagrama de componentes permite visualizar la estructura de alto nivel del sistema y el comportamiento del servicio que estos componentes proporcionan y usan a través de interfaces. Para crear un diagrama de componentes UML, en el **arquitectura** menú, haga clic en **nuevo UML o diagrama de capas**.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Puede usar un diagrama de componentes para describir un diseño que está implementado en cualquier idioma o estilo. Solo es necesario identificar los elementos del diseño que interactúan con las otros elementos del diseño a través de un conjunto restringido de entradas y salidas. Los componentes pueden ser de cualquier escala y pueden estar interconectados de cualquier manera.  
  
 Para obtener más información sobre cómo usar diagramas de componentes en el proceso de diseño, vea [modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md).  
  
> [!NOTE]
>  En este tema se describen los elementos que puede usar en los diagramas de componentes. Para obtener más información sobre cómo dibujar diagramas de componentes detallada vea [diagramas de componentes UML: instrucciones](../modeling/uml-component-diagrams-guidelines.md). Para obtener más información sobre cómo dibujar diagramas de modelado en general, consulte [modelos y diagramas UML editar](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-component-diagrams"></a>Lectura de diagramas de componentes  
 En la tabla siguiente se describen los elementos que puede usar en un diagrama de componentes, junto con sus propiedades principales. Para obtener una lista completa de las propiedades de los elementos, vea [propiedades de elementos en diagramas de componentes UML](../modeling/properties-of-elements-on-uml-component-diagrams.md).  
  
 ![Elementos que se usan en los diagramas de componentes](../modeling/media/uml-compovreading.png "UML_CompOvReading")  
  
|**Forma**|**Element**|**Descripción y propiedades principales**|  
|---------------|-----------------|-----------------------------------------|  
|1|**Componente**|Un fragmento reutilizable de funcionalidad del sistema. Un componente proporciona y consume el comportamiento a través de interfaces y puede usar otros componentes.<br /><br /> Puede ocultar o mostrar los elementos internos de un componente mediante el control Expandir y contraer (9).<br /><br /> Un componente es un tipo de clase.<br /><br /> -   **Is Indirectly Instantiated**. Si es true (valor predeterminado), el componente solo existe como artefacto de diseño. En tiempo de ejecución, solo existen sus partes.|  
|2|**Puerto de interfaz proporcionada**|Representa un grupo de mensajes o llamadas que implementa un componente y que pueden usar otros componentes o sistemas externos. Un puerto es una propiedad de un componente que tiene una interfaz como su tipo.|  
|3|**Puerto de interfaz necesaria**|Representa un grupo de mensajes o llamadas que envía el componente a otros componentes o sistemas externos. El componente está diseñado para acoplarse a componentes que proporcionan al menos estas operaciones. El puerto tiene una interfaz como su tipo.|  
|4|**dependencia**|Se puede usar para indicar que una interfaz necesaria en un componente se puede satisfacer mediante una interfaz proporcionada en otro.<br /><br /> Las dependencias también se pueden usar de manera más general entre los elementos del modelo para mostrar que el diseño de uno depende del diseño del otro.|  
|5|**Parte**|Un atributo de un componente, cuyo tipo suele ser otro componente. Un elemento se usa en el diseño interno de su componente primario. Los elementos se muestran gráficamente, anidados dentro del componente primario.<br /><br /> Para crear un elemento de un tipo de componente existente, arrastre el componente desde el Explorador de modelos UML hasta el componente propietario.<br /><br /> Para crear un elemento de un nuevo tipo, haga clic en el **componente** de la herramienta y, a continuación, haga clic en el componente propietario.<br /><br /> Por ejemplo, un componente `Car` tiene los elementos `engine:CarEngine`, `backLeft:Wheel`, `frontRight:Wheel`, etc.<br /><br /> Más de un elemento puede tener el mismo tipo y componentes diferentes pueden tener elementos del mismo tipo.<br /><br /> -   **Tipo**. El tipo del elemento, que se define en otra parte del modelo. Normalmente, el tipo es otro componente.<br />-   **Multiplicidad**. El valor predeterminado es 1. Puede establecerlo en **de 0.. 1** para indicar que el elemento puede tener el valor **null**, **\*** para indicar que el elemento es una colección de instancias del tipo especificado, o para cualquier expresión que pueda evaluarse como un intervalo de números.|  
|6|**Ensamblado de elemento**|Una conexión entre los puertos de la interfaz necesaria de un elemento y los puertos de la interfaz proporcionada de otro elemento. La implementación de un ensamblado de elementos puede variar de un componente a otro. Los elementos conectados deben tener el mismo componente primario.|  
|7|**Delegación**|Vincula un puerto a una interfaz de uno de los elementos del componente. Indica que los mensajes enviados al componente son administrados por el elemento o que los mensajes enviados desde el elemento se envían desde el componente primario.|  
|(sin mostrar)|**Generalización**|Indica que un componente hereda de otro componente. Los elementos y las interfaces se heredan.|  
|9|Control Contraer o expandir|Úselo para mostrar u ocultar los elementos internos de un componente.|  
|(sin mostrar)|**Comentario**|Para obtener notas adicionales. Puede vincular un comentario a cualquier número de elementos del diagrama mediante el uso de la **conector** herramienta.|  
  
## <a name="see-also"></a>Vea también  
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramas de componentes UML: instrucciones](../modeling/uml-component-diagrams-guidelines.md)   
 [Validar el sistema durante el desarrollo](../modeling/validate-your-system-during-development.md)   
 [Diagramas de casos de uso UML: referencia](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramas de clases UML: referencia](../modeling/uml-class-diagrams-reference.md)   
 [Diagramas de actividades UML: referencia](../modeling/uml-activity-diagrams-reference.md)   
 [Diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md)



