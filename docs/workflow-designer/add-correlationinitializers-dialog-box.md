---
title: "Agregar cuadro de diálogo CorrelationInitializers | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 4c4d8e07aa172aef524b4d85bda5ad8efdfb509f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="add-correlationinitializers-dialog-box"></a>Agregar CorrelationInitializers (cuadro de diálogo)
El **agregar inicializadores de correlación** cuadro de diálogo se usa en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] para configurar el **CorrelationInitializers** propiedades de la <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, y <xref:System.ServiceModel.Activities.ReceiveReply> actividades. [!INCLUDE[crabout](../test/includes/crabout_md.md)]los diseñadores de actividades que utilizan este cuadro, consulte la [enviar](../workflow-designer/send-activity-designer.md), [recepción](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), y [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) temas.  
  
 Los inicializadores de correlación en la colección que se especifica con este cuadro de diálogo pueden inicializar correlaciones basadas en consultas, de contexto, de contexto de devolución o de solicitud/respuesta entre actividades de mensajería.  
  
 La tabla siguiente describen los elementos de interfaz de usuario de la **agregar inicializadores de correlación** cuadro de diálogo.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------|-----------------|  
|**Agregar inicializador**|Haga clic en el **agregar initialize** para agregar un inicializador adicional a la colección.|  
|**Tipo de correlación**|Especifica el tipo de inicializador de correlación. Hay cuatro tipos a elegir:<br /><br /> 1.  Inicializador de correlación de devolución para especificar una clase <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2.  Inicializador de correlación de contexto para especificar una clase <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3.  Inicializador de correlación de solicitud/respuesta para especificar una clase <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4.  Inicializador de consultas para especificar una clase <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Para editar la **CorrelationType**<br /><br /> 1.  Pestaña a la fila específica en el **agregar inicializador** DataGrid.<br />2.  Presione CTRL+TAB para establecer el foco en **CorrelationTypeComboBox**<br />3.  Presione ALT+flecha abajo para producir el **ComboBox** y editarlo.|  
|**Consultas XPath**|Par clave-valor que contiene las consultas que se usan para extraer los datos de la correlación de los mensajes entrantes y salientes. Esta lista solo es válida cuando se utilizan tipos <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Para iniciar el cuadro de diálogo Agregar inicializadores de correlación  
 El **agregar inicializadores de correlación** cuadro de diálogo se usa por la **enviar**, **recepción**, **ReceiveAndSendReply**, y  **SendAndReceiveReply** diseñadores. Obtener acceso a ellos es similar en cada caso y el caso de que implica la **recepción** diseñador es útil aquí para ilustrar el procedimiento.  
  
 El **recepción** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Seleccione el **recepción** Diseñador de actividad y haga clic en botón de los puntos suspensivos junto al texto (colección) para la **CorrelationInitializers** propiedad en la cuadrícula de propiedades para el **agregar Inicializadores de correlación** que aparezca el cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Agregar cuadro de diálogo de correlación](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)