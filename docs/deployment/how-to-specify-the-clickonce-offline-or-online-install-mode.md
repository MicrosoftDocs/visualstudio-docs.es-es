---
title: "C&#243;mo: Especificar el modo de instalaci&#243;n en l&#237;nea y sin conexi&#243;n de ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "implementación ClickOnce, especificar el modo de instalación"
  - "modo de instalación ClickOnce"
  - "modo de instalación"
  - "aplicaciones sin conexión"
  - "aplicaciones en línea"
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# C&#243;mo: Especificar el modo de instalaci&#243;n en l&#237;nea y sin conexi&#243;n de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El `Install Mode` de una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] determina si la aplicación va a estar disponible sin conexión o en línea.  Cuando elija la opción **La aplicación sólo está disponible en línea**, el usuario deberá tener acceso a la ubicación de publicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] \(una página web o un recurso compartido de archivos\) para poder ejecutar la aplicación.  Cuando elija la opción **Esta aplicación también está disponible sin conexión**, la aplicación agregará las entradas al menú **Inicio** y al cuadro de diálogo **Agregar o quitar programas**; el usuario podrá ejecutar la aplicación cuando no esté conectado.  
  
 La propiedad `Install Mode` se puede establecer en la página **Publicar** del **Diseñador de proyectos**.  
  
 **Nota** `Install Mode` también se puede establecer usando el Asistente para publicación.  Para obtener más información, vea [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### Para hacer una aplicación ClickOnce sólo disponible en línea  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  En el área **Modo y configuración de instalación**, haga clic en el botón de opción **La aplicación sólo está disponible en línea**.  
  
### Para hacer que una aplicación ClickOnce esté disponible en línea o sin conexión  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  En el área **Modo y configuración de instalación**, haga clic en el botón de opción **La aplicación también está disponible sin conexión**.  
  
     Cuando se instala, la aplicación agrega las entradas al menú **Inicio** y a **Agregar o quitar programas** en el Panel de control.  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)