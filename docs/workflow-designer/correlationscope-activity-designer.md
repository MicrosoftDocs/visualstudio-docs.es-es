---
title: "Diseñador de actividades CorrelationScope | Documentos de Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3a8798e653148e07baff5f0fb70c2ff56f7d4a16
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="correlationscope-activity-designer"></a>Diseñador de actividades CorrelationScope
El **CorrelationScope** Diseñador de actividades se usa para crear y configurar un <xref:System.ServiceModel.Activities.CorrelationScope> actividad que proporciona administración implícita de actividades de mensajería secundarias mediante un <xref:System.ServiceModel.Activities.CorrelationHandle> objeto.

## <a name="the-correlationscope-activity"></a>Actividad CorrelationScope
 La propiedad <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> especifica la clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para administrar las actividades de mensajería secundarias. Las actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.Receive> que se incluyen en la propiedad <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> se configuran para utilizar la propiedad <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de la actividad <xref:System.ServiceModel.Activities.CorrelationScope> que sirve de contenedor para efectuar la correlación.

### <a name="using-the-correlationscope-activity-designer"></a>Utilizar el diseñador de actividades CorrelationScope
 El **CorrelationScope** Diseñador de actividad puede encontrarse en el **mensajería** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas** ficha en el lado izquierdo de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)

 El **CorrelationScope** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superficie. Esto crea una <xref:System.ServiceModel.Activities.CorrelationScope> actividad con el valor predeterminado es **DisplayName** de CorrelationScope. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **CorrelationScope** Diseñador de actividad o en la **DisplayName** cuadro de la **propiedades** ventana.

 Para especificar el <xref:System.ServiceModel.Activities.CorrelationHandle> utilizada por las actividades de mensajería secundarias, haga clic en el botón de puntos suspensivos junto a la **CorrelatesWith** campo **propiedades** ventana para mostrar la **Editor de expresiones**  cuadro de diálogo. Esta propiedad también se puede establecer en la superficie del diseñador de actividades.

 Las actividades dentro del ámbito la correlación se especifican al colocar sus diseñadores dentro de la **cuerpo** cuadro dentro de la **CorrelationScope** diseñador.

### <a name="the-correlationscope-properties"></a>Propiedades CorrelationScope
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.CorrelationScope> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en **propiedades** ventana o en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesto y a menudo tanto en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.ServiceModel.Activities.InitializeCorrelation>.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Especifica la propiedad <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para administrar las actividades de mensajería secundarias. Si no se establece esta propiedad, <xref:System.ServiceModel.Activities.CorrelationScope> crea una propiedad <xref:System.ServiceModel.Activities.CorrelationHandle> implícita automáticamente.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Especifica las actividades dentro del ámbito de la correlación.|

## <a name="see-also"></a>Vea también

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)