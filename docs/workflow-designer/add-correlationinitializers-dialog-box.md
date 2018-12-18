---
title: Diseñador de flujo de trabajo - Agregar cuadro de diálogo CorrelationInitializers
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 724c4e3ac911e5fda62304a08565937f38425368
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948959"
---
# <a name="add-correlationinitializers-dialog-box"></a>Agregar CorrelationInitializers (cuadro de diálogo)

El **agregar inicializadores de correlación** cuadro de diálogo se usa en el Diseñador de flujo de trabajo para configurar la **CorrelationInitializers** propiedades de la <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, y <xref:System.ServiceModel.Activities.ReceiveReply> actividades. Para obtener más información acerca de los diseñadores de actividad que utilizan este cuadro, vea el [enviar](../workflow-designer/send-activity-designer.md), [recepción](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), y [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) temas.

Los inicializadores de correlación en la colección especificada con este cuadro de diálogo pueden inicializar las correlaciones entre las actividades de mensajería siguientes:

- basado en consultas
- contexto
- contexto de devolución de llamada
- solicitud-respuesta

La tabla siguiente describen los elementos de interfaz de usuario de la **agregar inicializadores de correlación** cuadro de diálogo:

|Elemento de la interfaz de usuario|Descripción|
|-|-----------------|
|**Agregar inicializador**|Haga clic en el **agregar inicialización** casilla para agregar un inicializador adicional a la colección.|
|**Tipo de correlación**|Especifica el tipo de inicializador de correlación. Hay cuatro tipos a elegir:<br /><br /> 1. Inicializador de correlación de devolución para especificar una clase <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. Inicializador de correlación de contexto para especificar una clase <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. Inicializador de correlación de solicitud/respuesta para especificar una clase <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. Inicializador de consultas para especificar una clase <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Para editar el **CorrelationType**<br /><br /> 1. Pestaña a la fila específica en el **agregar inicializador** DataGrid.<br />2. Para establecer el foco **CorrelationTypeComboBox**, presione **Ctrl**+**ficha**.<br />3. Presione ALT+flecha abajo para mostrar el **ComboBox** y editarlo.|
|**Consultas XPath**|Par clave-valor que contiene las consultas que se usan para extraer los datos de la correlación de los mensajes entrantes y salientes. Esta lista solo es válida cuando se utilizan tipos <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Para iniciar el cuadro de diálogo Agregar inicializadores de correlación

 El **agregar inicializadores de correlación** cuadro de diálogo se usa por la **enviar**, **recepción**, **ReceiveAndSendReply**, y  **SendAndReceiveReply** diseñadores. Acceso a ellos es similar en cada caso y en el caso de que impliquen la **recepción** diseñador se usa aquí para ilustrar el procedimiento.

 El **recepción** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se colocan las actividades. Quitar el **recepción** Diseñador de actividad se crea un <xref:System.ServiceModel.Activities.Receive> actividad su valor predeterminado es <xref:System.Activities.Activity.DisplayName%2A> de recepción. Seleccione el **recepción** Diseñador de actividad y haga clic en el botón de puntos suspensivos situado junto al texto (colección) para el **CorrelationInitializers** propiedad en la cuadrícula de propiedades para el **agregar Inicializadores de correlación** cuadro de diálogo.

## <a name="see-also"></a>Vea también

- [Agregar cuadro de diálogo de correlación](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Cuadro de diálogo Inicializar correlación](../workflow-designer/initialize-correlation-dialog-box.md)