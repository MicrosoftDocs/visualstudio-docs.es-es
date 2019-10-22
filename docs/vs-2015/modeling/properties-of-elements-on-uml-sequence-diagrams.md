---
title: Propiedades de los elementos de diagramas de secuencia UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4d0753ea7396c9f21addcbb01ab7b90be066356a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671429"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Propiedades de los elementos de diagramas de secuencia de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de secuencia UML, cada elemento del diagrama tiene propiedades. Para ver las propiedades de un elemento, haga clic con el botón secundario en el elemento del diagrama o en el **Explorador de modelos UML** y, a continuación, haga clic en **propiedades**. Las propiedades aparecen en la ventana **propiedades** .

> [!NOTE]
> Este tema trata sobre las propiedades de los elementos de los diagramas de secuencia UML. Para obtener más información sobre cómo leer diagramas de secuencia UML, vea [diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md). Si quiere más información sobre cómo diseñar diagramas de secuencia UML, vea [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Propiedades de los elementos

|Propiedad.|Predeterminado|Elemento|Descripción|
|--------------|-------------|-------------|-----------------|
|**Nombre**|Nombre predeterminado|Todas|Identifica el elemento.|
|**Nombre completo**|Package :: Name|Todas|Identifica de forma única el elemento. Prefijo con el nombre completo del paquete que lo contiene.|
|**Elementos de trabajo**|0 asociados|Todas|Número de elementos de trabajo asociados a este elemento. Para asociar elementos de trabajo, vea [vincular elementos de modelo y elementos de trabajo](../modeling/link-model-elements-and-work-items.md).|
|**Descripción**|(en blanco)|Todas|Aquí puede realizar anotaciones generales sobre el elemento.|
|**Color**|(valor predeterminado para el tipo de elemento)|Línea de vida, mensaje|Color de la forma. Se trata de una propiedad de la forma, no del elemento que muestra.|
|**ype**|(en blanco)|Lifeline|El tipo de la instancia que representa la línea de vida.<br /><br /> Si hay un símbolo de referencia que se muestra en el encabezado de la línea de vida, esta clase o interfaz existe por separado en el Explorador de modelos UML y puede aparecer en un diagrama de clases.|
|**Agente**|False|Lifeline|Indica si la línea de vida representa un componente de usuario, dispositivo o software que es externo al componente al que hace referencia el diagrama.|
|**Tipo**|**Complete** : un mensaje que tiene el remitente y el receptor.<br /><br /> **Found** : un mensaje que tiene un remitente sin especificar.<br /><br /> **Perdido** : mensaje que tiene un receptor no especificado.|Mensaje|Indica qué extremos de un mensaje están unidos a una línea de vida.<br /><br /> Esta propiedad no se puede cambiar. Se establece cuando se crea el mensaje.|
|**Clasificación**|**AsynchCall** : un mensaje asincrónico.<br /><br /> **SynchCall** : un mensaje sincrónico.<br /><br /> **Reply** : la parte devuelta de un mensaje sincrónico.<br /><br /> **CreateMessage** : un mensaje de creación de instancia.|Mensaje|El tipo de mensaje. Esta propiedad no se puede cambiar. Viene determinado por la herramienta que usa para crear el mensaje.|
|**Sesión**|(vacío)|Mensaje|Un método llamado por el mensaje en la línea de vida receptora.<br /><br /> Sólo está visible si la línea de vida receptora está vinculada a una interfaz o una clase.|
|**Hace referencia a**|Diagrama de secuencia|Interaction Use|Diagrama de secuencia llamado por uso de interacción.|
|**Operador de interacción**|Se establece cuando se usa el comando **rodear con**|Fragmento combinado|Operador representado por este fragmento o colección de fragmentos.|
|**Proteja**|(vacío)|Operando de interacción de un fragmento combinado|La secuencia del fragmento no a menos que la restricción sea true.<br /><br /> Para seleccionar el fragmento superior de cualquier fragmento combinado, haga clic debajo del título del fragmento.|
|**Mín., máx.**|(sin restricción)|Fragmento combinado de bucle|El número mínimo y máximo de veces que se ejecuta el bucle.|
|**Mensajes**|(vacío)|Tener en cuenta y<br /><br /> omitir fragmentos combinados|Los mensajes que se tienen en cuenta o se omiten en este fragmento.|

## <a name="see-also"></a>Vea también
 [Diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md) [diagramas de secuencia UML: instrucciones](../modeling/uml-sequence-diagrams-guidelines.md) [describe el flujo de control con fragmentos en diagramas de secuencia UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)
