---
title: Propiedades de elementos de diagramas de actividades UML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.activitydiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
- activity diagrams, properties
ms.assetid: 9849d45e-65d5-46bd-a319-757e90b7c748
caps.latest.revision: 19
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: c9f2830f66ad7f79a49b096bb489b542124efe6e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269998"
---
# <a name="properties-of-elements-on-uml-activity-diagrams"></a>Propiedades de los elementos de diagramas de actividades UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de actividades UML, cada elemento del diagrama tiene propiedades. Para ver las propiedades de un elemento, haga clic en el elemento en el diagrama o en **Explorador de modelos UML** y, a continuación, haga clic en **propiedades**. Las propiedades aparecen en la **propiedades** ventana.  
  
> [!NOTE]
>  Este tema trata sobre las propiedades de los elementos de los diagramas de actividades UML. Para obtener información sobre cómo leer diagramas de actividades UML, vea [diagramas de actividades UML: referencia](../modeling/uml-activity-diagrams-reference.md). Para obtener más información sobre cómo dibujar diagramas de actividades UML, vea [diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Propiedades de los elementos  
  
|Propiedad|Predeterminado|Elemento|Descripción|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Nombre predeterminado|Todo|Identifica el elemento.|  
|**Nombre completo**|Package :: Name|Todo|Identifica el elemento de forma única. Prefijo con el nombre completo del paquete que lo contiene.|  
|**Los elementos de trabajo**|0 asociados|Todo|Número de elementos de trabajo asociados a este elemento. Para asociar elementos de trabajo, consulte [vincular elementos de modelo y los elementos de trabajo](../modeling/link-model-elements-and-work-items.md).|  
|**Descripción**|(ninguno)|Todo|Aquí puede realizar anotaciones generales sobre el elemento.|  
|**Color**|(valor predeterminado para el tipo)|Todo|Color de la forma.|  
|**Cuerpo**|(ninguno)|Acción|Especifica la acción en detalle.|  
|**Idioma**|(ninguno)|Acción|Idioma de la expresión en Body.|  
|**Local Postconditions**|(ninguno)|Action, Send, Accept, Call Behavior, Call Operation|Restricciones que deben cumplirse cuando finaliza la ejecución. Objetivo alcanzado por la acción.|  
|**Local Preconditions**|(ninguno)|Action, Send, Accept, Call Behavior, Call Operation|Restricciones que deben cumplirse antes de que comience la ejecución.|  
|**Es sincrónico**|True|Call Behavior, Call Operation|-Si es true, la acción espera hasta que finaliza la actividad.|  
|**Comportamiento**|(ninguno)|Comportamiento de llamada|-La actividad invocada.|  
|**Operación**|(ninguno)|Call Operation|-La operación invocada.|  
|**Es resolver referencia**|False|Accept Event|-Si es true, puede haber varios output PIN tipados y datos se deserializan en ellos. Si es false, todos los datos aparecen en un pin.|  
|**Límite superior**|**\***|Object Node, Activity Parameter|**0** indica que los datos deben pasar directamente a lo largo del flujo.<br /><br /> **\*** indica que se pueden almacenar datos en el flujo.|  
|**Selección**|(ninguno)|Object Node, Activity Parameter, Input Pin, Output Pin, Object Flow|Invoca un proceso que filtra los datos. Este proceso puede definirse en otro diagrama.|  
|**Ordenación**|(ninguno)|Object Node, Activity Parameter, Input Pin, Output Pin|-Cómo varios tokens se almacenan.|  
|**Es el Control**|False|Input Pin, Output Pin|-Si es true, el flujo de este pin es un flujo de control. Si es false, es un flujo de objeto.|  
|**Type**|(ninguno)|Input Pin, Output Pin, Object Node, Activity Parameter|-El tipo de objetos que se transmiten.<br />-El tipo puede ser un tipo primitivo como Integer, o un clasificador definido en otro lugar en el modelo. Si escribe el nombre de un tipo que no está definido, aparecerá en el **tipos sin especificar** sección del explorador de modelos UML.|  
|**Multiplicidad**|1|Input Pin, Output Pin|-Puede ser un valor único o un intervalo `[n..m]`.<br />-Límite inferior de `n` -la acción no se puede iniciar (para un input pin) o detener (para un output pin) hasta que no haya `n` objetos esperando en el pin.<br />-Límite superior de `m` -la acción no puede usar ni producir más de `m` objetos en una ejecución. * significa que no hay límite.|  
|**transformación**|(ninguno)|Flujo de objetos|-Se invoca un proceso que transforma los datos. Este proceso puede definirse en otro diagrama.|  
|**Es de multidifusión**|False|Flujo de objetos|: Indica que puede haber varios componentes u objetos de destinatario.|  
|**Es MultiReceive**|False|Flujo de objetos|: Indica que puede haber varios componentes u objetos de destinatario.|  
|**Is Single Execution**|False|Diagrama de actividades|-If true, hay a lo sumo una ejecución de este diagrama a la vez.|  
  
## <a name="see-also"></a>Vea también  
 [Diagramas de actividades UML: referencia](../modeling/uml-activity-diagrams-reference.md)   
 [Diagramas de actividades UML: instrucciones](../modeling/uml-activity-diagrams-guidelines.md)



