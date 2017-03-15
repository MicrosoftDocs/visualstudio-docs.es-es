---
title: "Argument is missing in &#39;\&#39; escape sequence. | Microsoft Docs"
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
  - "vs.message.VS_E_RE_ESCAPEMISSINGARG"
  - "vs.message.0x800A00BD"
ms.assetid: 5bd6559b-8cd9-450f-91c8-335ff1b1ef86
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Argument is missing in &#39;\&#39; escape sequence.
Este error ocurre normalmente cuando se efectúa una búsqueda o reemplazo mediante expresiones regulares o caracteres comodín en una cadena de búsqueda.  Este error puede deberse al uso de una barra invertida \(`\`\) al final de un patrón de búsqueda, o `\x` ó `\u` sin un carácter hexadecimal Unicode válido.  
  
### Para corregir este error  
  
1.  Para buscar usando el carácter de escape de expresiones regulares, escriba `\`.  
  
2.  Para buscar un carácter Unicode, escriba `\x` ó `\u` seguido de un valor correcto de Unicode.  
  
3.  Para buscar el carácter de barra invertida, use `\\`.  
  
## Vea también  
 [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/es-es/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Buscar en archivos](../ide/find-in-files.md)