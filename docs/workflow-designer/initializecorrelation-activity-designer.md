---
title: Diseñador de actividades Diseñador de flujo de trabajo-InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aadb526e50351c8344c8b265dca3364637d1ff0c
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875571"
---
# <a name="initializecorrelation-activity-designer"></a>Diseñador de actividades InitializeCorrelation

El diseñador de actividades **InitializeCorrelation** se utiliza para crear y configurar una <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad. La <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad establece una correlación entre los mensajes antes de enviarlos o recibirlos.

## <a name="the-initializecorrelation-activity"></a>Actividad InitializeCorrelation

Una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> se utiliza para inicializar las correlaciones sin enviar o recibir un mensaje. Normalmente una correlación se inicializa cuando se envía o recibe un mensaje. Si se debe establecer una correlación antes de enviar o recibir un mensaje, utilice <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar la correlación.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizar el diseñador de actividades InitializeCorrelation

Acceda al diseñador de actividades **InitializeCorrelation** en la categoría **Mensajería** del **cuadro de herramientas**.

El diseñador de actividades **InitializeCorrelation** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo. Al quitar el diseñador de actividad, se crea una <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de InitializeCorrelation. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **InitializeCorrelation** o en el cuadro **displayName** de la ventana **propiedades** .

<xref:System.ServiceModel.Activities.CorrelationHandle>Se puede especificar en el campo **correlación** de la ventana **propiedades** en la superficie del diseñador de actividades **InitializeCorrelation** .

Para mostrar el cuadro de diálogo **inicializar correlación** donde puede especificar el identificador de correlación y los pares clave-valor que se usan para inicializarlos, seleccione el botón de puntos suspensivos junto al campo **CorrelationData** en la ventana **propiedades** . O bien, seleccione la "vista..." texto de sugerencia en la superficie del diseñador de actividades **InitializeCorrelation** . Para obtener más información sobre el uso de este cuadro de diálogo, vea el artículo [cuadro de diálogo Editor de colección de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Propiedades InitializeCorrelation

En la tabla siguiente se muestran las <xref:System.ServiceModel.Activities.InitializeCorrelation> propiedades y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en la ventana **propiedades** o en diseñador de flujo de trabajo superficie.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.InitializeCorrelation>. El valor predeterminado es InitializeCorrelation.<br /><br /> Aunque el uso de un valor no predeterminado para el descriptivo <xref:System.Activities.Activity.DisplayName%2A> no es estrictamente necesario, se recomienda.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> se utiliza para asociar las actividades de flujo de trabajo en la correlación.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Un diccionario de datos de correlación que relaciona los mensajes con la instancia de flujo de trabajo.<br /><br /> Utilice el cuadro de diálogo **inicializar correlación** para configurar <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . Para obtener más información sobre el uso de este cuadro de diálogo, vea el artículo [cuadro de diálogo Editor de colección de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Aparecen](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)