---
title: "Diseñador de actividades Pick | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: ab9ef5504b8785e31446d51f517e8ac41c27d579
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="pick-activity-designer"></a>Diseñador de actividades Pick
La actividad <xref:System.Activities.Statements.Pick> proporciona un flujo de control basado en eventos. La actividad ejecuta una de las diversas bifurcaciones en respuesta a un evento desencadenador.  
  
## <a name="the-pick-activity"></a>Actividad Pick  
 Una actividad <xref:System.Activities.Statements.Pick> contiene una colección de objetos <xref:System.Activities.Statements.PickBranch>, uno de los cuales puede ejecutar la actividad <xref:System.Activities.Statements.Pick> a causa de algún evento de entrada que actúa como un desencadenador. De esta forma, [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] proporciona un modelado de flujo de control basado en eventos. Cada clase <xref:System.Activities.Statements.PickBranch> contiene una propiedad <xref:System.Activities.Statements.PickBranch.Trigger%2A> y una propiedad <xref:System.Activities.Statements.PickBranch.Action%2A>. Al principio de un <xref:System.Activities.Statements.Pick> ejecución de la actividad, todas las actividades de desencadenador de la <xref:System.Activities.Statements.PickBranch> se programan elementos. Cuando se completa la primera actividad, se programa la actividad de acción correspondiente y el resto de actividades de desencadenador se cancelan.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Usar el diseñador de actividad Pick  
 El **elegir** Diseñador de actividad puede encontrarse en el **flujo de Control** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **elegir** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde actividad se coloquen normalmente los diseñadores, por ejemplo dentro de un  **Secuencia** Diseñador de actividad. Después de colocarlo en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], crea una actividad <xref:System.Activities.Statements.Pick> que, de forma predeterminada, contiene dos actividades <xref:System.Activities.Statements.PickBranch> vacías como elementos, con los nombres para mostrar Branch1 y Branch2. Los respectivos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valores de propiedad se pueden editar en el **PickBranch** encabezado del Diseñador de actividad o en la **propiedades** ventana para cada bifurcación.  
  
 Hay dos maneras de agregar <xref:System.Activities.Statements.PickBranch> actividades a la colección de un <xref:System.Activities.Statements.Pick> objeto: arrastrando y colocando el **PickBranch** diseñador desde el **cuadro de herramientas** o mediante el menú contextual de en el **elegir** superficie de diseño. Para obtener más información, consulte el [PickBranch](../workflow-designer/pickbranch-activity-designer.md) tema. Observe que el único elemento que se puede colocar dentro de un **elegir** Diseñador de actividad es un **PickBranch** Diseñador de actividad.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad Pick en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Pick> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.Pick> en el encabezado. El valor predeterminado es Pick. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
  
## <a name="see-also"></a>Vea también  
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)   
 [Actividad Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [Uso de la actividad Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)