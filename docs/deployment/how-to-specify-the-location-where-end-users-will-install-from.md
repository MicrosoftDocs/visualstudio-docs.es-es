---
title: "C&#243;mo: Especificar la ubicaci&#243;n desde la que instalar&#225;n los usuarios finales | Microsoft Docs"
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
  - "implementar aplicaciones [ClickOnce], especificar instalación de URL"
  - "propiedad de instalación de dirección URL"
  - "instalación, especificar instalación de dirección URL"
  - "direcciones URL, especificar instalación de URL"
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# C&#243;mo: Especificar la ubicaci&#243;n desde la que instalar&#225;n los usuarios finales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se publica una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la ubicación donde los usuarios van a descargarla e instalarla no es necesariamente la ubicación donde se publica inicialmente la aplicación.  Por ejemplo, en algunas organizaciones un desarrollador podría publicar una aplicación en un servidor de ensayo y, a continuación, un administrador movería la aplicación a un servidor Web.  
  
 En este caso, puede utilizar la propiedad `Installation URL` para especificar el servidor Web donde los usuarios descargarán la aplicación.  Esto es necesario para que el manifiesto de la aplicación sepa dónde buscar actualizaciones.  
  
 La propiedad `Installation URL` se puede establecer en la página **Publicar** del **Diseñador de proyectos**.  
  
 **Nota** La propiedad `Installation URL` también se puede establecer mediante el **Asistente para publicación**.  Para obtener más información, vea [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### Para especificar una dirección URL de instalación  
  
1.  Con un proyecto seleccionado en el **Explorador de soluciones**, en el menú **Proyecto** haga clic en **Propiedades**.  
  
2.  Haga clic en la ficha **Publicar**.  
  
3.  En el campo de dirección URL de instalación, escriba la ubicación de la instalación mediante una dirección URL completa utilizando el formato http:\/\/www.microsoft.com\/Nombre de aplicación o una ruta UNC utilizando el formato \\\\Servidor\\Nombre de aplicación.  
  
## Vea también  
 [Cómo: Especificar dónde Visual Studio copia los archivos](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)