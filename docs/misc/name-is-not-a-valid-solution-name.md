---
title: "&lt;name&gt; is not a valid solution name. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALIDSOLUTIONNAME"
  - "vs.message.0x800A00D3"
ms.assetid: 79b7870d-16bd-4527-8ce6-ffb015e7e330
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid solution name.
Este error se produce normalmente cuando se especifica el comando `File.NewProject` en la ventana **Comando** o el cuadro **Buscar\/Comando** con un valor de formato incorrecto para el argumento \/sln:*solutionname*.  
  
### Para corregir este error  
  
1.  Vuelva a escribir la sintaxis del comando y omita el argumento opcional \/sln:*solutionname*.  Se generará automáticamente un nombre de solución único.  
  
     \-O bien\-  
  
     Compruebe que el nombre de solución no contiene espacios iniciales o finales y no es una palabra reservada.  Las palabras reservadas incluyen NUL, CON, AUX, COM*x* y LPT*x*, donde *x* es un dígito del 1 al 9.  
  
## Vea también  
 [Ventana de comandos](../ide/reference/command-window.md)