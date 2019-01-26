---
title: Diseñador de flujo de trabajo - Diseñador de actividades InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ff0dd27409c77e75a451e98a3771dfb78bf2b7d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070791"
---
# <a name="initializecorrelation-activity-designer"></a>Diseñador de actividades InitializeCorrelation

El **InitializeCorrelation** Diseñador de actividad se usa para crear y configurar un <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad. El <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad establece una correlación entre los mensajes antes de enviarlos o recibirlos.

## <a name="the-initializecorrelation-activity"></a>Actividad InitializeCorrelation

Una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> se utiliza para inicializar las correlaciones sin enviar o recibir un mensaje. Normalmente una correlación se inicializa cuando se envía o recibe un mensaje. Si se debe establecer una correlación antes de enviar o recibir un mensaje, utilice <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar la correlación.

### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizar el diseñador de actividades InitializeCorrelation

Acceso a la **InitializeCorrelation** Diseñador de actividad en el **mensajería** categoría de la **cuadro de herramientas**.

El **InitializeCorrelation** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo. Al colocar el Diseñador de actividad se crea un <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad su valor predeterminado es <xref:System.Activities.Activity.DisplayName%2A> de InitializeCorrelation. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **InitializeCorrelation** Diseñador de actividad o en el **DisplayName** cuadro de la **propiedades** ventana.

El <xref:System.ServiceModel.Activities.CorrelationHandle> puede ser especifica en el **correlación** campo **propiedades** ventana en la **InitializeCorrelation** superficie del Diseñador de actividad.

Para mostrar el **inicializar correlación** cuadro de diálogo donde puede especificar el identificador de correlación y los pares de clave y valor utilizados para inicializar, seleccione el botón de puntos suspensivos junto a la **CorrelationData** campo **propiedades** ventana. O bien, seleccione el texto de la sugerencia "Ver..." en el **InitializeCorrelation** superficie del Diseñador de actividad. Para obtener más información sobre el uso de este cuadro de diálogo, vea el [cuadro de diálogo del Editor de colección de tipo](../workflow-designer/type-collection-editor-dialog-box.md) artículo.

### <a name="the-initializecorrelation-properties"></a>Propiedades InitializeCorrelation

La tabla siguiente muestra la <xref:System.ServiceModel.Activities.InitializeCorrelation> propiedades y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en **propiedades** ventana o en la superficie del Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.InitializeCorrelation>. El valor predeterminado es InitializeCorrelation.<br /><br /> Aunque el uso de un valor no predeterminado para el sencillo <xref:System.Activities.Activity.DisplayName%2A> no es estrictamente necesaria, se recomienda.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> se utiliza para asociar las actividades de flujo de trabajo en la correlación.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Un diccionario de datos de correlación que relaciona los mensajes con la instancia de flujo de trabajo.<br /><br /> Use la **inicializar correlación** cuadro de diálogo para configurar el <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Para obtener más información sobre el uso este cuadro de diálogo, vea el [cuadro de diálogo del Editor de colección de tipo](../workflow-designer/type-collection-editor-dialog-box.md) artículo.|

## <a name="see-also"></a>Vea también

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)