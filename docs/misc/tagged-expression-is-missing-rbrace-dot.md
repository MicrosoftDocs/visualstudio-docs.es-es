---
title: "Tagged expression is missing &#39;}&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_RE_TAGMISSINGCLOSE"
  - "vs.message.0x800A00D6"
ms.assetid: 832905d3-0faa-43c8-9c37-37130e66e6d2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Tagged expression is missing &#39;}&#39;.
Este error se produce normalmente cuando, en una cadena de búsqueda, se especifica una llave de apertura \(`{`\), pero se omite la de cierre \(`}`\).  
  
### Para corregir este error  
  
1.  Para buscar el literal de cadena `{`, utilice `\{`.  
  
2.  Para etiquetar una expresión, escriba la llave de cierre \(`}`\) que falta.  
  
## Vea también  
 [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/es-es/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Buscar en archivos](../ide/find-in-files.md)