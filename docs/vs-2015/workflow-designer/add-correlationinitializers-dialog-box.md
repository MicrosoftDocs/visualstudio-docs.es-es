---
title: Cuadro de diálogo Agregar CorrelationInitializers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1402b90dfc78068546b510ce6b85379b1695f47
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672039"
---
# <a name="add-correlationinitializers-dialog-box"></a>Agregar CorrelationInitializers (cuadro de diálogo)
El cuadro de diálogo **Agregar inicializadores de correlación** se utiliza en [!INCLUDE[wfd1](../includes/wfd1-md.md)] para configurar las propiedades de **CorrelationInitializers** de las actividades <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> y <xref:System.ServiceModel.Activities.ReceiveReply>. [!INCLUDE[crabout](../includes/crabout-md.md)] los diseñadores de actividad que utilizan este cuadro, vea los temas [send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)y [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 Los inicializadores de correlación en la colección que se especifica con este cuadro de diálogo pueden inicializar correlaciones basadas en consultas, de contexto, de contexto de devolución o de solicitud/respuesta entre actividades de mensajería.

 En la tabla siguiente se describen los elementos de la interfaz de usuario (IU) del cuadro de diálogo **Agregar inicializadores de correlación** .

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Agregar inicializador**|Haga clic en el cuadro **Agregar inicializar** para agregar un inicializador adicional a la colección.|
|**Tipo de correlación**|Especifica el tipo de inicializador de correlación. Hay cuatro tipos a elegir:<br /><br /> 1. un inicializador de correlación de devolución de llamada para especificar una <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. un inicializador de correlación de contexto para especificar un <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. un inicializador de correlación de solicitud-respuesta para especificar una <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. un inicializador de correlación de consultas para especificar una <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Para editar el **CorrelationType**<br /><br /> 1. Tab para la fila específica de la cuadrícula **Agregar inicializador** .<br />2. Presione CTRL + TAB para establecer el foco en **CorrelationTypeComboBox**<br />3. Presione Alt + flecha abajo para mostrar el **cuadro combinado** y editarlo.|
|**Consultas XPath**|Par clave-valor que contiene las consultas que se usan para extraer los datos de la correlación de los mensajes entrantes y salientes. Esta lista solo es válida cuando se utilizan tipos <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Para iniciar el cuadro de diálogo Agregar inicializadores de correlación
 Los diseñadores **send**, **Receive**, **ReceiveAndSendReply**y **SendAndReceiveReply** utilizan el cuadro de diálogo **Agregar inicializadores de correlación** . Tener acceso a ellos es similar en cada caso y el caso en el que se usa el diseñador de **recepción** se utiliza aquí para ilustrar el procedimiento.

 El diseñador de actividades **Receive** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie [!INCLUDE[wfd2](../includes/wfd2-md.md)], donde se coloquen normalmente las actividades. Esto crea una actividad <xref:System.ServiceModel.Activities.Receive> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Receive. Seleccione el diseñador de actividades **Receive** y haga clic en el botón de puntos suspensivos junto al texto (colección) de la propiedad **CorrelationInitializers** en la cuadrícula de propiedades para que aparezca el cuadro de diálogo **Agregar inicializadores de correlación** .

## <a name="see-also"></a>Vea también
 [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)