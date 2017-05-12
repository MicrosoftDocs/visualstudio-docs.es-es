---
title: "C&#243;mo: Modificar una configuraci&#243;n de implementaci&#243;n de SharePoint"
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
  - "VS.SharePointTools.Project.DeploymentConfig"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, implementar"
ms.assetid: bff1895b-d3fe-4ec0-ba91-f8884dc35957
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# C&#243;mo: Modificar una configuraci&#243;n de implementaci&#243;n de SharePoint
  Puede crear una configuración de implementación o modificar una existente.  Por ejemplo, podría ejecutar un paso único o cambiar el orden de los pasos del proceso de implementación.  Le puede interesar crear o modificar las configuraciones de implementación porque las configuraciones integradas y agregadas mediante programación no se pueden cambiar.  
  
## Crear una configuración de implementación de SharePoint  
  
#### Para crear una configuración de implementación de SharePoint  
  
1.  En **Explorador de soluciones**, elija un proyecto de SharePoint y, a continuación, en la barra de menús, elija **Project**, *ProjectName***Propiedades**.  
  
2.  En la pestaña de **sharepoint** , elija el botón de **new** .  
  
     Aparecerá el cuadro de diálogo **Agregar nueva configuración de implementación**.  
  
3.  En el cuadro de texto de **Name** , escriba un nombre para la configuración de implementación.  
  
4.  En el panel de **Pasos de implementación disponibles** , elija los pasos que desea agregar a la configuración de implementación, elija el botón \(de**\>**\), y después elija el botón de **Aceptar** .  
  
    > [!NOTE]  
    >  Si ha configurado un comando de la pre\- implementación o un comando de la POST\- implementación, estos pasos solo se ejecutan si los agrega a una configuración de implementación personalizada.  
  
## Cambiar la configuración de implementación activa  
  
#### Para cambiar la configuración de implementación activa  
  
1.  En **Explorador de soluciones**, elija un proyecto de SharePoint y, a continuación, en la barra de menús, elija **Project**, *ProjectName***Propiedades**.  
  
2.  Elija la ficha de **sharepoint** .  
  
3.  En el cuadro de lista de **Configuración de implementación activa** , elija el nombre de la configuración de implementación que desee utilizar.  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  