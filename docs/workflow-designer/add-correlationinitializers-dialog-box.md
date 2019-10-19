---
title: 'Diseñador de flujo de trabajo: agregar CorrelationInitializers (cuadro de diálogo)'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d69b53e21d11cba99a9e897871c6f9e0320352f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650771"
---
# <a name="add-correlationinitializers-dialog-box"></a>Agregar CorrelationInitializers (cuadro de diálogo)

El cuadro de diálogo **Agregar inicializadores de correlación** se utiliza en diseñador de flujo de trabajo para configurar las propiedades de **CorrelationInitializers** de las actividades <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> y <xref:System.ServiceModel.Activities.ReceiveReply>. Para obtener más información sobre los diseñadores de actividad que utilizan este cuadro, vea los temas [send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)y [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Los inicializadores de correlación de la colección especificada con este cuadro de diálogo pueden inicializar las siguientes correlaciones entre las actividades de mensajería:

- basado en consultas
- contexto
- contexto de devolución de llamada
- solicitud-respuesta

En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **Agregar inicializadores de correlación** :

|Elemento de la interfaz de usuario|Descripción|
|-|-----------------|
|**Agregar inicializador**|Haga clic en el cuadro **Agregar inicializar** para agregar un inicializador adicional a la colección.|
|**Tipo de correlación**|Especifica el tipo de inicializador de correlación. Hay cuatro tipos a elegir:<br /><br /> 1. un inicializador de correlación de devolución de llamada para especificar una <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. un inicializador de correlación de contexto para especificar un <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. un inicializador de correlación de solicitud-respuesta para especificar una <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. un inicializador de correlación de consultas para especificar una <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Para editar el **CorrelationType**<br /><br /> 1. Tab para la fila específica de la cuadrícula **Agregar inicializador** .<br />2. para establecer el foco en **CorrelationTypeComboBox**, presione **Ctrl** +**Tab**.<br />3. Presione Alt + flecha abajo para mostrar el **cuadro combinado** y editarlo.|
|**Consultas XPath**|Par clave-valor que contiene las consultas que se usan para extraer los datos de la correlación de los mensajes entrantes y salientes. Esta lista solo es válida cuando se utilizan tipos <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Para iniciar el cuadro de diálogo Agregar inicializadores de correlación

 Los diseñadores **send**, **Receive**, **ReceiveAndSendReply**y **SendAndReceiveReply** utilizan el cuadro de diálogo **Agregar inicializadores de correlación** . El acceso a ellas es similar en cada caso, y en este caso se usa el caso que implica el diseñador de **recepción** para ilustrar el procedimiento.

 El diseñador de actividades **Receive** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo cada vez que se colocan las actividades. Al quitar el diseñador de actividades **Receive** , se crea una actividad <xref:System.ServiceModel.Activities.Receive> con una <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Seleccione el diseñador de actividades **Receive** y haga clic en el botón de puntos suspensivos junto al texto (colección) de la propiedad **CorrelationInitializers** en la cuadrícula de propiedades para que aparezca el cuadro de diálogo **Agregar inicializadores de correlación** .

## <a name="see-also"></a>Vea también

- [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)