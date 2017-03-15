---
title: "Error de MSBuild MSB3252 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB3252"
helpviewer_keywords: 
  - "MSB3252"
ms.assetid: 4e6982b8-84b3-4d21-94e1-05cc10bf1393
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3252
**MSB3252: El proyecto tiene una referencia al ensamblado \< nombre \>.  Este ensamblado no forma parte de .NET Framework Client Profile.  La ausencia de esta referencia puede producir errores de compilación o errores en tiempo de ejecución.**  
  
 Se realizó una llamada a un miembro de un ensamblado, o un ensamblado dependiente, que no forma parte de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  Por tanto, la llamada no se pudo resolver y la aplicación no se pudo compilar.  
  
 Para obtener más información acerca de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], vea [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
### Para corregir este error  
  
-   Quite la referencia al ensamblado especificado de su proyecto o especifique como destino la versión completa de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en lugar de la biblioteca del subconjunto de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  Para obtener más información acerca de cómo se especifica como destino la versión completa de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], vea [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## Vea también  
 [Versión de .NET Framework de destino y plataforma de destino](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)