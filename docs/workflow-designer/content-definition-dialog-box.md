---
title: "Definici&#243;n de contenido (cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "MessageContent.UI"
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Definici&#243;n de contenido (cuadro de di&#225;logo)
El cuadro de diálogo **Definición de contenido** se usa en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] para configurar las propiedades **Content** de las actividades <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> y <xref:System.ServiceModel.Activities.ReceiveReply>.[!INCLUDE[crabout](../test/includes/crabout_md.md)] los diseñadores de actividad que usan este cuadro, vea los temas [Enviar](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) y [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md).  
  
 En la tabla siguiente se describen los elementos de la interfaz de usuario del cuadro de diálogo **Inicializar correlación**.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------------------------------|-----------------|  
|**Mensaje**|Especifica el contenido del mensaje con el cuadro de texto de expresión **Datos del mensaje** y el tipo mediante el cuadro de lista desplegable **Tipo de mensaje**.De forma predeterminada, **Definición de contenido** se sirve de la clase <xref:System.ServiceModel.Activities.ReceiveMessageContent>, que espera una clase <xref:System.ServiceModel.Channels.Message> o un tipo de contrato de mensaje dentro de la definición de servicio de flujo de trabajo.|  
|**Parámetros**|Haga clic en el botón de radio **Parámetros** para utilizar <xref:System.ServiceModel.Activities.ReceiveParametersContent>, que espera un contrato de datos.Utilice la cuadrícula de datos para establecer una colección genérica de par clave\-valor <xref:System.Activities.OutArgument> cuyos valores se asignen a parámetros de variables en el flujo de trabajo actual.|  
  
 Los diseñadores **Send**, **Receive**, **ReceiveAndSendReply** y **SendAndReceiveReply** se sirven del cuadro de diálogo **Definición de contenido**.El acceso a los mismos es similar en todos los casos; se usará Receive para ilustrar el procedimiento.  
  
 El diseñador de actividades **Receive** se puede arrastrar desde el **Cuadro de herramientas** y colocar en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades.Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive.Seleccione el diseñador de actividades **Receive** y haga clic en el botón de puntos suspensivos junto al texto \(Contenido\) para la propiedad **Content** en la cuadrícula de propiedades para que aparezca el cuadro de diálogo **Definición de contenido**.  
  
 El contenido se puede especificar en la sección **Mensaje** para obtener una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o en la sección **Parámetro** para obtener una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>.  
  
## Vea también  
 [Ayuda de la interfaz de usuario del Diseñador de flujo de trabajo](../workflow-designer/workflow-designer-ui-help.md)