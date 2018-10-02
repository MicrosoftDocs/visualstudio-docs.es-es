---
title: Diagramas de secuencia de propiedades de elementos de UML | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b1f83999f3859583c4429ff3bf19482f01d90546
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565764"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Propiedades de los elementos de diagramas de secuencia de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [diagramas de secuencia de propiedades de elementos de UML](https://docs.microsoft.com/visualstudio/modeling/properties-of-elements-on-uml-sequence-diagrams).  
  
En un diagrama de secuencia UML, cada elemento del diagrama tiene propiedades. Para ver las propiedades de un elemento, haga clic en el elemento en el diagrama o en **Explorador de modelos UML** y, a continuación, haga clic en **propiedades**. Las propiedades aparecen en la **propiedades** ventana.  
  
> [!NOTE]
>  Este tema trata sobre las propiedades de los elementos de los diagramas de secuencia UML. Para obtener más información sobre cómo leer diagramas de secuencia UML, vea [diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md). Para obtener más información sobre cómo dibujar diagramas de secuencia UML, vea [diagramas de secuencia UML: instrucciones](../modeling/uml-sequence-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Propiedades de los elementos  
  
|Propiedad|Predeterminado|Elemento|Descripción|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Nombre predeterminado|Todo|Identifica el elemento.|  
|**Nombre completo**|Package :: Name|Todo|Identifica el elemento de forma única. Prefijo con el nombre completo del paquete que lo contiene.|  
|**Los elementos de trabajo**|0 asociados|Todo|Número de elementos de trabajo asociados a este elemento. Para asociar elementos de trabajo, consulte [vincular elementos de modelo y los elementos de trabajo](../modeling/link-model-elements-and-work-items.md).|  
|**Descripción**|(en blanco)|Todo|Aquí puede realizar anotaciones generales sobre el elemento.|  
|**Color**|(valor predeterminado para el tipo de elemento)|Línea de vida, mensaje|Color de la forma. Se trata de una propiedad de la forma, no del elemento que muestra.|  
|**Type**|(en blanco)|Lifeline|El tipo de la instancia que representa la línea de vida.<br /><br /> Si hay un símbolo de referencia que se muestra en el encabezado de la línea de vida, esta clase o interfaz existe por separado en el Explorador de modelos UML y puede aparecer en un diagrama de clases.|  
|**actor**|False|Lifeline|Indica si la línea de vida representa un componente de usuario, dispositivo o software que es externo al componente al que hace referencia el diagrama.|  
|**Tipo**|**Completa** -un mensaje con remitente y receptor.<br /><br /> **Se encontró** -un mensaje que tiene un remitente no especificado.<br /><br /> **Perdido** -un mensaje que tiene un destinatario no especificado.|Mensaje|Indica qué extremos de un mensaje están unidos a una línea de vida.<br /><br /> Esta propiedad no se puede cambiar. Se establece cuando se crea el mensaje.|  
|**Ordenación**|**AsynchCall** -un mensaje asincrónico.<br /><br /> **SynchCall** -un mensaje sincrónico.<br /><br /> **Respuesta** -elemento devuelto de un mensaje sincrónico.<br /><br /> **CreateMessage** -creación de una mensaje de instancia.|Mensaje|El tipo de mensaje. Esta propiedad no se puede cambiar. Viene determinado por la herramienta que usa para crear el mensaje.|  
|**Operación**|(vacío)|Mensaje|Un método llamado por el mensaje en la línea de vida receptora.<br /><br /> Sólo está visible si la línea de vida receptora está vinculada a una interfaz o una clase.|  
|**Hace referencia a**|Diagrama de secuencia|Interaction Use|Diagrama de secuencia llamado por uso de interacción.|  
|**Operador de interacción**|Establece cuando se utiliza el **rodear con** comando|Fragmento combinado|Operador representado por este fragmento o colección de fragmentos.|  
|**Guard**|(vacío)|Operando de interacción de un fragmento combinado|La secuencia del fragmento no a menos que la restricción sea true.<br /><br /> Para seleccionar el fragmento superior de cualquier fragmento combinado, haga clic debajo del título del fragmento.|  
|**Mín., máx.**|(sin restricción)|Fragmento combinado de bucle|El número mínimo y máximo de veces que se ejecuta el bucle.|  
|**Mensajes**|(vacío)|Tener en cuenta y<br /><br /> omitir fragmentos combinados|Los mensajes que se tienen en cuenta o se omiten en este fragmento.|  
  
## <a name="see-also"></a>Vea también  
 [Diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramas de secuencia UML: instrucciones](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Describir el flujo de control con fragmentos de diagramas de secuencia de UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)



