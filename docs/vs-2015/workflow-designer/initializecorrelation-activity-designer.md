---
title: Diseñador de actividades InitializeCorrelation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 145b67574169696771f4102b29e9dc8f6a9d1575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659023"
---
# <a name="initializecorrelation-activity-designer"></a>Diseñador de actividades InitializeCorrelation
El diseñador de actividades **InitializeCorrelation** se utiliza para crear y configurar una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> que se usa para establecer una correlación entre los mensajes antes de enviarlos o recibirlos.

## <a name="the-initializecorrelation-activity"></a>Actividad InitializeCorrelation
 Una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> se utiliza para inicializar las correlaciones sin enviar o recibir un mensaje. Normalmente una correlación se inicializa cuando se envía o recibe un mensaje. Si se debe establecer una correlación antes de enviar o recibir un mensaje, utilice <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar la correlación.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizar el diseñador de actividades InitializeCorrelation
 El diseñador de actividades **InitializeCorrelation** se puede encontrar en la categoría **Mensajería** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** del [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione **barra de herramientas** en la **vista.** menú o Ctrl + Alt + X).

 El diseñador de actividades **InitializeCorrelation** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Esto crea una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> con un <xref:System.Activities.Activity.DisplayName%2A> predeterminado de InitializeCorrelation. el <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **InitializeCorrelation** o en el cuadro **displayName** de la ventana **propiedades** .

 El <xref:System.ServiceModel.Activities.CorrelationHandle> se puede especificar en el campo **correlación** de la ventana **propiedades** en la superficie del diseñador de actividades **InitializeCorrelation** .

 Hacer clic en el botón de puntos suspensivos además del campo **CorrelationData** en la ventana **propiedades** o en la vista "ver..." texto de sugerencia en la superficie del diseñador de actividades **InitializeCorrelation** muestra el cuadro de diálogo **inicializar correlación** , en el que puede especificar el identificador de correlación y los pares clave-valor que se usan para inicializarlos. [!INCLUDE[crabout](../includes/crabout-md.md)] usar este cuadro de diálogo, vea el tema del [cuadro de diálogo Editor de colección de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Propiedades InitializeCorrelation
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.InitializeCorrelation> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la ventana **propiedades** o en [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie.

|Nombre de la propiedad|Requerido|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.InitializeCorrelation>. El valor predeterminado es InitializeCorrelation.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> se utiliza para asociar las actividades de flujo de trabajo en la correlación.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Un diccionario de datos de correlación que relaciona los mensajes con la instancia de flujo de trabajo.<br /><br /> Utilice el cuadro de diálogo **inicializar correlación** para configurar el <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] el cuadro de diálogo usar este, vea el tema del [cuadro de diálogo Editor de colección de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Vea también
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [send](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)