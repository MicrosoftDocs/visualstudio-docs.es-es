---
title: 'Cómo: crear una aplicación de servicio de flujo de trabajo WCF | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d901354b4a6a5f90ef75567131540405af7c9690
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Crear una aplicación de servicio de flujo de trabajo WCF

Las aplicaciones de servicio de flujo de trabajo [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] son servicios de comunicación distribuidos que transfieren mensajes entre clientes y ellos mismos entre límites de procesos. La implementación del contrato de servicios en el lado del servicio se efectúa mediante declaración a través de las actividades de flujo de trabajo de [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] de forma análoga a los servicios de flujo de trabajo heredados en .NET Framework 3.5.

### <a name="to-create-a-wcf-workflow-service-application"></a>Para crear una aplicación de servicio de flujo de trabajo WCF

1.  Inicie [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

2.  En el **archivo** menú, elija **New**y, a continuación, seleccione **proyecto...** .

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3.  En el **plantillas instaladas** panel, seleccione **WCF** o **flujo de trabajo** desde el **Visual C#** o **Visual Basic** agrupaciones dependiendo del lenguaje elegido.

4.  En el panel central, seleccione **aplicación de servicio de flujo de trabajo de WCF**.

5.  En el **nombre** cuadro, escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.

6.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para navegar hasta él.

7.  En el **solución** cuadro, seleccione esta opción para crear una nueva solución y, a continuación, haga clic en **Aceptar**.

    > [!NOTE]
    > Si desea agregar una aplicación de consola de flujos de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], haga clic en la solución de **el Explorador de soluciones**y seleccione **agregar**, a continuación, **Nuevo proyecto...** para abrir el **nuevo proyecto** cuadro de diálogo. Continúe de la forma descrita anteriormente en este procedimiento.

8.  La plantilla de proyecto crea una definición de servicio como XAML. Se abre el Diseñador de flujo de trabajo de Windows a la vista de diseño con un <xref:System.Activities.Statements.Sequence> actividad que contiene un conjunto de <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply> las actividades.

## <a name="see-also"></a>Vea también

- [Cómo crear una actividad](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)