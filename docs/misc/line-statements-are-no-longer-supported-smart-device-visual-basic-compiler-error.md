---
title: "Ya no se admiten instrucciones &#39;Line&#39; (error del compilador de Smart Device/Visual Basic). | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30768"
  - "bc30768"
helpviewer_keywords: 
  - "BC30768"
ms.assetid: e7a17c77-06bb-4d33-966e-addb4f51caaf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ya no se admiten instrucciones &#39;Line&#39; (error del compilador de Smart Device/Visual Basic).
Ya no se admite la instrucción `Line`. La función de E\/S de archivos está disponible normalmente como <xref:Microsoft.VisualBasic.FileSystem.LineInput%2A?displayProperty=fullName>, pero no es compatible con la versión de destino de .NET Compact Framework.  
  
 **Identificador de error:** BC30768  
  
### Para corregir este error  
  
-   Si está accediendo a archivos, use las funciones definidas en el espacio de nombres <xref:System.IO>.  
  
-   Si está realizando gráficos, use <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName>.  
  
## Vea también  
 <xref:System.IO>   
 <xref:System.Drawing>   
 [Acceso a archivos con Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)