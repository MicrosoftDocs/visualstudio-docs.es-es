---
title: Cuadro de diálogo Definición de contenido | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d989f5a0c57e381041e8fe9c200aae1a76316ad8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656959"
---
# <a name="content-definition-dialog-box"></a>Definición de contenido (cuadro de diálogo)
El cuadro de diálogo **definición de contenido** se usa en [!INCLUDE[wfd1](../includes/wfd1-md.md)] para configurar las propiedades de **contenido** de las actividades <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> y <xref:System.ServiceModel.Activities.ReceiveReply>. [!INCLUDE[crabout](../includes/crabout-md.md)] los diseñadores de actividad que utilizan este cuadro, vea los temas [send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)y [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 En la tabla siguiente se describen los elementos de la interfaz de usuario (IU) del cuadro de diálogo **inicializar correlación** .

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Mensaje**|Especifica el contenido del mensaje con el cuadro de texto expresión de **datos del mensaje** y el tipo mediante el cuadro de lista desplegable **tipo de mensaje** . De forma predeterminada, la **definición de contenido** utiliza el <xref:System.ServiceModel.Activities.ReceiveMessageContent>, que espera un <xref:System.ServiceModel.Channels.Message> o un tipo de contrato de mensaje dentro de la definición del servicio de flujo de trabajo.|
|**Parámetros**|Haga clic en el botón de radio **parámetros** para usar <xref:System.ServiceModel.Activities.ReceiveParametersContent>, que espera un contrato de datos. Utilice la cuadrícula de datos para establecer una colección genérica de par clave-valor <xref:System.Activities.OutArgument> cuyos valores se asignen a parámetros de variables en el flujo de trabajo actual.|

 Los diseñadores **send**, **Receive**, **ReceiveAndSendReply**y **SendAndReceiveReply** utilizan el cuadro de diálogo **definición de contenido** . El acceso a los mismos es similar en todos los casos; se usará Receive para ilustrar el procedimiento.

 El diseñador de actividades **Receive** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie [!INCLUDE[wfd2](../includes/wfd2-md.md)], donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Seleccione el diseñador de actividades **Receive** y haga clic en el botón de puntos suspensivos junto al texto (contenido) de la propiedad **Content** en la cuadrícula de propiedades para que aparezca el cuadro de diálogo **definición de contenido** .

 El contenido se puede especificar en la sección de **mensajes** de una actividad <xref:System.ServiceModel.Activities.ReceiveMessageContent> o en la sección de **parámetros** de una actividad <xref:System.ServiceModel.Activities.ReceiveParametersContent>.

## <a name="see-also"></a>Vea también
 [Ayuda de la interfaz de usuario del Diseñador de flujo de trabajo](../workflow-designer/workflow-designer-ui-help.md)