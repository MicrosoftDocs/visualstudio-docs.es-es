---
title: 'Diseñador de flujo de trabajo: cuadro de diálogo Definición de contenido'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19e2341d458c98f01d3b58d6f77887ac1cfe6746
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876208"
---
# <a name="content-definition-dialog-box"></a>Definición de contenido (cuadro de diálogo)

El cuadro de diálogo **definición de contenido** se usa en diseñador de flujo de trabajo para configurar las propiedades de **contenido** de las <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> actividades,, <xref:System.ServiceModel.Activities.SendReply> y <xref:System.ServiceModel.Activities.ReceiveReply> . Para obtener más información sobre los diseñadores de actividad que utilizan este cuadro, vea los temas [send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)y [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

En la tabla siguiente se describen los elementos de la interfaz de usuario (IU) del cuadro de diálogo **inicializar correlación** :

|Elemento de UI|Descripción|
|-|-----------------|
|**Mensaje**|Especifica el contenido del mensaje con el cuadro de texto expresión de **datos del mensaje** y el tipo mediante el cuadro de lista desplegable **tipo de mensaje** . De forma predeterminada, la **definición de contenido** utiliza <xref:System.ServiceModel.Activities.ReceiveMessageContent> , que espera un <xref:System.ServiceModel.Channels.Message> tipo de contrato de mensaje o dentro de la definición del servicio de flujo de trabajo.|
|**Parámetros**|Haga clic en el botón de radio **parámetros** para usar <xref:System.ServiceModel.Activities.ReceiveParametersContent> , que espera un contrato de datos. Utilice la cuadrícula de datos para establecer una colección genérica de par clave-valor <xref:System.Activities.OutArgument> cuyos valores se asignen a parámetros de variables en el flujo de trabajo actual.|

Los diseñadores **send**, **Receive**, **ReceiveAndSendReply**y **SendAndReceiveReply** utilizan el cuadro de diálogo **definición de contenido** . El acceso a los mismos es similar en todos los casos; se usará Receive para ilustrar el procedimiento.

El diseñador de actividades **Receive** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Seleccione el diseñador de actividades **Receive** y haga clic en el botón de puntos suspensivos junto al texto (contenido) de la propiedad **Content** en la cuadrícula de propiedades para que aparezca el cuadro de diálogo **definición de contenido** .

El contenido se puede especificar en la sección de **mensajes** de una <xref:System.ServiceModel.Activities.ReceiveMessageContent> actividad o en la sección de **parámetros** de una <xref:System.ServiceModel.Activities.ReceiveParametersContent> actividad.

## <a name="see-also"></a>Vea también

- [Ayuda de la interfaz de usuario del Diseñador de flujo de trabajo](browse-and-select-a-dotnet-type-dialog-box.md)