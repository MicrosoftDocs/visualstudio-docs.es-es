---
title: "C&#243;mo: Incrementar autom&#225;ticamente la versi&#243;n de publicaci&#243;n de ClickOnce | Microsoft Docs"
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
  - "implementación ClickOnce, aumentar la versión de publicación automáticamente"
  - "implementar aplicaciones [ClickOnce], aumentar la versión de publicación automáticamente"
  - "propiedad de versión de publicación, aumentar"
  - "publicar, ClickOnce"
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# C&#243;mo: Incrementar autom&#225;ticamente la versi&#243;n de publicaci&#243;n de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si se publica una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] y se modifica la propiedad `Publish Version`, la aplicación se publicará como una actualización.  De manera predeterminada, Visual Studio incrementa automáticamente el número de `Revision` de `Publish Version` cada vez que se publica la aplicación.  
  
 Puede deshabilitar este comportamiento en la página **Publicar** del **Diseñador de proyectos**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para deshabilitar automáticamente el incremento de la versión de publicación  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  En la sección **Versión de publicación**, desactive la casilla **Incrementar revisión automáticamente con cada versión**.  
  
## Vea también  
 [Cómo: Establecer la versión de publicación de ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)