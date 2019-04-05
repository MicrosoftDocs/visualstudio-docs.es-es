---
title: Filtrar Invocar una operación de contrato de Windows Communication Foundation (heredado) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b6cdd551a0cf8ee085359f5545dd16dfac163c4d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988053"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Filtrar Invocar a una operación de contrato de Windows Communication Foundation (heredado)
En este tema se describe cómo invocar una operación de contrato de [!INCLUDE[indigo1](../includes/indigo1-md.md)] usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Después de arrastrar un **SendActivity** actividad desde el cuadro de herramientas hasta la superficie de diseño de flujo de trabajo, debe importar un contrato existente y determinar qué operación se invocará desde que **SendActivity** actividad. Seleccione el contrato y sus operaciones a través de la [elija el cuadro de diálogo de operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Además, si se utiliza un archivo de configuración con el servicio, es necesario especificar un <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifica la configuración del extremo que la actividad de envío va a utilizar para conectar con el servicio de flujo de trabajo.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Invocar una operación de contrato WCF desde una actividad SendActivity  
  
1.  Haga doble clic en el **SendActivity** actividad en el diseñador o haga clic en el botón de puntos suspensivos junto a la **ServiceOperationInfo** propiedad en el **propiedades** panel.  
  
2.  Cuando el **elegir operación** abre el cuadro de diálogo, haga clic en **importación** en la esquina superior derecha del cuadro de diálogo.  
  
     El [examinar y seleccionar un cuadro de diálogo de tipo .NET (heredado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) se abre.  
  
3.  Busque un ensamblado o proyecto que contenga el contrato deseado.  
  
4.  Seleccione el contrato y haga clic en **Aceptar**.  
  
5.  En **las operaciones disponibles**, seleccione la operación que desea invocar y haga clic en **Aceptar**.  
  
### <a name="to-specify-a-channel-token"></a>Para especificar un token de canal  
  
1.  Seleccione la actividad <xref:System.Workflow.Activities.SendActivity> en el diseñador.  
  
2.  En el **propiedades** panel, especifique un nombre para el <xref:System.Workflow.Activities.ChannelToken>. Este nombre únicamente identifica el token de canal.  
  
3.  Expanda el nodo del token de canal y especifique un nombre para el punto de conexión de cliente que va a utilizar en el campo <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. La configuración del extremo del mismo nombre en el archivo de configuración se utilizará para configurar el canal.  
  
4.  Cree la configuración del extremo en el archivo de configuración, si aún no existe. Para obtener más información acerca de cómo configurar el cliente, consulte [WCF Client Overview](http://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).  
  
## <a name="see-also"></a>Vea también  
 [Elija el cuadro de diálogo de operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Cómo: Implementar una operación de contrato WCF (heredado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)