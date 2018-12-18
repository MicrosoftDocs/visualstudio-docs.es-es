---
title: Diseñador de actividades InitializeCorrelation | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9dd9d622785fbfebd8560daf9bf459716381ddbf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49234031"
---
# <a name="initializecorrelation-activity-designer"></a>Diseñador de actividades InitializeCorrelation
El **InitializeCorrelation** Diseñador de actividad se usa para crear y configurar un <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad que se usa para establecer una correlación entre los mensajes antes de enviarlos o recibirlos.  
  
## <a name="the-initializecorrelation-activity"></a>Actividad InitializeCorrelation  
 Una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> se utiliza para inicializar las correlaciones sin enviar o recibir un mensaje. Normalmente una correlación se inicializa cuando se envía o recibe un mensaje. Si se debe establecer una correlación antes de enviar o recibir un mensaje, utilice <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar la correlación.  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>Utilizar el diseñador de actividades InitializeCorrelation  
 El **InitializeCorrelation** Diseñador de actividad puede encontrarse en el **mensajería** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **cuadro de herramientas**  ficha la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **InitializeCorrelation** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie. Esto crea un <xref:System.ServiceModel.Activities.InitializeCorrelation> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **InitializeCorrelation** Diseñador de actividad o en el  **DisplayName** cuadro de la **propiedades** ventana.  
  
 El <xref:System.ServiceModel.Activities.CorrelationHandle> puede ser especifica en el **correlación** campo **propiedades** ventana en la **InitializeCorrelation** superficie del Diseñador de actividad.  
  
 Al hacer clic en el botón de puntos suspensivos además el **CorrelationData** campo **propiedades** ventana o "Ver..." texto de sugerencia en **InitializeCorrelation** superficie del Diseñador de actividad muestra la **inicializar correlación** en el que puede especificar el identificador de correlación y los pares de clave y valor utilizados para el cuadro de diálogo inicializarla. [!INCLUDE[crabout](../includes/crabout-md.md)] mediante este cuadro de diálogo, vea el [cuadro de diálogo del Editor de colección de tipo](../workflow-designer/type-collection-editor-dialog-box.md) tema.  
  
### <a name="the-initializecorrelation-properties"></a>Propiedades InitializeCorrelation  
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.InitializeCorrelation> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en **propiedades** ventana o en [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.InitializeCorrelation>. El valor predeterminado es InitializeCorrelation.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> se utiliza para asociar las actividades de flujo de trabajo en la correlación.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Un diccionario de datos de correlación que relaciona los mensajes con la instancia de flujo de trabajo.<br /><br /> Use la **inicializar correlación** cuadro de diálogo para configurar el <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] el uso este cuadro de diálogo, vea el [cuadro de diálogo del Editor de colección de tipo](../workflow-designer/type-collection-editor-dialog-box.md) tema.|  
  
## <a name="see-also"></a>Vea también  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Recibir](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Enviar](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)