---
title: "C&#243;mo: Establecer comandos de implementaci&#243;n de SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, implementar"
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# C&#243;mo: Establecer comandos de implementaci&#243;n de SharePoint
  Puede personalizar el proceso de implementación estableciendo comandos anteriores y posteriores a la implementación.  Estos comandos se ejecutan antes y después de otras acciones de implementación cuando se depuran las soluciones de SharePoint en Visual Studio.  
  
### Para agregar un comando anterior a la implementación  
  
1.  En la barra de menús, elija **Proyecto**, *ProjectName* **Propiedades**.  
  
2.  Elija la ficha de **sharepoint** .  
  
3.  En el cuadro de texto de **Línea de comandos anterior a la implementación** , escriba MS\-DOS o comandos de MSBuild para personalizar este paso.  
  
     Por ejemplo, para enumerar el contenido del directorio antes de que se complete la implementación, escriba en **dir**.  
  
### Para agregar un comando posterior a la implementación  
  
1.  En la barra de menús, elija **Proyecto**, *ProjectName* **Propiedades**.  
  
2.  Elija la ficha de **sharepoint** .  
  
3.  En el cuadro de texto de **Línea de comandos posterior a la implementación** , escriba MS\-DOS o comandos de MSBuild para personalizar este paso.  
  
     Por ejemplo, para enumerar el contenido del directorio después de que se complete la implementación, escriba en **dir**.  Para utilizar una variable de MSBuild para copiar el ensamblado del directorio de compilación, escriba en **copy $\(TargetPath\) c:\\DeploymentDirectory**.  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  