---
title: "C&#243;mo: Invocar una operaci&#243;n de contrato de Windows Communication Foundation (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# C&#243;mo: Invocar una operaci&#243;n de contrato de Windows Communication Foundation (Heredado)
En este tema se describe cómo invocar una operación de contrato de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] usando [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Después de arrastrar una actividad **SendActivity** desde el cuadro de herramientas hasta la superficie de diseño de flujo de trabajo, debe importar un contrato existente y determinar qué operación se invocará desde esa actividad **SendActivity**.El contrato y sus operaciones se seleccionan a través del [Elegir operación \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Además, si se utiliza un archivo de configuración con el servicio, es necesario especificar un <xref:System.Workflow.Activities.ChannelToken>.<xref:System.Workflow.Activities.ChannelToken> identifica la configuración del extremo que la actividad de envío va a utilizar para conectar con el servicio de flujo de trabajo.  
  
### Invocar una operación de contrato WCF desde una actividad SendActivity  
  
1.  Haga doble clic en la actividad **SendActivity** en el diseñador, o haga clic en los puntos suspensivos situados junto a la propiedad **ServiceOperationInfo** en el panel **Propiedades**.  
  
2.  Cuando se abre el cuadro de diálogo **Elegir operación**, haga clic en **Importar**, en la esquina superior derecha del cuadro de diálogo.  
  
     Se abre [Examinar y seleccionar un cuadro de diálogo de tipo .NET \(Heredado\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).  
  
3.  Busque un ensamblado o proyecto que contenga el contrato deseado.  
  
4.  Seleccione el contrato y haga clic en **Aceptar**.  
  
5.  En **Operaciones disponibles**, seleccione la operación que desea invocar y haga clic en **Aceptar**.  
  
### Para especificar un token de canal  
  
1.  Seleccione la actividad <xref:System.Workflow.Activities.SendActivity> en el diseñador.  
  
2.  En el panel **Propiedades**, especifique un nombre para el <xref:System.Workflow.Activities.ChannelToken>.Este nombre únicamente identifica el token de canal.  
  
3.  Expanda el nodo del token de canal y especifique un nombre para el extremo de cliente que va a utilizar en el campo <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>.La configuración del extremo del mismo nombre en el archivo de configuración se utilizará para configurar el canal.  
  
4.  Cree la configuración del extremo en el archivo de configuración, si aún no existe.Para obtener más información acerca de la configuración del cliente, vea [Introducción a un cliente WCF](../Topic/WCF%20Client%20Overview.md).  
  
## Vea también  
 [Elegir operación \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Cómo: Implementar una operación de contrato WCF \(Heredado\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)