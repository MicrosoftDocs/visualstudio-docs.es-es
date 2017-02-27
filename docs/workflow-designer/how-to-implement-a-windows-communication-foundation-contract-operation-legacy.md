---
title: "C&#243;mo: Implementar una operaci&#243;n de contrato de Windows Communication Foundation (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# C&#243;mo: Implementar una operaci&#243;n de contrato de Windows Communication Foundation (Heredado)
En este tema se describe cómo implementar una operación de contrato de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] usando [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Después de arrastrar una actividad **ReceiveActivity** desde el cuadro de herramientas hasta la superficie de diseño de flujo de trabajo, cree un nuevo contrato de [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] o importe uno existente e implemente las operaciones.Puede seleccionar y crear el contrato y sus operaciones a través del [Elegir operación \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### Para implementar una operación de contrato WCF  
  
1.  Haga doble clic en la actividad **ReceiveActivity** del diseñador, o haga clic en los puntos suspensivos situados junto a la propiedad **ServiceOperationInfo** en el panel **Propiedades**.  
  
2.  Siga uno de los procedimientos siguientes:  
  
    -   Haga clic en **Agregar contrato** en la esquina superior derecha del cuadro de diálogo.De este modo creará un nuevo contrato y operación [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
         O bien,  
  
    -   Haga clic en **Importar** en la esquina superior derecha del cuadro de diálogo.Se abre [Examinar y seleccionar un cuadro de diálogo de tipo .NET \(Heredado\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).Busque un ensamblado o proyecto que contenga el contrato deseado.Seleccione el contrato y haga clic en **Aceptar**.  
  
     Después de que se crea o importa un contrato, puede agregarle nuevas operaciones.Para agregar una nueva operación, seleccione el contrato y haga clic en **Agregar operación** en la esquina superior derecha del cuadro de diálogo.Cuando haya terminado de agregar operaciones, continúe con el paso 3.  
  
3.  Seleccione la operación que desea asociar a la actividad **ReceiveActivity**.Puede manipular la definición de la operación cambiando el nombre, los parámetros, las propiedades y los valores de permiso de la operación.  
  
     Para cambiar el nombre, escriba el nuevo nombre en el cuadro de texto **Nombre de la operación**.  
  
     Haga clic en la pestaña **Parámetros** para acceder a los parámetros de la operación.Puede cambiar el nombre, el tipo o la dirección de un parámetro, así como agregar o eliminar parámetros de la operación.  
  
     Haga clic en la pestaña **Propiedades** para acceder al nivel de protección de la operación y a la funcionalidad de intercambio de mensajes compatible de la operación.  
  
     Haga clic en la pestaña **Permisos** para especificar qué grupos pueden implementar la operación.  
  
4.  Haga clic **Aceptar**, y la actividad **ReceiveActivity** mostrarán el nombre de la operación que está implementando.  
  
5.  Coloque las actividades de flujo de trabajo que va a utilizar para la implementación de esa operación dentro de la actividad **ReceiveActivity**.  
  
## Vea también  
 [Elegir operación \(Cuadro de diálogo\) \(Heredado\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Cómo: Invocar una operación de contrato WCF \(Heredado\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)