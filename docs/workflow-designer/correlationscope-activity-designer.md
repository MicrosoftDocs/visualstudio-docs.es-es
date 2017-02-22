---
title: "Dise&#241;ador de actividades CorrelationScope | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.CorrelationScope.UI"
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades CorrelationScope
El diseñador de actividades **CorrelationScope** se utiliza para crear y configurar una actividad <xref:System.ServiceModel.Activities.CorrelationScope> que proporciona administración implícita de actividades de mensajería secundarias mediante el uso de un objeto <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
## Actividad CorrelationScope  
 La propiedad <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> especifica la clase <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para administrar las actividades de mensajería secundarias.Las actividades <xref:System.ServiceModel.Activities.Send> y <xref:System.ServiceModel.Activities.Receive> que se incluyen en la propiedad <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> se configuran para utilizar la propiedad <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de la actividad <xref:System.ServiceModel.Activities.CorrelationScope> que sirve de contenedor para efectuar la correlación.  
  
### Utilizar el diseñador de actividades CorrelationScope  
 El diseñador de actividades **CorrelationScope** se puede encontrar en la categoría **Mensajería** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** a la izquierda de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **CorrelationScope** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en a la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Esto crea una actividad <xref:System.ServiceModel.Activities.CorrelationScope> con un valor **DisplayName** predeterminado de CorrelationScope.La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **CorrelationScope** o en el cuadro **DisplayName** de la ventana **Propiedades**.  
  
 Para especificar la propiedad <xref:System.ServiceModel.Activities.CorrelationHandle> que utilizan las actividades de mensajería secundarias, haga clic en el botón de puntos suspensivos junto al campo **CorrelatesWith** en la ventana **Propiedades** para mostrar el cuadro de diálogo **Editor de expresiones**.Esta propiedad también se puede establecer en la superficie del diseñador de actividades.  
  
 Las actividades dentro del ámbito de la correlación se especifican al colocar sus diseñadores dentro del cuadro **Cuerpo** en el diseñador **CorrelationScope**.  
  
### Propiedades CorrelationScope  
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.CorrelationScope> y se describe cómo se utilizan en el diseñador.Estas propiedades se pueden editar en la ventana **Propiedades** o en la superficie del diseñador [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] y, en muchas ocasiones, en ambos.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre opcional descriptivo de la actividad <xref:System.ServiceModel.Activities.InitializeCorrelation>.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Especifica la propiedad <xref:System.ServiceModel.Activities.CorrelationHandle> que se utiliza para administrar las actividades de mensajería secundarias.Si no se establece esta propiedad, <xref:System.ServiceModel.Activities.CorrelationScope> crea una propiedad <xref:System.ServiceModel.Activities.CorrelationHandle> implícita automáticamente.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Especifica las actividades dentro del ámbito de la correlación.|  
  
## Vea también  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Enviar](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)