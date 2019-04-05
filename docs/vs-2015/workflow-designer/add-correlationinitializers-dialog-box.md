---
title: Agregar cuadro de diálogo CorrelationInitializers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0c90a2d0e0297a00454e38f428093a2f2db1e46d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002444"
---
# <a name="add-correlationinitializers-dialog-box"></a>Agregar CorrelationInitializers (cuadro de diálogo)
El **agregar inicializadores de correlación** cuadro de diálogo se usa en [!INCLUDE[wfd1](../includes/wfd1-md.md)] para configurar el **CorrelationInitializers** propiedades de la <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, y <xref:System.ServiceModel.Activities.ReceiveReply> actividades. [!INCLUDE[crabout](../includes/crabout-md.md)] los diseñadores de actividad que utilizan este cuadro, vea el [enviar](../workflow-designer/send-activity-designer.md), [recepción](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), y [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) temas.  
  
 Los inicializadores de correlación en la colección que se especifica con este cuadro de diálogo pueden inicializar correlaciones basadas en consultas, de contexto, de contexto de devolución o de solicitud/respuesta entre actividades de mensajería.  
  
 La tabla siguiente describen los elementos de interfaz de usuario de la **agregar inicializadores de correlación** cuadro de diálogo.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------|-----------------|  
|**Agregar inicializador**|Haga clic en el **agregar inicialización** casilla para agregar un inicializador adicional a la colección.|  
|**Tipo de correlación**|Especifica el tipo de inicializador de correlación. Hay cuatro tipos a elegir:<br /><br /> 1.  Inicializador de correlación de devolución para especificar una clase <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2.  Inicializador de correlación de contexto para especificar una clase <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3.  Inicializador de correlación de solicitud/respuesta para especificar una clase <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4.  Inicializador de consultas para especificar una clase <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Para editar el **CorrelationType**<br /><br /> 1.  Pestaña a la fila específica en el **agregar inicializador** DataGrid.<br />2.  Presione CTRL+TAB para establecer el foco en **CorrelationTypeComboBox**<br />3.  Presione ALT+flecha abajo para mostrar el **ComboBox** y editarlo.|  
|**Consultas XPath**|Par clave-valor que contiene las consultas que se usan para extraer los datos de la correlación de los mensajes entrantes y salientes. Esta lista solo es válida cuando se utilizan tipos <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Para iniciar el cuadro de diálogo Agregar inicializadores de correlación  
 El **agregar inicializadores de correlación** cuadro de diálogo se usa por la **enviar**, **recepción**, **ReceiveAndSendReply**, y  **SendAndReceiveReply** diseñadores. Acceso a ellos es similar en cada caso y en el caso de que impliquen la **recepción** diseñador es útil aquí para ilustrar el procedimiento.  
  
 El **recepción** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Seleccione el **recepción** Diseñador de actividad y haga clic en el botón de puntos suspensivos situado junto al texto (colección) para el **CorrelationInitializers** propiedad en la cuadrícula de propiedades para el **agregar Inicializadores de correlación** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)