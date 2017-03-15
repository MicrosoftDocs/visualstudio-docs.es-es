---
title: "Falta la definici&#243;n de &#39;RaiseEvent&#39; para el evento &#39;&lt;nombreEvento&gt;&#39;. | Microsoft Docs"
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
  - "vbc31132"
  - "bc31132"
helpviewer_keywords: 
  - "BC31132"
ms.assetid: 8f3442fd-2ed1-4dbc-83a8-f0860ec022ac
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Falta la definici&#243;n de &#39;RaiseEvent&#39; para el evento &#39;&lt;nombreEvento&gt;&#39;.
Si un evento se declara como `Custom`, debe proporcionar un procedimiento para generar el evento.  
  
 **Identificador de error:** BC31132  
  
### Para corregir este error  
  
1.  Incluya una declaración `RaiseEvent` entre la instrucción `Custom Event` y la instrucción `End Event`.  
  
2.  Compruebe que otros procedimientos de la declaración de evento terminan correctamente.  
  
## Vea también  
 [RaiseEvent \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)   
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)