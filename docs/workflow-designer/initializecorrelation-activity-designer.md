---
title: Diseñador de actividades Diseñador de flujo de trabajo-InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98a9a6bccb6eab2c4565a717daa897f93dbe8f53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650223"
---
# <a name="initializecorrelation-activity-designer"></a>Diseñador de actividades InitializeCorrelation

El diseñador de actividades **InitializeCorrelation** se utiliza para crear y configurar una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation>. La actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> establece una correlación entre los mensajes antes de enviarlos o recibirlos.

## <a name="the-initializecorrelation-activity"></a>Actividad InitializeCorrelation

Una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> se utiliza para inicializar las correlaciones sin enviar o recibir un mensaje. Normalmente una correlación se inicializa cuando se envía o recibe un mensaje. Si se debe establecer una correlación antes de enviar o recibir un mensaje, utilice <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar la correlación.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizar el diseñador de actividades InitializeCorrelation

Acceda al diseñador de actividades **InitializeCorrelation** en la categoría **Mensajería** del **cuadro de herramientas**.

El diseñador de actividades **InitializeCorrelation** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo. Al quitar el diseñador de actividad, se crea una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> con un <xref:System.Activities.Activity.DisplayName%2A> predeterminado de InitializeCorrelation. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **InitializeCorrelation** o en el cuadro **displayName** de la ventana **propiedades** .

El <xref:System.ServiceModel.Activities.CorrelationHandle> se puede especificar en el campo **correlación** de la ventana **propiedades** en la superficie del diseñador de actividades **InitializeCorrelation** .

Para mostrar el cuadro de diálogo **inicializar correlación** donde puede especificar el identificador de correlación y los pares clave-valor que se usan para inicializarlos, seleccione el botón de puntos suspensivos junto al campo **CorrelationData** en la ventana **propiedades** . O bien, seleccione la "vista..." texto de sugerencia en la superficie del diseñador de actividades **InitializeCorrelation** . Para obtener más información sobre el uso de este cuadro de diálogo, vea el artículo [cuadro de diálogo Editor de colección de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Propiedades InitializeCorrelation

En la tabla siguiente se muestran las propiedades de <xref:System.ServiceModel.Activities.InitializeCorrelation> y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en la ventana **propiedades** o en diseñador de flujo de trabajo superficie.

|Nombre de la propiedad|Requerido|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.InitializeCorrelation>. El valor predeterminado es InitializeCorrelation.<br /><br /> Aunque el uso de un valor no predeterminado para el <xref:System.Activities.Activity.DisplayName%2A> descriptivo no es estrictamente necesario, se recomienda.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> se utiliza para asociar las actividades de flujo de trabajo en la correlación.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Un diccionario de datos de correlación que relaciona los mensajes con la instancia de flujo de trabajo.<br /><br /> Utilice el cuadro de diálogo **inicializar correlación** para configurar el <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Para obtener más información sobre el uso de este cuadro de diálogo, vea el artículo [cuadro de diálogo Editor de colección de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)