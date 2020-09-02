---
title: Diseñador de actividad Flowchart | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a85efea49d641fa54774c1428d15f7d8218ca53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656708"
---
# <a name="flowchart-activity-designer"></a>Diseñador de actividades Flowchart
La actividad <xref:System.Activities.Statements.Flowchart> se utiliza para crear flujos de trabajo que definen y administran los controles de flujo complejos. Una clase <xref:System.Activities.Statements.Flowchart> se puede crear en código o mediante [!INCLUDE[wfd2](../includes/wfd2-md.md)]. En este tema se documenta la experiencia de uso con [!INCLUDE[wfd2](../includes/wfd2-md.md)]. El diseñador de actividades de flujos de trabajo de [!INCLUDE[wfd1](../includes/wfd1-md.md)] permite a los desarrolladores de software crear flujos de trabajo de forma natural.

## <a name="the-flowchart-activity"></a>Actividad Flowchart
 La clase <xref:System.Activities.Statements.Flowchart> especifica una propiedad <xref:System.Activities.Statements.Flowchart.StartNode%2A> única que se ejecuta cuando el flujo de trabajo se inicia y utiliza una red de propiedades <xref:System.Activities.Statements.Flowchart.Nodes%2A> vinculadas para crear bucles arbitrarios o desviar el flujo de la ejecución hacia otro sitio en el flujo de trabajo en cualquier momento.

### <a name="using-the-flowchart-activity-designer"></a>Utilizar el diseñador de actividades Flowchart
 El diseñador de actividades **Flowchart** se puede encontrar en la categoría **Diagrama de flujo** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** de. [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **Flowchart** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie de, donde se coloquen normalmente los diseñadores de actividad, ya sea como una actividad raíz o como elemento secundario de otra actividad de flujo de control. Si el diseñador de actividades **Flowchart** se coloca en una [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie en blanco, crea una <xref:System.Activities.Statements.Flowchart> actividad que, de forma predeterminada, se presenta en una vista expandida en la que el nodo de inicio que inicia la ejecución se representa como una bola verde. Si el diseñador de actividades **Flowchart** se coloca en otra actividad de flujo de control, se presenta en una vista minimizada que se puede expandir haciendo doble clic en el diseñador de actividades **Flowchart** . Cualquier actividad del **cuadro de herramientas** se puede arrastrar directamente al diseñador de actividad **Flowchart** , incluidas otras actividades de flujo de control.

 Después de arrastrar varios diseñadores de actividades hasta el lienzo de [!INCLUDE[wfd2](../includes/wfd2-md.md)], los objetos <xref:System.Activities.Activity> que representan se pueden vincular entre sí para especificar el orden de ejecución. Para crear un vínculo entre una actividad de origen y una actividad de destino, desplace el mouse sobre el diseñador de la actividad de origen y de los identificadores cuadrados que aparecen a ambos lados de la misma. Haga clic en uno de los identificadores cuadrados y arrástrelo manteniendo presionado el botón del mouse hasta uno de los identificadores que aparecen de forma similar rodeando la actividad de destino cuando se mantiene el mouse sobre ella. Suelte el botón del mouse y se creará un vínculo entre ambas actividades que quedará representado como una flecha desde diseñador de origen hasta el diseñador de destino.

### <a name="flowchart-activity-properties"></a>Propiedades de la actividad Flowchart
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Flowchart> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica el nombre para mostrar del diseñador de actividades en el encabezado. El valor predeterminado es Flowchart. El valor se puede editar en la ventana **propiedades** o directamente en el encabezado del diseñador de actividad.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|Falso|La colección de variables que se aplican a esta clase <xref:System.Activities.Statements.Flowchart> para compartir el estado entre sus actividades secundarias.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|Falso|La clase <xref:System.Activities.Statements.FlowNode> que se ejecuta cuando se inicia la clase <xref:System.Activities.Statements.Flowchart>.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|Falso|Contiene la colección de objetos <xref:System.Activities.Statements.FlowNode> en la clase <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Consulte también
 [Flowchart](../workflow-designer/flowchart-activity-designers.md) [FlowDecision](../workflow-designer/flowdecision-activity-designer.md) [FlowSwitch \<T> ](../workflow-designer/flowswitch-t-activity-designer.md)