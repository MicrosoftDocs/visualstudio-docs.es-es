---
title: 'Cómo: invocar una operación de contrato de Windows Communication Foundation (heredado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f42600a739561a27a6dd8f6caa237027bac4554
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603697"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Cómo: Invocar una operación de contrato de Windows Communication Foundation (Heredado)
En este tema se describe cómo invocar una operación de contrato de [!INCLUDE[indigo1](../includes/indigo1-md.md)] usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Después de arrastrar una actividad **SendActivity** desde el cuadro de herramientas a la superficie de diseño de flujo de trabajo, debe importar un contrato existente y determinar qué operación se invocará desde esa actividad **SendActivity** . Seleccione el contrato y sus operaciones a través del [cuadro de diálogo elegir operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md).

 Además, si se utiliza un archivo de configuración con el servicio, es necesario especificar un <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifica la configuración del extremo que la actividad de envío va a utilizar para conectar con el servicio de flujo de trabajo.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Invocar una operación de contrato WCF desde una actividad SendActivity

1. Haga doble clic en la actividad **SendActivity** en el diseñador o haga clic en los puntos suspensivos junto a la propiedad **ServiceOperationInfo** en el panel de **propiedades** .

2. Cuando se abra el cuadro de diálogo **elegir operación** , haga clic en **importar** en la esquina superior derecha del cuadro de diálogo.

     Se abre el [cuadro de diálogo examinar y seleccionar un tipo .net (heredado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) .

3. Busque un ensamblado o proyecto que contenga el contrato deseado.

4. Seleccione el contrato y haga clic en **Aceptar**.

5. En **operaciones disponibles**, seleccione la operación que desea invocar y haga clic en **Aceptar**.

### <a name="to-specify-a-channel-token"></a>Para especificar un token de canal

1. Seleccione la actividad <xref:System.Workflow.Activities.SendActivity> en el diseñador.

2. En el panel **propiedades** , especifique un nombre para el <xref:System.Workflow.Activities.ChannelToken> . Este nombre únicamente identifica el token de canal.

3. Expanda el nodo del token de canal y especifique un nombre para el punto de conexión de cliente que va a utilizar en el campo <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. La configuración del extremo del mismo nombre en el archivo de configuración se utilizará para configurar el canal.

4. Cree la configuración del extremo en el archivo de configuración, si aún no existe. Para obtener más información acerca de cómo configurar el cliente, consulte [información general del cliente de WCF](https://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).

## <a name="see-also"></a>Consulte también
 [Cuadro de diálogo elegir operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md) cómo: implementar [las actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md) [de operación de contrato WCF (heredadas)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)