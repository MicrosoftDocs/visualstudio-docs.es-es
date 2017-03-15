---
title: "Implementaci&#243;n de la interfaz IVsPackage | Microsoft Docs"
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
  - "Interfaz IVsPackage"
  - "interfaces, implementación de IVsPackages"
ms.assetid: 0c76b2e1-ce63-47fc-93ee-847cad281fc1
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Implementaci&#243;n de la interfaz IVsPackage
todo el VSPackages debe implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> .  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] llama a los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> para inicializar y cerrar VSPackages, obtener páginas de propiedades asociadas, y por otras razones.  la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> es la interfaz de la puerta de enlace entre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y un VSPackage.  
  
 Puede escribir un VSPackage administrado como una subclase de la clase de <xref:Microsoft.VisualStudio.Shell.Package> , que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> en nombre.  Para obtener más información, vea [VSPackages administrado](../misc/managed-vspackages.md).  
  
> [!NOTE]
>  Gran parte del código no administrado en la sección de integración de Visual Studio de [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] utiliza Active Template \(ATL\) Library.  No necesita utilizar ATL para crear VSPackages, pero debe entender ATL para entender el código de ejemplo.  
  
## Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)