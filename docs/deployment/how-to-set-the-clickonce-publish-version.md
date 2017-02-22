---
title: "C&#243;mo: Establecer la versi&#243;n de publicaci&#243;n de ClickOnce | Microsoft Docs"
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
  - "implementación ClickOnce, establecer versión de publicación"
  - "propiedad de versión de publicación"
  - "publicar, ClickOnce"
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Establecer la versi&#243;n de publicaci&#243;n de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La propiedad `Publish Version` de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] determina si la aplicación que se está publicando se va a tratar como una actualización.  Cada vez que se incremente el número de versión, la aplicación se publicará como una actualización.  
  
 La propiedad `Publish Version` se puede establecer en la página **Publicar** del **Diseñador de proyectos**.  
  
> [!NOTE]
>  Hay una opción de proyecto que incrementará automáticamente la propiedad `Publish Version` cada vez que se publica la aplicación; esta opción se habilita de manera predeterminada.  Para obtener más información, vea [Cómo: Incrementar automáticamente la versión de publicación de ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### Para cambiar el campo Versión de publicación  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  En el campo **Versión de publicación**, incremente los números de versión **Mayor**, **Menor**, **Compilación** o **Revisión**.  
  
    > [!NOTE]
    >  Nunca se debe disminuir un número de versión; al hacerlo se puede producir un comportamiento de actualización imprevisible.  
  
## Vea también  
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Cómo: Incrementar automáticamente la versión de publicación de ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)