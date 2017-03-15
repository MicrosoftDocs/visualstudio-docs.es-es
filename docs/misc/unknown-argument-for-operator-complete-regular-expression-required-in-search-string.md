---
title: "Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string. | Microsoft Docs"
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
  - "vs.message.0x800A00BE"
  - "vs.message.VS_E_RE_SPECIALUNKNOWN"
ms.assetid: 8cbc2f7f-7ea1-4803-904c-1f716cd36376
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unknown argument for &#39;:&#39; operator. Complete Regular Expression required in search string.
Este error ocurre normalmente cuando se efectúa una búsqueda o reemplazo mediante expresiones regulares o caracteres comodín en una cadena de búsqueda.  Se utilizó el operador \(`:`\) pero seguido de un argumento no válido.  
  
> [!NOTE]
>  Los argumentos del operador \(`:`\) distinguen mayúsculas y minúsculas.  
  
### Para corregir este error  
  
1.  Revise la sintaxis correcta de expresiones regulares presente en el tema "Expresiones regulares."  
  
2.  Asegúrese de que se emplea correctamente las mayúsculas o minúsculas en el argumento.  
  
3.  Si está usando un Editor de métodos de entrada \(IME\), compruebe que no se pasa el argumento usando caracteres de doble ancho.  
  
## Vea también  
 [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/es-es/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Buscar en archivos](../ide/find-in-files.md)