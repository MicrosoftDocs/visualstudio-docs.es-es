---
title: "C&#243;mo: Agregar y quitar dependencias de caracter&#237;sticas"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW"
  - "VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, características"
ms.assetid: 2b34c8d9-c975-4fe9-b8e0-52db4a6014ea
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# C&#243;mo: Agregar y quitar dependencias de caracter&#237;sticas
  Su característica de SharePoint puede depender de otra característica para la funcionalidad o los datos.  En estos casos, puede marcar estas otras características como dependencias de su característica.  De esta manera, el servidor de SharePoint se asegura de que todas las características dependientes están activadas antes de que se active su característica.  
  
## Agregar dependencias  
 Puede agregar otras características a la solución como dependencias.  De este modo se asegura de que las características necesarias se instalan y activan antes de que se instale su característica.  
  
#### Para agregar una dependencia a una característica de la solución  
  
1.  Abra el diseñador de características, expanda el nodo de **Dependencias de activación de característica** , y después elija el botón de **Add** .  
  
2.  En el cuadro de diálogo de **Agregar dependencias de activación de característica** , elija el botón de opción de **Agregar una dependencia a las características de la solución** , elija el título de la característica que desea agregar como dependencia, y después elija el botón de **Add** .  
  
     Puede agregar más de una característica eligiendo varios títulos mientras elige la tecla CTRL.  
  
## Agregar dependencias personalizadas  
 Puede agregar características que ya están implementadas en un servidor de SharePoint como una dependencia.  De esta manera, el proceso de activación de SharePoint comprueba para asegurarse de que se activan todas las características dependientes antes de que se instale su característica.  
  
#### Para agregar una dependencia por el identificador de la característica  
  
1.  Abra el diseñador de características, expanda el nodo de **Dependencias de activación de característica** , y después elija el botón de **Add** .  
  
2.  En el cuadro de diálogo de **Agregar dependencias de activación de característica** , elija el botón de opción de **Agregar una dependencia personalizada** .  
  
3.  En el cuadro de texto de **Id. de característica** , entre el GUID de la característica que desea marcar como una dependencia de activación, y elija el botón de **Add** .  
  
## Modificar dependencias personalizadas  
 Puede modificar las dependencias personalizadas que agregó previamente.  Sin embargo, las características dependientes que estén en la solución solo se pueden quitar, no modificar.  
  
#### Para cambiar una dependencia de una característica de la solución  
  
1.  Abra el diseñador de características, expanda el nodo de **Dependencias de activación de característica** .  
  
2.  Elija el nombre de la característica que desea modificar y, a continuación elija el botón de **edición** .  
  
3.  En el cuadro de diálogo de **Editar dependencia de activación de característica personalizada** , cambie el título, el identificador de la característica, o descripción, y elija el botón de **Enviar** .  
  
## Quitar dependencias  
  
#### Para quitar una dependencia de una característica de la solución  
  
1.  En el diseñador de características, expanda el nodo de **Dependencias de activación de característica** , elija el nombre de la característica que desea quitar y, a continuación el botón de **Quitar** .  
  
## Vea también  
 [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Cómo: Personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Cómo: Agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  