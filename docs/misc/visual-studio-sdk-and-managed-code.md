---
title: "SDK de Visual Studio y c&#243;digo administrado | Microsoft Docs"
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
  - "VSIP, acerca del código administrado"
ms.assetid: 16b3d88e-b5d8-49a5-a5d7-07cbb0b7e4fc
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# SDK de Visual Studio y c&#243;digo administrado
*El código administrado* es el código que se escribe en cualquier lenguaje dirigido a Common Language \(CLR\) Runtime, como [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], o [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  Independientemente del lenguaje que está escrito, todo el código administrado se compila en el Lenguaje intermedio de Microsoft \(MSIL\) en lugar de código nativo.  
  
## Compatibilidad con el entorno para VSPackages administrado  
 Para poder crear un VSPackage o un proyecto con un lenguaje administrado como [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona lo siguiente:  
  
-   Los ensamblados de interoperabilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], que habilitan VSPackages escrito en código administrado para interoperar con el entorno de desarrollo integrado \(COM\) no administrada de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(IDE\).  Para obtener más información, vea [Utilizar ensamblados de interoperabilidad de Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md).  
  
-   Un conjunto de clases administradas de paquete \(MPF\) que proporciona una abstracción de alto nivel para ejecutar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el IDE.  Estas clases encapsulan algunos la mayoría de las interfaces y los tipos utilizados en los ensamblados de interoperabilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Reduce considerablemente la cantidad de trabajo que debe hacer para proporcionar la funcionalidad básica de un VSPackage o proyecto.  Para obtener más información, vea [Clases de Managed Package Framework](../misc/managed-package-framework-classes.md).  
  
-   un conjunto de ejemplos básicos de VSPackage escritos en código administrado.  Los ejemplos administrados compilados en un ejemplo de un simple, \- VSPackage funcional mostrar totalmente un editor básico, una ventana de herramientas, un extensor de objeto, y otros componentes.  Para obtener más información, vea [Muestras de VSSDK](../misc/vssdk-samples.md).  
  
## Vea también  
 [VSPackages administrado](../misc/managed-vspackages.md)   
 [Utilizar ensamblados de interoperabilidad de Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [Clases de Managed Package Framework](../misc/managed-package-framework-classes.md)