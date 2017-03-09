---
title: "Configuration name is not valid. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALID_CFG_NAME"
  - "vs.message.0x800A00B7"
ms.assetid: aa439582-0863-41d3-825c-7c45b1773cde
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Configuration name is not valid.
Este error ocurre normalmente cuando el nombre especificado para la configuración de compilación de generación incluye caracteres no válidos, como \<, \>, &#124; y \*.  
  
### Para corregir este error  
  
1.  Compruebe que el nombre de configuración no contiene los siguientes caracteres: \<, \>, &#124;, \*, ;, \\, \/, &, %, ", ., \#, ? o un espacio inicial o final.  Además, el nombre de configuración no puede utilizar nombres reservados para Windows o DOS, tales como "nul", "aux", "con', "com\#", "lpt\#", etc.  
  
2.  Vuelva a escribir el nombre.  
  
## Vea también  
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)