---
title: 'Diagramas de actividades UML: Referencia | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.activitydiagram.diagram
- vs.teamarch.activitydiagram.toolbox
- vs.teamarch.UMLModelExplorer.activitydiagram
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
- behaviors, UML
ms.assetid: 07efcd17-2a96-4052-9957-6dcccbb725ee
caps.latest.revision: 50
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: bfe4eaad401ce61534e5785ed82b9e33fa2f6610
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567438"
---
# <a name="uml-activity-diagrams-reference"></a>Diagramas de actividades UML: Referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [diagramas de actividades UML: referencia](https://docs.microsoft.com/visualstudio/modeling/uml-activity-diagrams-reference).  
  
Un *diagrama de actividades* muestra un proceso empresarial o un proceso de software como un flujo de trabajo a través de una serie de acciones. Las personas, los componentes de software o los equipos pueden realizar estas acciones.  
  
 Puede usar un diagrama de actividades para describir procesos de varios tipos, como los ejemplos siguientes:  
  
-   Un proceso de negocio o un flujo de trabajo entre los usuarios y el sistema. Para obtener más información, consulte [modelar los requisitos del usuario](../modeling/model-user-requirements.md).  
  
-   Los pasos que se realizan en un caso de uso. Para obtener más información, consulte [diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md).  
  
-   Un protocolo de software, es decir, las secuencias de interacciones entre componentes permitidas.  
  
-   Un algoritmo de software.  
  
 En este tema se describen los elementos que puede usar en los diagramas de actividades. Para obtener más información detallada sobre la actividad de dibujo Vea diagramas [diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md). Para crear un diagrama de actividades UML, en el **arquitectura** menú, haga clic en **nuevo UML o diagrama de capas**. Para obtener más información sobre cómo dibujar diagramas de modelado en general, consulte [modelos y diagramas UML editar](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-activity-diagrams"></a>Leer diagramas de actividades  
 En las tablas de las secciones siguientes se describen los elementos que puede usar en un diagrama de actividades y sus propiedades principales. Para obtener una lista completa de las propiedades de los elementos, vea [propiedades de elementos de diagramas de actividades UML](../modeling/properties-of-elements-on-uml-activity-diagrams.md).  
  
 Las acciones y otros elementos que aparecen en un diagrama de actividades conforman una actividad. Puede ver la actividad en el Explorador de modelos UML. Se crea cuando se agrega el primer elemento al diagrama.  
  
 Para leer un diagrama, imagine que un token o un subproceso de control pasa por los conectores de una acción a la siguiente.  
  
### <a name="simple-control-flows"></a>Flujos de control simple  
 Puede mostrar una secuencia de acciones con bifurcaciones y bucles. Para obtener más información sobre cómo usar los elementos que se describen aquí, consulte la sección Describir el flujo de Control del tema [diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Un flujo de control simple](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")  
  
||||  
|-|-|-|  
|**Forma**|**Element**|**Descripción y propiedades principales**|  
|1|**Acción**|Paso de la actividad en el que los usuarios o el software realizan alguna tarea.<br /><br /> La acción se puede iniciar cuando un token llega a todos sus flujos entrantes. Cuando termina, los tokens se envían en todos los flujos salientes.<br /><br /> -   **Cuerpo** -especifica la acción en detalle.<br />-   **Lenguaje** -el idioma de la expresión de cuerpo.<br />-   **Local Postconditions** -las restricciones que deben cumplirse cuando finaliza la ejecución. Objetivo alcanzado por la acción.<br />-   **Local Preconditions** -las restricciones que deben cumplirse antes de que comience la ejecución.|  
|2|**Flujo de control**|Conector que muestra el flujo de control entre las acciones. Para interpretar el diagrama, imagine que un token fluye de una acción a la siguiente.<br /><br /> Para crear un flujo de control, use el **conector** herramienta.|  
|3|**Nodo inicial**|Indica la primera acción o las primeras acciones de la actividad. Cuando se inicia la actividad, un token fluye desde el nodo inicial.|  
|4|**Nodo Final de actividad**|Fin de la actividad. Cuando llega un token, la actividad finaliza.|  
|5|**Nodo de decisión**|Bifurcación condicional de un flujo. Tiene una entrada y dos o más salidas. Un token entrante solo emerge en una de las salidas.|  
|6|**Guard**|Condición que especifica si un token puede fluir por un conector. Se usa con más frecuencia en los flujos salientes de un nodo de decisión.<br /><br /> Para establecer una restricción, haga clic en un flujo, haga clic en **propiedades** y, a continuación, establezca el **protegerse** propiedad.|  
|7|**Mezcla de nodo**|Necesario para combinar los flujos que se dividieron mediante un nodo de decisión. Tiene dos o más entradas y una salida. Un token en cualquier entrada emerge en la salida.|  
|8|**Comentario**|Proporciona información adicional sobre los elementos a los que está vinculado.|  
|9|**Acción de llamada a comportamiento**|Acción que se define con más detalle en otro diagrama de actividades.<br /><br /> -   **IsSynchronous** : si es true, la acción espera hasta que finaliza la actividad.<br />-   **Comportamiento** : actividad invocada.|  
|(sin mostrar)|**Acción de operación de llamada**|Acción que llama a una operación en una instancia de una clase.|  
||**Actividad**|Flujo de trabajo que se representa mediante un diagrama de actividades. Para ver las propiedades de una actividad, debe seleccionarla en **Explorador de modelos UML**.<br /><br /> -   **Es de sólo lectura** : si es true, la actividad no debería cambiar el estado de cualquier objeto.<br />-   **Is Single Execution** : si es true, hay a lo sumo una ejecución de este diagrama a la vez.|  
||**Diagrama de actividades UML**|Diagrama que muestra una actividad. Para ver sus propiedades, haga clic en una parte vacía del diagrama. **Nota:** los nombres del diagrama de actividad, el archivo que contiene el diagrama y la actividad que se muestra en el diagrama puede ser diferente.|  
  
### <a name="concurrent-flows"></a>Flujos simultáneos  
 Puede describir secuencias de acciones que se ejecutan al mismo tiempo. Para más información, vea Dibujar flujos simultáneos.  
  
 ![Diagrama de actividades mostrando flujo simultáneo](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")  
  
||||  
|-|-|-|  
|**Forma**|**Element**|**Descripción**|  
|11|**Nodo de bifurcación**|Divide un único flujo en flujos simultáneos. Cada token entrante genera un token en cada conector saliente.|  
|12|**Únase a nodo**|Combina flujos simultáneos en un único flujo. Cuando cada flujo entrante tiene un token en espera, se genera un token en la salida.|  
|13|**Enviar acción de señal**|Acción que envía un mensaje o una señal a otra actividad o a un subproceso simultáneo de la misma actividad. El tipo y el contenido del mensaje están implícitos en el título de la acción o se especifican en los comentarios adicionales.<br /><br /> La acción puede enviar datos de la señal, que se pueden pasar a la acción de un flujo de objeto o terminal de entrada (16).|  
|14|**Acepte la acción de evento**|Acción que espera un mensaje o una señal antes de continuar con la acción. El tipo de mensaje que la acción puede recibir está implícito en el título o se especifica en los comentarios adicionales.<br /><br /> Si la acción no tiene ningún flujo de control entrante, genera un token cada vez que recibe un mensaje.<br /><br /> La acción puede recibir datos de la señal, que se pueden pasar a un flujo de objeto o terminal de salida (17).<br /><br /> -   **IsUnmarshall** : si es true, puede haber varios output PIN tipados y datos se deserializan en ellos. Si es false, todos los datos aparecen en un terminal.|  
  
###  <a name="DataFlow"></a> Flujos de datos  
 Puede describir el flujo de datos de una acción a otra. Para más información sobre los elementos que se usan en esta sección, vea la sección Dibujar flujos de datos del tema Instrucciones para dibujar un diagrama de actividades.  
  
 ![Diagrama de actividades mostrando flujo de datos](../modeling/media/uml-actovdata.png "UML_ActOvData")  
  
||||  
|-|-|-|  
|**Forma**|**Element**|**Descripción**|  
|15|**Nodo de objeto**|Representa los datos que pasan por un flujo.<br /><br /> -   **Ordenación** : cómo se almacenan varios tokens.<br />-   **Selección** -invoca un proceso que se puede definir en otro diagrama, que filtra los datos.<br />-   **Límite superior** -0 indica que los datos deben pasar directamente a lo largo del flujo; \* indica que se pueden almacenar datos en el flujo.<br />-   **Tipo** -el tipo de objetos se almacenan y se transmiten.|  
|16|**Entrada de Pin**|Representa los datos que puede recibir una acción cuando se ejecuta.<br /><br /> -   **Tipo** -el tipo de objetos que se transmiten.|  
|17|**Terminal de salida**|Representa los datos que genera una acción cuando se ejecuta.<br /><br /> -   **Tipo** -el tipo de objetos que se transmiten.|  
|18|**Nodo de parámetros de actividad**|Nodo de objeto a través del cual la actividad recibe o genera datos.<br /><br /> Se usa cuando la actividad representada en el diagrama se llama desde otra actividad, o bien cuando el diagrama describe una operación o función.<br /><br /> -   **Tipo** -el tipo de objetos que se transmiten.|  
|(sin mostrar)|**Flujo de objeto**|Conector que muestra el flujo de datos entre las acciones y los nodos de objeto.<br /><br /> Para crear un flujo de objeto, utilice el **conector** herramienta para vincular una entrada o Terminal de salida o un nodo de objeto a otro elemento.<br /><br /> -   **Selección** -invoca un proceso que se puede definir en otro diagrama, que filtra los datos.<br />-   **Transformación** -invoca un proceso que se puede definir en otro diagrama, que transforma los datos.<br />-   **IsMulticast** -indica que puede haber varios componentes u objetos de destinatario.<br />-   **IsMultiReceive** -indica que pueden recibirse entradas de varios componentes u objetos.|  
  
## <a name="see-also"></a>Vea también  
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md)



