---
title: "Cuadro de diálogo Definición de contenido | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: c87180f1f1c0b2c578977021b6a9511e629d10bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="content-definition-dialog-box"></a>Definición de contenido (cuadro de diálogo)
El **definición de contenido** cuadro de diálogo se usa en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] para configurar el **contenido** propiedades de la <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, y <xref:System.ServiceModel.Activities.ReceiveReply> actividades. [!INCLUDE[crabout](../test/includes/crabout_md.md)]los diseñadores de actividades que utilizan este cuadro, consulte la [enviar](../workflow-designer/send-activity-designer.md), [recepción](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), y [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) temas.  
  
 La tabla siguiente describen los elementos de interfaz de usuario de la **inicializar correlación** cuadro de diálogo.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------|-----------------|  
|**Mensaje**|Especifica el contenido del mensaje con el **los datos del mensaje** cuadro de texto de expresión y el tipo mediante el **tipo de mensaje** cuadro de lista desplegable. De forma predeterminada, el **definición de contenido** utiliza la <xref:System.ServiceModel.Activities.ReceiveMessageContent>, que espera un <xref:System.ServiceModel.Channels.Message> o un tipo dentro de la definición de servicio de flujo de trabajo de contrato de mensaje.|  
|**Parámetros**|Haga clic en el **parámetros** botón de radio para utilizar <xref:System.ServiceModel.Activities.ReceiveParametersContent>, que espera un contrato de datos. Utilice la cuadrícula de datos para establecer una colección genérica de par clave-valor <xref:System.Activities.OutArgument> cuyos valores se asignen a parámetros de variables en el flujo de trabajo actual.|  
  
 El **definición de contenido** cuadro de diálogo se usa por la **enviar**, **recepción**, **ReceiveAndSendReply**, y  **SendAndReceiveReply** diseñadores. El acceso a los mismos es similar en todos los casos; se usará Receive para ilustrar el procedimiento.  
  
 El **recepción** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Seleccione el **recepción** Diseñador de actividad y haga clic en botón de los puntos suspensivos junto al texto (contenido) para la **contenido** propiedad en la cuadrícula de propiedades para el **definición de contenido**que aparezca el cuadro de diálogo.  
  
 El contenido se puede especificar en el **mensaje** sección para un <xref:System.ServiceModel.Activities.ReceiveMessageContent> actividad o en la **parámetro** sección un <xref:System.ServiceModel.Activities.ReceiveParametersContent> actividad.  
  
## <a name="see-also"></a>Vea también  
 [Ayuda de la interfaz de usuario del Diseñador de flujo de trabajo](../workflow-designer/workflow-designer-ui-help.md)