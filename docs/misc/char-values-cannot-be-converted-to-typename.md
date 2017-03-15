---
title: "Los valores &#39;Char&#39; no se pueden convertir a &#39;&lt;nombreDeTipo&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32006"
  - "vbc32006"
helpviewer_keywords: 
  - "BC32006"
ms.assetid: c033f65e-a315-47fc-be2e-ed371847a221
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los valores &#39;Char&#39; no se pueden convertir a &#39;&lt;nombreDeTipo&gt;&#39;
Los valores 'Char' no se pueden convertir a '\<nombreDeTipo\>'. Use Microsoft.VisualBasic.AscW para interpretar un carácter como valor Unicode o Microsoft.VisualBasic.Val para interpretarlo como un dígito.  
  
 Una expresión intenta convertir un valor `Char` a un tipo de datos distinto de `String` o `Object`.  
  
 **Identificador de error:** BC32006  
  
### Para corregir este error  
  
-   Use la función `AscW` para interpretar un valor `Char` como un carácter Unicode o la función `Val` para interpretarlo como un dígito numérico.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Asc, AscW \(Funciones\)](http://msdn.microsoft.com/es-es/6814bfec-12ba-41fb-b10e-bec99750d5e1)   
 [NO ESTÁ EN LA COMPILACIÓN: Val \(Función\)](http://msdn.microsoft.com/es-es/81650f77-9242-4ec1-8e04-e93b5daa451d)   
 [Char \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/char-data-type)