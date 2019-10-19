---
title: 'Cómo: crear una aplicación de servicio de flujo de trabajo WCF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9bf941babd943c6856809a13de847b62745b2056
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605011"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Crear una aplicación de servicio de flujo de trabajo WCF
Las aplicaciones de servicio de flujo de trabajo [!INCLUDE[indigo1](../includes/indigo1-md.md)] son servicios de comunicación distribuidos que transfieren mensajes entre clientes y ellos mismos entre límites de procesos. La implementación del contrato de servicios en el lado del servicio se efectúa mediante declaración a través de las actividades de flujo de trabajo de [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] de forma análoga a los servicios de flujo de trabajo heredados en .NET Framework 3.5.

### <a name="to-create-a-wcf-workflow-service-application"></a>Para crear una aplicación de servicio de flujo de trabajo WCF

1. Inicie [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. En el menú **archivo** , seleccione **nuevo**y, a continuación, seleccione **proyecto.** .

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3. En el panel **plantillas instaladas** , **Seleccione WCF** o **flujo de trabajo** desde las agrupaciones **Visual C#**  o **Visual Basic** en función del lenguaje que elija.

4. En el panel central, seleccione **aplicación de servicio de flujo de trabajo WCF**.

5. En el cuadro **nombre** , escriba un nombre descriptivo para el proyecto con el fin de facilitar su identificación.

6. En el cuadro **Ubicación** , escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.

7. En el cuadro **solución** , seleccione crear una nueva solución y, a continuación, haga clic en **Aceptar**.

    > [!NOTE]
    > Si desea agregar una aplicación de consola de flujos de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../includes/vs2010-md.md)], haga clic con el botón derecho en la solución en **Explorador de soluciones**y seleccione **Agregar**y luego **nuevo proyecto.** . para abrir el cuadro de diálogo **nuevo proyecto** . Continúe de la forma descrita anteriormente en este procedimiento.

8. La plantilla de proyecto crea una definición de servicio como XAML. Se abre [!INCLUDE[wfd1](../includes/wfd1-md.md)] en la vista de diseño con una actividad <xref:System.Activities.Statements.Sequence> que contiene un conjunto de actividades <xref:System.ServiceModel.Activities.Receive> y <xref:System.ServiceModel.Activities.SendReply>.

## <a name="see-also"></a>Vea también
 [Cómo: crear una actividad](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)