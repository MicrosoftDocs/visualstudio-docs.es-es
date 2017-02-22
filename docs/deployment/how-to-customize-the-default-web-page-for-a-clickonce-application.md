---
title: "C&#243;mo: Personalizar la p&#225;gina web predeterminada para una aplicaci&#243;n ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "Publish.htm (página web)"
  - "página web predeterminada de implementación ClickOnce"
  - "implementar aplicaciones [ClickOnce], publicación"
  - "publicación, ClickOnce"
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Personalizar la p&#225;gina web predeterminada para una aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al publicar una aplicación ClickOnce en Web, se genera automáticamente una página Web y se publica junto con la aplicación.  La página predeterminada contiene el nombre de la aplicación y los vínculos para instalarla, instalar los requisitos previos u obtener acceso a la ayuda de MSDN.  
  
> [!NOTE]
>  Los vínculos que ve en la página dependen del equipo donde se ve la página y qué requisitos previos está incluyendo.  
  
 El nombre predeterminado de la página Web es Publish.htm; puede cambiarlo en el **Diseñador de proyectos**.  Para obtener más información, vea [Cómo: Especificar una página de publicación para una aplicación ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 La página Web Publish.htm sólo se publica si se detecta una versión más reciente.  
  
> [!NOTE]
>  Los cambios que realiza en la configuración **Publicar** no afectarán a la página Publish.htm con una excepción: si agrega o quita los requisitos previos después de la publicación inicial, la lista de estos requisitos ya no será exacta.  Necesitará editar el texto del vínculo de requisitos previos para reflejar los cambios.  
  
### Para personalizar la página Web de publicación  
  
1.  Publique su aplicación ClickOnce en una ubicación Web.  Para obtener más información, vea [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  En el servidor Web, abra el archivo Publish.htm en el Diseñador Web de Visual u otro editor HTML.  
  
3.  Personalice la página como desee y guárdela.  
  
4.  Opcional.  Para evitar que Visual Studio sobrescriba la página web de publicación personalizada, desactive **Generar automáticamente la página web de implementación después de cada publicación** en el cuadro de diálogo Opciones de publicación.  
  
## Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Cómo: Especificar una página de publicación para una aplicación ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)