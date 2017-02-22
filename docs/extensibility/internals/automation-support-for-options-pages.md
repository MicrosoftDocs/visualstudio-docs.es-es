---
title: "Compatibilidad de automatizaci&#243;n para las p&#225;ginas de opciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Páginas de opciones de herramientas [Visual Studio SDK], compatibilidad con la automatización"
  - "automatización [Visual Studio SDK], crear páginas de opciones de herramientas"
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Compatibilidad de automatizaci&#243;n para las p&#225;ginas de opciones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackages puede proporcionar personalizada **opciones** cuadros de diálogo para el **herramientas** menú \(páginas de opciones de herramientas\) en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y puede que estén disponibles para el modelo de automatización.  
  
## Páginas de opciones de herramientas  
 Para crear un **Opciones de herramientas** página, un VSPackage debe proporcionar una implementación de control de usuario devuelta en el entorno a través de la implementación de VSPackage la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> \(método\), \(o código administrado la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método\).  
  
 Es opcional, pero se recomienda encarecidamente, para permitir el acceso a esta nueva página a través del modelo de automatización. Puede hacerlo a través de los pasos siguientes:  
  
1.  Extender la <xref:EnvDTE._DTE.Properties%2A> objeto a través de la implementación de un objeto derivado de IDispatch.  
  
2.  Devolver una implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> \(método\) \(o en el código administrado la <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> \(método\)\) para el objeto derivado de IDispatch.  
  
3.  Cuando un consumidor de automatización llama el <xref:EnvDTE._DTE.Properties%2A> método personalizado **opción** utiliza el entorno de página de propiedades, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> método para obtener un personalizado **Opciones de herramientas** implementación de la automatización de la página.  
  
4.  El objeto de automatización del VSPackage, a continuación, se utiliza para proporcionar a cada uno de ellos <xref:EnvDTE.Property> devuelto por <xref:EnvDTE._DTE.Properties%2A>.  
  
 Para obtener un ejemplo de implementación de una página de opciones de herramientas personalizada, consulte [Muestras de VSSDK](../../misc/vssdk-samples.md).  
  
## Vea también  
 [Exponer objetos de proyecto](../../extensibility/internals/exposing-project-objects.md)