---
title: 'Diseñador de flujo de trabajo: Cómo: invocar una operación de contrato de Windows Communication Foundation (heredado)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b39d2132b29ec1f8fbfd8339bdb8f81e6f752a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Cómo: Invocar una operación de contrato de Windows Communication Foundation (Heredado)

En este tema se describe cómo invocar una operación de contrato de Windows Communication Foundation (WCF) mediante el Diseñador de flujo de trabajo de Windows heredado que tiene como destino la versión 3.5 de .NET Framework o el conocido como WinFX.

Después de arrastrar un **SendActivity** actividad en el cuadro de herramientas a la superficie de diseño de flujo de trabajo, importar un contrato existente. Determinar qué operación se invoca desde la que **SendActivity** actividad. Seleccione el contrato y sus operaciones a través de la [elija el cuadro de diálogo de operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md).

Además, si usa un archivo de configuración con su servicio, debe especificar un <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifica la configuración del extremo que la actividad de envío va a utilizar para conectar con el servicio de flujo de trabajo.

## <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Invocar una operación de contrato WCF desde una actividad SendActivity

1.  Haga doble clic en el **SendActivity** actividad en el diseñador o haga clic en los puntos suspensivos junto a la **ServiceOperationInfo** propiedad en el **propiedades** panel.

2.  Cuando el **elegir operación** abre el cuadro de diálogo, haga clic en **importación** en la esquina superior derecha del cuadro de diálogo.

     El [examinar y seleccionar un cuadro de diálogo de tipo de .NET (heredado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) se abre.

3.  Busque un ensamblado o proyecto que contenga el contrato deseado.

4.  Seleccione el contrato y haga clic en **Aceptar**.

5.  En **operaciones disponibles**, seleccione la operación que desea invocar y haga clic en **Aceptar**.

## <a name="to-specify-a-channel-token"></a>Para especificar un token de canal

1.  Seleccione la actividad <xref:System.Workflow.Activities.SendActivity> en el diseñador.

2.  En el **propiedades** panel, especifique un nombre para el <xref:System.Workflow.Activities.ChannelToken>. Este nombre únicamente identifica el token de canal.

3.  Expanda el nodo del token de canal y especifique un nombre para el extremo de cliente que va a utilizar en el campo <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>. La configuración del extremo del mismo nombre en el archivo de configuración se utiliza para configurar el canal.

4.  Cree la configuración del punto de conexión en el archivo de configuración, si aún no existe. Para obtener más información acerca de cómo configurar el cliente, consulte [información general sobre el cliente de WCF](/dotnet/framework/wcf/wcf-client-overview).

## <a name="see-also"></a>Vea también

- [Cuadro de diálogo Elegir operación (heredado)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Cómo: implementar una operación de contrato WCF (heredado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)