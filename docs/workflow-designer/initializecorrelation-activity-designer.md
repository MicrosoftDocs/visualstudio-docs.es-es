---
title: "Dise&#241;ador de actividades InitializeCorrelation | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.InitializeCorrelation.UI"
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades InitializeCorrelation
El diseñador de actividades **InitializeCorrelation** se utiliza para crear y configurar una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> que se utiliza para establecer una correlación entre los mensajes antes de enviarlos o recibirlos.  
  
## Actividad InitializeCorrelation  
 Una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> se utiliza para inicializar las correlaciones sin enviar o recibir un mensaje.Normalmente una correlación se inicializa cuando se envía o recibe un mensaje.Si se debe establecer una correlación antes de enviar o recibir un mensaje, utilice <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar la correlación.  
  
### Utilizar el diseñador de actividades InitializeCorrelation  
 El diseñador de actividades **InitializeCorrelation** se puede encontrar en la categoría **Mensajería** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **InitializeCorrelation** se puede arrastrar desde el **Cuadro de herramientas** y colocar en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].De esta forma se crea una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de InitializeCorrelation.<xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **InitializeCorrelation** o en el cuadro **DisplayName** de la ventana **Propiedades**.  
  
 Se puede especificar <xref:System.ServiceModel.Activities.CorrelationHandle> en el campo **Correlación** de la ventana **Propiedades** en la superficie del diseñador de actividades **InitializeCorrelation**.  
  
 Al hacer clic en el botón con puntos suspensivos junto al campo **CorrelationData** en la ventana **Propiedades** o en el texto con la sugerencia "Ver..." en la superficie del diseñador de actividades **InitializeCorrelation** se muestra el cuadro de diálogo **Inicializar correlación** donde puede especificar el identificador de correlación y los pares clave\-valor que se usan para la inicialización.[!INCLUDE[crabout](../test/includes/crabout_md.md)] cómo usar este cuadro de diálogo, vea el tema [Editor de colección de tipos \(cuadro de diálogo\)](../workflow-designer/type-collection-editor-dialog-box.md).  
  
### Propiedades InitializeCorrelation  
 En la tabla siguiente se muestran las propiedades <xref:System.ServiceModel.Activities.InitializeCorrelation> y se describe cómo se utilizan en el diseñador.Estas propiedades se pueden editar en ventana **Propiedades** o en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo de la actividad <xref:System.ServiceModel.Activities.InitializeCorrelation>.El valor predeterminado es InitializeCorrelation.<br /><br /> Aunque no es obligatorio utilizar un valor no predeterminado para la propiedad <xref:System.Activities.Activity.DisplayName%2A> descriptiva, se recomienza utilizar uno.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> se utiliza para asociar las actividades de flujo de trabajo en la correlación.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Un diccionario de datos de correlación que relaciona los mensajes con la instancia de flujo de trabajo.<br /><br /> Use el cuadro de diálogo **Inicializar correlación** para configurar <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>.[!INCLUDE[crabout](../test/includes/crabout_md.md)] el uso de este cuadro de diálogo, vea el tema [Editor de colección de tipos \(cuadro de diálogo\)](../workflow-designer/type-collection-editor-dialog-box.md).|  
  
## Vea también  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Enviar](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)