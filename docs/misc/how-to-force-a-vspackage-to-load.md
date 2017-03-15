---
title: "Procedimiento: forzar la carga de un VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, forzar carga"
  - "VSPackages, cargar"
ms.assetid: 05f4dc3f-3c9a-45ea-96da-986553b5c5f2
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Procedimiento: forzar la carga de un VSPackage
VSPackages se carga normalmente sólo cuando la funcionalidad de acompañamiento se necesita para finalizar un proceso.  En algunas circunstancias, sin embargo, un Paquete puede tener que forzar a otro Paquete que se va a cargar.  Por ejemplo, un ligeros VSPackage podría cargar un VSPackage más grande en un contexto de programación que no está disponible como CMDUIContext.  
  
 Puede utilizar el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> para forzar un VSPackage para cargar.  
  
### para forzar un VSPackage para cargar  
  
-   Inserte este código en el método de <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> de VSPackage que obliga a otro Paquete para cargar:  
  
     [!code-cs[ForceVSPackageLoad#01](../misc/codesnippet/CSharp/how-to-force-a-vspackage-to-load_1.cs)]  
  
     Cuando se inicializa el Paquete, también `PackageToBeLoaded` para cargar.  
  
## Programación eficaz  
 La carga force no se debe utilizar para la comunicación de VSPackage.  Utilice [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md) en su lugar.  
  
## Vea también  
 [Administración de VSPackages](../extensibility/managing-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)