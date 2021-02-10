---
title: Cuadro de diálogo Agregar CorrelationInitializers
description: Obtenga información acerca de cómo puede usar el cuadro de diálogo Agregar inicializadores de correlación en Diseñador de flujo de trabajo para configurar las propiedades de CorrelationInitializers de las actividades de envío, recepción y SendReply.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ca78cea409f559583507fd4b5b7c9fc43f9a5ffc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963736"
---
# <a name="add-correlationinitializers-dialog-box"></a>Agregar CorrelationInitializers (cuadro de diálogo)

El cuadro de diálogo **Agregar inicializadores de correlación** se utiliza en diseñador de flujo de trabajo para configurar las propiedades de **CorrelationInitializers** de las <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> actividades,, <xref:System.ServiceModel.Activities.SendReply> y <xref:System.ServiceModel.Activities.ReceiveReply> . Para obtener más información sobre los diseñadores de actividad que utilizan este cuadro, vea los temas [send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)y [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Los inicializadores de correlación de la colección especificada con este cuadro de diálogo pueden inicializar las siguientes correlaciones entre las actividades de mensajería:

- basado en consultas
- context
- contexto de devolución de llamada
- solicitud-respuesta

En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **Agregar inicializadores de correlación** :

|Elemento de UI|Descripción|
|-|-----------------|
|**Agregar inicializador**|Haga clic en el cuadro **Agregar inicializar** para agregar un inicializador adicional a la colección.|
|**Tipo de correlación**|Especifica el tipo de inicializador de correlación. Hay cuatro tipos a elegir:<br /><br /> 1. un inicializador de correlación de devolución de llamada para especificar un <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .<br />2. un inicializador de correlación de contexto para especificar un <xref:System.ServiceModel.Activities.CorrelationInitializer> .<br />3. un inicializador de correlación de solicitud-respuesta para especificar un <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .<br />4. un inicializador de correlación de consultas para especificar un <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .<br /><br /> Para editar el **CorrelationType**<br /><br /> 1. Tab para la fila específica de la cuadrícula **Agregar inicializador** .<br />2. para establecer el foco en **CorrelationTypeComboBox**, presione la tecla **Ctrl** + .<br />3. Presione Alt + flecha abajo para mostrar el **cuadro combinado** y editarlo.|
|**Consultas XPath**|Par clave-valor que contiene las consultas que se usan para extraer los datos de la correlación de los mensajes entrantes y salientes. Esta lista solo es válida cuando se utilizan tipos <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Para iniciar el cuadro de diálogo Agregar inicializadores de correlación

 Los diseñadores **send**, **Receive**, **ReceiveAndSendReply** y **SendAndReceiveReply** utilizan el cuadro de diálogo **Agregar inicializadores de correlación** . El acceso a ellas es similar en cada caso, y en este caso se usa el caso que implica el diseñador de **recepción** para ilustrar el procedimiento.

 El diseñador de actividades **Receive** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo cada vez que se colocan las actividades. Al quitar el diseñador de actividad **Receive** , se crea una <xref:System.ServiceModel.Activities.Receive> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de Receive. Seleccione el diseñador de actividades **Receive** y haga clic en el botón de puntos suspensivos junto al texto (colección) de la propiedad **CorrelationInitializers** en la cuadrícula de propiedades para que aparezca el cuadro de diálogo **Agregar inicializadores de correlación** .

## <a name="see-also"></a>Vea también

- [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)
