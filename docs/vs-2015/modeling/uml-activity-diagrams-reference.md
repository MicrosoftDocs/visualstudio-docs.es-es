---
title: 'Diagramas de actividades UML: referencia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 960e9469290bca42abd252d497c2ce72e62e41a4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531539"
---
# <a name="uml-activity-diagrams-reference"></a>Diagramas de actividades UML: Referencia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *Diagrama de actividades* muestra un proceso de negocio o un proceso de software como un flujo de trabajo a través de una serie de acciones. Las personas, los componentes de software o los equipos pueden realizar estas acciones.

 Puede usar un diagrama de actividades para describir procesos de varios tipos, como los ejemplos siguientes:

- Un proceso de negocio o un flujo de trabajo entre los usuarios y el sistema. Para obtener más información, vea [requisitos de usuario de modelo](../modeling/model-user-requirements.md).

- Los pasos que se realizan en un caso de uso. Para obtener más información, vea [diagramas de casos de uso de UML: instrucciones](../modeling/uml-use-case-diagrams-guidelines.md).

- Un protocolo de software, es decir, las secuencias de interacciones entre componentes permitidas.

- Un algoritmo de software.

  En este tema se describen los elementos que puede usar en los diagramas de actividades. Para obtener más información sobre los diagramas de actividades de dibujo, vea [diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md). Para crear un diagrama de actividades UML, en el menú **arquitectura** , haga clic en **nuevo diagrama de UML o de capas**. Para obtener más información sobre cómo dibujar diagramas de modelado en general, vea [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-activity-diagrams"></a>Leer diagramas de actividades
 En las tablas de las secciones siguientes se describen los elementos que puede usar en un diagrama de actividades y sus propiedades principales. Para obtener una lista completa de las propiedades de los elementos, vea [propiedades de los elementos de los diagramas de actividades UML](../modeling/properties-of-elements-on-uml-activity-diagrams.md).

 Las acciones y otros elementos que aparecen en un diagrama de actividades conforman una actividad. Puede ver la actividad en el Explorador de modelos UML. Se crea cuando se agrega el primer elemento al diagrama.

 Para leer un diagrama, imagine que un token o un subproceso de control pasa por los conectores de una acción a la siguiente.

### <a name="simple-control-flows"></a>Flujos de control simple
 Puede mostrar una secuencia de acciones con bifurcaciones y bucles. Para obtener más información sobre cómo usar los elementos que se describen aquí, vea la sección Descripción del flujo de control del tema [diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md).

 ![Flujo de control simple](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")

|**Forma**|**Element**|**Descripción y propiedades principales**|
|-|-|-|
|1|**Acción**|Paso de la actividad en el que los usuarios o el software realizan alguna tarea.<br /><br /> La acción se puede iniciar cuando un token llega a todos sus flujos entrantes. Cuando termina, los tokens se envían en todos los flujos salientes.<br /><br /> -   **Cuerpo** : especifica la acción en detalle.<br />-   **Language** : el idioma de la expresión en Body.<br />-   **Condiciones posteriores locales** : restricciones que deben satisfacerse cuando finaliza la ejecución. Objetivo alcanzado por la acción.<br />-   **Condiciones previas locales** : restricciones que deben cumplirse antes de que empiece la ejecución.|
|2|**Flujo de control**|Conector que muestra el flujo de control entre las acciones. Para interpretar el diagrama, imagine que un token fluye de una acción a la siguiente.<br /><br /> Para crear un flujo de control, use la herramienta **conector** .|
|3|**Initial Node**|Indica la primera acción o las primeras acciones de la actividad. Cuando se inicia la actividad, un token fluye desde el nodo inicial.|
|4|**Activity Final Node**|Fin de la actividad. Cuando llega un token, la actividad finaliza.|
|5|**Decision Node**|Bifurcación condicional de un flujo. Tiene una entrada y dos o más salidas. Un token entrante solo emerge en una de las salidas.|
|6|**Proteja**|Condición que especifica si un token puede fluir por un conector. Se usa con más frecuencia en los flujos salientes de un nodo de decisión.<br /><br /> Para establecer una protección, haga clic con el botón derecho en un flujo, haga clic en **propiedades** y, a continuación, establezca la propiedad **Guard** .|
|7|**Merge Node**|Necesario para combinar los flujos que se dividieron mediante un nodo de decisión. Tiene dos o más entradas y una salida. Un token en cualquier entrada emerge en la salida.|
|8|**Comment**|Proporciona información adicional sobre los elementos a los que está vinculado.|
|9|**Call Behavior Action**|Acción que se define con más detalle en otro diagrama de actividades.<br /><br /> -   **IsSynchronous** : si es true, la acción espera hasta que la actividad finaliza.<br />-   **Behavior** : la actividad invocada.|
|(no se muestra)|**Call Operation Action**|Acción que llama a una operación en una instancia de una clase.|
||**Actividad**|Flujo de trabajo que se representa mediante un diagrama de actividades. Para ver las propiedades de una actividad, debe seleccionarla en el **Explorador de modelos UML**.<br /><br /> -   **Es de solo lectura** : si es true, la actividad no debe cambiar el estado de ningún objeto.<br />-   **Es una ejecución única** : si es true, hay como máximo una ejecución de este diagrama a la vez.|
||**Diagrama de actividades UML**|Diagrama que muestra una actividad. Para ver sus propiedades, haga clic en una parte vacía del diagrama. **Nota:**  Los nombres del diagrama de actividades, el archivo que contiene el diagrama y la actividad que muestra el diagrama pueden ser diferentes.|

### <a name="concurrent-flows"></a>Flujos simultáneos
 Puede describir secuencias de acciones que se ejecutan al mismo tiempo. Para más información, vea Dibujar flujos simultáneos.

 ![Diagrama de actividades mostrando flujo simultáneo](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")

|**Forma**|**Element**|**Descripción**|
|-|-|-|
|11|**Fork Node**|Divide un único flujo en flujos simultáneos. Cada token entrante genera un token en cada conector saliente.|
|12|**Join Node**|Combina flujos simultáneos en un único flujo. Cuando cada flujo entrante tiene un token en espera, se genera un token en la salida.|
|13|**Send Signal Action**|Acción que envía un mensaje o una señal a otra actividad o a un subproceso simultáneo de la misma actividad. El tipo y el contenido del mensaje están implícitos en el título de la acción o se especifican en los comentarios adicionales.<br /><br /> La acción puede enviar datos de la señal, que se pueden pasar a la acción de un flujo de objeto o terminal de entrada (16).|
|14|**Accept Event Action**|Acción que espera un mensaje o una señal antes de continuar con la acción. El tipo de mensaje que la acción puede recibir está implícito en el título o se especifica en los comentarios adicionales.<br /><br /> Si la acción no tiene ningún flujo de control entrante, genera un token cada vez que recibe un mensaje.<br /><br /> La acción puede recibir datos de la señal, que se pueden pasar a un flujo de objeto o terminal de salida (17).<br /><br /> -   **IsUnmarshall** : si es true, puede haber varios PIN de salida con tipo y los datos no se aplican a la serialización. Si es false, todos los datos aparecen en un terminal.|

### <a name="data-flows"></a><a name="DataFlow"></a>Flujos de datos
 Puede describir el flujo de datos de una acción a otra. Para más información sobre los elementos que se usan en esta sección, vea la sección Dibujar flujos de datos del tema Instrucciones para dibujar un diagrama de actividades.

 ![Diagrama de actividades mostrando flujo de datos](../modeling/media/uml-actovdata.png "UML_ActOvData")

|**Forma**|**Element**|**Descripción**|
|-|-|-|
|15|**Nodo de objeto**|Representa los datos que pasan por un flujo.<br /><br /> -   **Ordenación** : cómo se almacenan varios tokens.<br />-   **Selection** : invoca un proceso, que se puede definir en otro diagrama, que filtra los datos.<br />-   **Límite superior** : 0 indica que los datos deben pasar directamente a lo largo del flujo; \*indica que los datos se pueden almacenar en el flujo.<br />-   **Type** : el tipo de objetos almacenados y transmitidos.|
|16|**Input Pin**|Representa los datos que puede recibir una acción cuando se ejecuta.<br /><br /> -   **Type** : el tipo de objetos transmitidos.|
|17|**Output Pin**|Representa los datos que genera una acción cuando se ejecuta.<br /><br /> -   **Type** : el tipo de objetos transmitidos.|
|18|**Activity Parameter Node**|Nodo de objeto a través del cual la actividad recibe o genera datos.<br /><br /> Se usa cuando la actividad representada en el diagrama se llama desde otra actividad, o bien cuando el diagrama describe una operación o función.<br /><br /> -   **Type** : el tipo de objetos transmitidos.|
|(no se muestra)|**Flujo de objetos**|Conector que muestra el flujo de datos entre las acciones y los nodos de objeto.<br /><br /> Para crear un flujo de objeto, use la herramienta **conector** para vincular un terminal de entrada o salida o un nodo de objeto a otro elemento.<br /><br /> -   **Selection** : invoca un proceso, que se puede definir en otro diagrama, que filtra los datos.<br />-   **Transformación** : invoca un proceso, que se puede definir en otro diagrama, que transforma los datos.<br />-   **IsMulticast** : indica que puede haber varios objetos o componentes de destinatario.<br />-   **IsMultiReceive** : indica que se pueden recibir entradas de varios objetos o componentes.|

## <a name="see-also"></a>Consulte también
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md) [diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md)
