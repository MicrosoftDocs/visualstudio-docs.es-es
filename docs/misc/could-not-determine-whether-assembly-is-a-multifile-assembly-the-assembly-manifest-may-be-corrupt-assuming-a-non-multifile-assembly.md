---
title: "No se pudo determinar si &#39;ensamblado&#39; es un ensamblado de m&#250;ltiples archivos. El manifiesto del ensamblado podr&#237;a estar da&#241;ado. Se supone que el ensamblado no es de m&#250;ltiples archivos. | Microsoft Docs"
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
  - "vs.tasklisterror.unknownscatterstatusforcopy"
ms.assetid: be49d3f2-b091-488c-8579-e27ef09d9c80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# No se pudo determinar si &#39;ensamblado&#39; es un ensamblado de m&#250;ltiples archivos. El manifiesto del ensamblado podr&#237;a estar da&#241;ado. Se supone que el ensamblado no es de m&#250;ltiples archivos.
El sistema del proyecto no pudo leer un ensamblado al que hacía referencia su proyecto y, por tanto, no puede determinar si hace referencia a un ensamblado de múltiples archivos. Por este motivo, es posible que el ensamblado no se copie correctamente al directorio de salida.  
  
 **Para corregir este error**  
  
-   Reinstale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(si el ensamblado venía incluido con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o .NET Framework\).  
  
     o bien  
  
-   Reinstale el control de terceros adecuado.  
  
     Este error no impedirá que se compile el proyecto. Sin embargo, podría producirse un error en tiempo de ejecución.  
  
## Vea también  
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: agregar o quitar referencias mediante el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/es-es/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)