---
title: Diseñador de flujo de trabajo - cuadro de diálogo de definición de contenido
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f20a17cf7e01eafc75263bd2753d686908574752
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971672"
---
# <a name="content-definition-dialog-box"></a>Definición de contenido (cuadro de diálogo)

El **definición de contenido** cuadro de diálogo se usa en el Diseñador de flujo de trabajo de Windows para configurar el **contenido** propiedades de la <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, y <xref:System.ServiceModel.Activities.ReceiveReply> actividades. Para obtener más información acerca de los diseñadores de actividad que utilice este cuadro, consulte la [enviar](../workflow-designer/send-activity-designer.md), [recepción](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), y [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) temas.

La tabla siguiente describen los elementos de interfaz de usuario de la **inicializar correlación** cuadro de diálogo:

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Mensaje**|Especifica el contenido del mensaje con el **los datos del mensaje** cuadro de texto de expresión y el tipo mediante el **tipo de mensaje** cuadro de lista desplegable. De forma predeterminada, el **definición de contenido** utiliza la <xref:System.ServiceModel.Activities.ReceiveMessageContent>, que espera un <xref:System.ServiceModel.Channels.Message> o un tipo dentro de la definición de servicio de flujo de trabajo de contrato de mensaje.|
|**Parámetros**|Haga clic en el **parámetros** botón de radio para utilizar <xref:System.ServiceModel.Activities.ReceiveParametersContent>, que espera un contrato de datos. Utilice la cuadrícula de datos para establecer una colección genérica de par clave-valor <xref:System.Activities.OutArgument> cuyos valores se asignen a parámetros de variables en el flujo de trabajo actual.|

El **definición de contenido** cuadro de diálogo se usa por la **enviar**, **recepción**, **ReceiveAndSendReply**, y  **SendAndReceiveReply** diseñadores. El acceso a los mismos es similar en todos los casos; se usará Receive para ilustrar el procedimiento.

El **recepción** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Seleccione el **recepción** Diseñador de actividad y haga clic en botón de los puntos suspensivos junto al texto (contenido) para la **contenido** propiedad en la cuadrícula de propiedades para el **definición de contenido**que aparezca el cuadro de diálogo.

El contenido se puede especificar en el **mensaje** sección para un <xref:System.ServiceModel.Activities.ReceiveMessageContent> actividad o en la **parámetro** sección un <xref:System.ServiceModel.Activities.ReceiveParametersContent> actividad.

## <a name="see-also"></a>Vea también

- [Ayuda de la interfaz de usuario del Diseñador de flujo de trabajo](../workflow-designer/workflow-designer-ui-help.md)