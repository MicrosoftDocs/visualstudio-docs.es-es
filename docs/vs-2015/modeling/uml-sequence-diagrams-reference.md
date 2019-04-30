---
title: 'Diagramas de secuencia UML: Referencia de | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3990d43ae11db3db8eb792883ba62a030cde3a2f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548573"
---
# <a name="uml-sequence-diagrams-reference"></a>Diagramas de secuencia UML: Referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, un *diagrama de secuencia* muestra una interacción, que representa la secuencia de mensajes entre instancias de clases, componentes, subsistemas o actores. El tiempo fluye por el diagrama y muestra el flujo de control de un participante a otro. Utilice diagramas de secuencia para visualizar instancias y eventos, en lugar de clases y métodos. En el diagrama, puede aparecer más de una instancia del mismo tipo. También puede haber más de una ocurrencia del mismo mensaje.  
  
 Los diagramas de secuencia de UML forman parte de un modelo UML y solo existen en los proyectos de modelado UML. Para crear un diagrama de secuencia UML, en el **arquitectura** menú, haga clic en **nuevo UML o diagrama de capas**. Encontrará más información sobre cómo crear y dibujar [diagramas de secuencia UML](../modeling/uml-sequence-diagrams-guidelines.md) o [diagramas de modelado UML](../modeling/edit-uml-models-and-diagrams.md) en general.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="reading-sequence-diagrams"></a>Leer diagramas de secuencia  
 En la tabla siguiente se describen los elementos que puede ver en un diagrama de secuencia. Obtenga más información sobre estas [propiedades de los elementos](../modeling/properties-of-elements-on-uml-sequence-diagrams.md).  
  
 ![Partes de un diagrama de secuencia](../modeling/media/uml-sequence.png "UML_Sequence")  
  
|**Shape**|**Element**|**Descripción**|  
|---------------|-----------------|---------------------|  
|1|**Lifeline**|Línea vertical que representa la secuencia de eventos que se producen en un participante durante una interacción, mientras el tiempo avanza por la línea. Este participante puede ser una instancia de una clase, un componente o un actor.|  
|2|**Actor**|Participante externo al sistema que está desarrollando.<br /><br /> Puede realizar un símbolo de actor que aparecen en la parte superior de una línea de vida estableciendo su **Actor** propiedad.|  
|3|**Mensaje sincrónico**|El remitente espera una respuesta a un mensaje sincrónico antes de continuar. El diagrama muestra la llamada y la devolución. Los mensajes sincrónicos se usan para representar llamadas de función ordinarias dentro de un programa, así como otros tipos de mensaje que se comportan de la misma manera.|  
|4|**Mensaje asincrónico**|Mensaje que no requiere una respuesta para que el remitente continúe. Un mensaje asincrónico muestra solo una llamada del remitente. Se usa para representar la comunicación entre subprocesos diferentes o la creación de un nuevo subproceso.|  
|5|**Ocurrencia de ejecución**|Rectángulo sombreado vertical que aparece en la línea de vida de un participante y representa el período en el que el participante ejecuta una operación.<br /><br /> La ejecución empieza cuando el participante recibe un mensaje. Si el mensaje de inicio es un mensaje sincrónico, la ejecución finalizará con una flecha de retorno al remitente.|  
|6|**Mensaje de devolución de llamada**|Mensaje que se devuelve a un participante que espera la devolución de una llamada anterior. La ocurrencia de ejecución resultante aparece encima de la que ya existe.|  
|7|**Mensaje propio**|Mensaje de un participante a sí mismo. La ocurrencia de ejecución resultante aparece encima de la ejecución de envío.|  
|8|**Crear mensaje**|Mensaje que crea un participante. Si un participante recibe un mensaje de creación, este debe ser el primero que reciba.|  
|9|**Mensaje encontrado**|Mensaje asincrónico de un participante desconocido o no especificado.|  
|10|**Mensaje perdido**|Mensaje asincrónico a un participante desconocido o no especificado.|  
|11|**Comentario**|Se puede asociar un comentario a cualquier punto de una línea de vida.|  
|12|**Uso de interacción**|Contiene una secuencia de mensajes definidos en otro diagrama.<br /><br /> Para crear un **uso de interacción**, haga clic en la herramienta y, a continuación, arrastre las líneas de vida que desea incluir.|  
|13|**Fragmento combinado**|Colección de fragmentos. Cada fragmento puede incluir uno o varios mensajes. Hay varios tipos de fragmentos combinados. Para obtener más información, consulte [Describe el flujo de control con fragmentos de diagramas de secuencia UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Para crear un fragmento, haga clic en un mensaje, seleccione **rodear con**y, a continuación, haga clic en un tipo de fragmento.|  
|14|**Restricción de fragmentos**|Se puede usar para indicar una condición sobre si tendrá lugar el fragmento.<br /><br /> Para establecer la restricción, seleccione un fragmento y, después, seleccione la restricción y escriba un valor.|  
|**X**|**Evento de destrucción**|Representa el punto en el que el objeto se ha eliminado o ya no es accesible. Aparece en la parte inferior de cada línea de vida.|  
||**Interacción**|Colección de mensajes y líneas de vida que se muestra en el diagrama de secuencia. Para ver las propiedades de una interacción, debe seleccionarla en **Explorador de modelos UML**.|  
||**Diagrama de secuencia**|Diagrama que muestra una interacción. Para ver sus propiedades, haga clic en una parte vacía del diagrama. **Nota:**  Los nombres del diagrama de secuencia, la interacción que muestra y el archivo que incluye el diagrama pueden ser diferentes.|  
  
## <a name="see-also"></a>Vea también  
 [Diagramas de secuencia de UML: Directrices](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramas de casos de uso UML: Referencia](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrama de clases de UML: Referencia](../modeling/uml-class-diagrams-reference.md)   
 [Diagramas de componentes UML: Referencia](../modeling/uml-component-diagrams-reference.md)   
 [Diagramas de componentes UML: referencia](../modeling/uml-component-diagrams-reference.md)
