---
title: "Inicializar correlaci&#243;n (cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "InitializeCorrelation.UI"
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Inicializar correlaci&#243;n (cuadro de di&#225;logo)
El cuadro de diálogo **Inicializar correlación** se usa en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] para editar la propiedad <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> de una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation>.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)] el tema [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).  
  
 En la tabla siguiente se describen los elementos de la interfaz de usuario del cuadro de diálogo **Inicializar correlación**.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------------------------------|-----------------|  
|**Correlación**|El objeto <xref:System.ServiceModel.Activities.CorrelationHandle> de la correlación que se va a inicializar.|  
|**Inicializar el**|Un par clave\-valor que contiene los datos que se van a inicializar.Esto corresponde a la propiedad <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>.Un ejemplo de par clave\-valor válido sería una clave denominada "OrderID" que se asocia a una variable denominada OrderID.|  
  
## Para iniciar el cuadro de diálogo Inicializar correlación  
  
-   Haga clic en **Ver** en el diseñador de actividades **InitializeCorrelation** o seleccione una actividad <xref:System.ServiceModel.Activities.InitializeCorrelation> en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] y, a continuación, haga clic en el botón de puntos suspensivos junto a la propiedad <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> en la cuadrícula de propiedades.  
  
## Vea también  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)