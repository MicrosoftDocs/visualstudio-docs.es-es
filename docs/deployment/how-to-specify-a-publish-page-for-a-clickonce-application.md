---
title: "C&#243;mo: Especificar una p&#225;gina de publicaci&#243;n para una aplicaci&#243;n ClickOnce | Microsoft Docs"
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
  - "implementación ClickOnce, especificar página de publicación"
  - "implementar aplicaciones [ClickOnce], especificar página de publicación"
  - "propiedad de página de publicación"
  - "publicar, ClickOnce"
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# C&#243;mo: Especificar una p&#225;gina de publicaci&#243;n para una aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se publica una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], se genera y se publica una página Web predeterminada \(publish.htm\) junto con la aplicación.  Esta página contiene el nombre de la aplicación, un vínculo para instalarla o cualquier requisito previo, y un vínculo a un tema de la Ayuda que describa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  La propiedad **Página de publicación** del proyecto permite especificar un nombre para la página web de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Una vez especificada la página de publicación, la siguiente vez que publique, se copiará en la ubicación de publicación; no se reemplazará si vuelve a publicar.  Si desea personalizar la apariencia de la página, puede hacerlo sin preocuparse de perder los cambios.  Para obtener más información, vea [Cómo: Personalizar la página web predeterminada para ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 La propiedad **Página de publicación** se puede establecer en el cuadro de diálogo **Opciones de publicación**, al que se puede obtener acceso desde el panel **Publicar** del **Diseñador de proyectos**.  
  
### Para especificar una página Web personalizada para una aplicación ClickOnce  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Seleccione el panel **Publicar**.  
  
3.  Haga clic en el botón **Opciones** para abrir el cuadro de diálogo **Opciones de publicación**.  
  
4.  Haga clic en **Implementación**.  
  
5.  En el cuadro de diálogo **Opciones de publicación**, asegúrese de que está activada la casilla **Abrir la página Web de implementación después de publicar** \(debe estar activada de forma predeterminada\).  
  
6.  En el cuadro **Implementación de la página Web:**, especifique el nombre de la página Web y, a continuación, haga clic en **Aceptar**.  
  
### Para evitar que se inicie la página de publicación cada vez que se publica  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Seleccione el panel **Publicar**.  
  
3.  Haga clic en el botón **Opciones** para abrir el cuadro de diálogo **Opciones de publicación**.  
  
4.  Haga clic en **Implementación**.  
  
5.  En el cuadro de diálogo **Opciones de publicación**, desactive la casilla **Abrir la página Web de implementación después de publicar**.  
  
## Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Cómo: Personalizar la página web predeterminada para ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)