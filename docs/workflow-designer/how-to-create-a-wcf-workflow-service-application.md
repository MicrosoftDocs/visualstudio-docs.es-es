---
title: "Crear una aplicaci&#243;n de servicio de flujo de trabajo WCF | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
caps.handback.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Crear una aplicaci&#243;n de servicio de flujo de trabajo WCF
Las aplicaciones de servicio de flujo de trabajo [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] son servicios de comunicación distribuidos que transfieren mensajes entre clientes y ellos mismos entre límites de procesos.La implementación del contrato de servicios en el lado del servicio se efectúa mediante declaración a través de las actividades de flujo de trabajo de [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] de forma análoga a los servicios de flujo de trabajo heredados en .NET Framework 3.5.  
  
### Para crear una aplicación de servicio de flujo de trabajo WCF  
  
1.  Inicie [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto**.  
  
3.  En el panel **Plantillas instaladas**, seleccione **WCF** o **Flujo de trabajo** en las agrupaciones **Visual C\#** o **Visual Basic** en función del lenguaje elegido.  
  
4.  En el panel del centro, seleccione **Aplicación de servicio de flujo de trabajo WCF**.  
  
5.  En el cuadro **Nombre**, escriba un nombre descriptivo para que resulte sencillo identificar el proyecto.  
  
6.  En el cuadro **Ubicación**, escriba el directorio en el que desee guardar el proyecto o haga clic en **Examinar** para navegar hasta él.  
  
7.  En el cuadro **Solución**, seleccione la creación de una nueva solución y, a continuación, haga clic en **Aceptar**.  
  
    > [!NOTE]
    >  Si desea agregar una aplicación de consola de flujos de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], haga clic con el botón secundario en la solución en el **Explorador de soluciones**, seleccione **Agregar** y luego **Nuevo proyecto...** para abrir el cuadro de diálogo **Nuevo proyecto**.Continúe de la forma descrita anteriormente en este procedimiento.  
  
8.  La plantilla de proyecto crea una definición de servicio como XAML.Se abre [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] en la vista de diseño con una actividad <xref:System.Activities.Statements.Sequence> que contiene un conjunto de actividades <xref:System.ServiceModel.Activities.SendReply> y <xref:System.ServiceModel.Activities.Receive>.  
  
## Vea también  
 [Cómo: Crear una actividad](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)