---
title: "Falta la definici&#243;n de &#39;RemoveHandler&#39; para el evento &#39;&lt;eventname&gt;&#39;. | Microsoft Docs"
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
  - "bc31131"
  - "vbc31131"
helpviewer_keywords: 
  - "BC31131"
ms.assetid: 0ef68daf-b66e-4ecf-bf2c-dcacabd8aa3d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Falta la definici&#243;n de &#39;RemoveHandler&#39; para el evento &#39;&lt;eventname&gt;&#39;.
Si un evento se declara como `Custom`, debe proporcionar un procedimiento para quitar el controlador de eventos.  
  
 **Identificador de error:** BC31131  
  
### Para corregir este error  
  
1.  Incluya una declaración `RemoveHandler` entre la instrucción `Custom Event` y la instrucción `End Event`.  
  
2.  Compruebe que otros procedimientos de la declaración de evento terminan correctamente.  
  
## Vea también  
 [RemoveHandler \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)