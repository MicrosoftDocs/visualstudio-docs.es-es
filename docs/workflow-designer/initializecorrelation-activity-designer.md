---
title: Diseñador de flujo de trabajo - Diseñador de actividades InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24d319af36b5d07661213edb3cff48d376bd3736
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="initializecorrelation-activity-designer"></a>Diseñador de actividades InitializeCorrelation

El **InitializeCorrelation** Diseñador de actividades se usa para crear y configurar un <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad que se utiliza para establecer una correlación entre los mensajes antes de enviarlos o recibirlos.

## <a name="the-initializecorrelation-activity"></a>Actividad InitializeCorrelation

Una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> se utiliza para inicializar las correlaciones sin enviar o recibir un mensaje. Normalmente una correlación se inicializa cuando se envía o recibe un mensaje. Si se debe establecer una correlación antes de enviar o recibir un mensaje, utilice <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar la correlación.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizar el diseñador de actividades InitializeCorrelation
 El **InitializeCorrelation** Diseñador de actividad puede encontrarse en el **mensajería** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en la **cuadro de herramientas**  ficha en el Diseñador de flujo de trabajo (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)

 El **InitializeCorrelation** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo. Esto crea una <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad no tiene un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **InitializeCorrelation** Diseñador de actividad o en la  **DisplayName** cuadro de la **propiedades** ventana.

 El <xref:System.ServiceModel.Activities.CorrelationHandle> puede ser especifica en la **correlación** campo **propiedades** ventana en el **InitializeCorrelation** superficie del Diseñador de actividad.

 Haga clic en el botón de puntos suspensivos además el **CorrelationData** campo **propiedades** ventana o el texto de la sugerencia "Ver..." en **InitializeCorrelation** Diseñador de actividad superficie muestra el **inicializar correlación** cuadro de diálogo en el que puede especificar el identificador de correlación y los pares de clave y valor utilizados para inicializarlo. Para obtener más información sobre el uso de este cuadro de diálogo, vea el [cuadro de diálogo de Editor de colección de tipo](../workflow-designer/type-collection-editor-dialog-box.md) tema.

### <a name="the-initializecorrelation-properties"></a>Propiedades InitializeCorrelation
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.InitializeCorrelation> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en **propiedades** ventana o en la superficie del Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.InitializeCorrelation>. El valor predeterminado es InitializeCorrelation.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> se utiliza para asociar las actividades de flujo de trabajo en la correlación.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Un diccionario de datos de correlación que relaciona los mensajes con la instancia de flujo de trabajo.<br /><br /> Use la **inicializar correlación** cuadro de diálogo para configurar la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Para obtener más información sobre el uso en este cuadro de diálogo, vea el [cuadro de diálogo de Editor de colección de tipo](../workflow-designer/type-collection-editor-dialog-box.md) tema.|

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Recepción](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)