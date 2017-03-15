---
title: "Ya no se admiten instrucciones &#39;Get&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30829"
  - "bc30829"
helpviewer_keywords: 
  - "BC30829"
ms.assetid: 8d798357-7efb-4423-9808-8b20777b97ba
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ya no se admiten instrucciones &#39;Get&#39;.
Ya no se admiten instrucciones `Get`. La función de E\/S de archivos está disponible en el espacio de nombres `Microsoft.VisualBasic`.  
  
 `Get` no se admite para operaciones de archivo y solo puede usarse en la sintaxis del procedimiento de propiedad.  
  
 **Identificador de error:** BC30829  
  
### Para corregir este error  
  
1.  Realice operaciones de archivo mediante los miembros de las funciones de tiempo de ejecución `System.IO`, `FileSystemObject` y [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Vea también  
 [Procesar unidades, directorios y archivos](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/index)   
 [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Acceso a archivos con Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)