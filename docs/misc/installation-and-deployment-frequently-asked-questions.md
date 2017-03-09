---
title: "Preguntas m&#225;s frecuentes sobre la instalaci&#243;n y la implementaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "implementar [SDK de Visual Studio]"
  - "LCID [SDK de Visual Studio]"
  - "instalación [SDK de Visual Studio]"
ms.assetid: 4ac62bf3-e335-4899-9074-89bcd004dc65
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Preguntas m&#225;s frecuentes sobre la instalaci&#243;n y la implementaci&#243;n
En este tema se trata preguntas de la comunidad de usuarios de [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] sobre la instalación e implementación.  El tema se seguirá actualizado con el nuevo contenido de la comunidad.  
  
## Contenido  
  
-   [Determinar el LCID de una instalación mediante programación de Visual Studio](#DeterminingtheLCIDofaVisualStudioInstallationProgrammatically)  
  
##  <a name="DeterminingtheLCIDofaVisualStudioInstallationProgrammatically"></a> Determinar el LCID de una instalación mediante programación de Visual Studio  
 **q:** ¿Hay una manera mediante programación de determinar el LCID de una instalación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ?  
  
 **a:**  <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale2.GetUILocale%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IUIHostLocale.GetUILocale%2A>devolverá un LCID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] actualmente en uso.  
  
## Vea también  
 [Publicar un producto](../misc/releasing-a-visual-studio-integration-product.md)