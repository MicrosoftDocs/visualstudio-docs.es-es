---
title: "C&#243;mo: Habilitar AutoStart para instalaciones con CD | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, AutoStart"
  - "implementación ClickOnce, instalación en CD o DVD"
  - "implementar aplicaciones [ClickOnce], instalación en CD o DVD"
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Habilitar AutoStart para instalaciones con CD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al implementar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mediante medios extraíbles como un CD\-ROM o DVD\-ROM, puede habilitar `AutoStart` para que se inicie la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] automáticamente cuando se inserte el medio.  
  
 La propiedad `AutoStart` se puede establecer en la página **Publicar** del **Diseñador de proyectos**.  
  
### Para habilitar AutoStart  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  Haga clic en el botón **Opciones**.  
  
     Aparece el cuadro de diálogo **Opciones de publicación**.  
  
4.  Haga clic en **Implementación**.  
  
5.  Active la casilla **En las instalaciones desde CD, el programa de instalación se inicia automáticamente al insertar el CD**.  
  
     Al publicar la aplicación, se copiará un archivo Autorun.inf en la ubicación de publicación.  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)