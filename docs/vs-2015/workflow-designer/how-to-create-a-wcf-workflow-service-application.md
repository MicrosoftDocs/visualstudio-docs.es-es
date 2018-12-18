---
title: 'Cómo: crear una aplicación de servicio de flujo de trabajo WCF | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 8632d8cf942fe4a06f12d324fea1f6f567080981
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228441"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Crear una aplicación de servicio de flujo de trabajo WCF
Las aplicaciones de servicio de flujo de trabajo [!INCLUDE[indigo1](../includes/indigo1-md.md)] son servicios de comunicación distribuidos que transfieren mensajes entre clientes y ellos mismos entre límites de procesos. La implementación del contrato de servicios en el lado del servicio se efectúa mediante declaración a través de las actividades de flujo de trabajo de [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] de forma análoga a los servicios de flujo de trabajo heredados en .NET Framework 3.5.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>Para crear una aplicación de servicio de flujo de trabajo WCF  
  
1.  Inicie [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  En el **archivo** menú, elija **New**y, a continuación, seleccione **proyecto...** .  
  
     Aparece el cuadro de diálogo **Nuevo proyecto** .  
  
3.  En el **plantillas instaladas** panel, seleccione **WCF** o **flujo de trabajo** desde el **Visual C#** o **Visual Basic** agrupaciones dependiendo del lenguaje elegido.  
  
4.  En el panel central, seleccione **aplicación de servicio de flujo de trabajo de WCF**.  
  
5.  En el **nombre** , escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
6.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.  
  
7.  En el **solución** , seleccione crear una nueva solución y, a continuación, haga clic en **Aceptar**.  
  
    > [!NOTE]
    >  Si desea agregar una aplicación de consola de flujo de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../includes/vs2010-md.md)], haga clic en la solución de **el Explorador de soluciones**y seleccione **agregar**, a continuación,  **Nuevo proyecto...** Para abrir el **nuevo proyecto** cuadro de diálogo. Continúe de la forma descrita anteriormente en este procedimiento.  
  
8.  La plantilla de proyecto crea una definición de servicio como XAML. Se abre [!INCLUDE[wfd1](../includes/wfd1-md.md)] en la vista de diseño con una actividad <xref:System.Activities.Statements.Sequence> que contiene un conjunto de actividades <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply>.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear una actividad](http://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)