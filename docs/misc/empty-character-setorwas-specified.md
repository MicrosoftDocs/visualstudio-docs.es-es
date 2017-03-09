---
title: "Se ha especificado un juego de caracteres vac&#237;o. | Microsoft Docs"
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
  - "vs.message.VS_E_RE_EMPTYSET"
  - "vs.message.0x800A00DF"
ms.assetid: 27ed2ebe-a492-4bc9-ab33-a09fba6cf1d3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Se ha especificado un juego de caracteres vac&#237;o.
Este error se produce normalmente cuando se ha seleccionado la opción de expresiones regulares y se ha especificado una cadena que contiene una sintaxis incompleta para los modelos **Juego de caracteres \[\]** o **Carácter no perteneciente al juego de caracteres \[^\]**.  Por ejemplo, `[}`.  
  
### Para corregir este error  
  
1.  Revise el tema Expresiones regulares para obtener más información acerca de la sintaxis correcta para el modelo y vuelva a escribir la cadena.  
  
## Vea también  
 [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/es-es/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Buscar en archivos](../ide/find-in-files.md)   
 [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)