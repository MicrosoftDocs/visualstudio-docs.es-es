---
title: "No se puede generar una referencia al archivo &#39;&lt;nombreDeArchivo&gt;&#39; (use la utilidad TLBIMP para hacer referencia a archivos DLL de COM): &lt;mensaje de error&gt; | Microsoft Docs"
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
  - "vbc30142"
  - "bc30142"
helpviewer_keywords: 
  - "BC30142"
ms.assetid: ee0f2c77-3714-4ec2-bddf-d098ab77722f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede generar una referencia al archivo &#39;&lt;nombreDeArchivo&gt;&#39; (use la utilidad TLBIMP para hacer referencia a archivos DLL de COM): &lt;mensaje de error&gt;
El compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] llama a Assembly Linker \(Al.exe, también denominado Alink\) para generar un ensamblado con un manifiesto. El vinculador notificó un error al buscar o validar un archivo DLL de COM\+.  
  
 **Identificador de error:** BC30142  
  
### Para corregir este error  
  
1.  Examine el mensaje de error citado y consulte el tema [Errores y advertencias de la herramienta Al.exe](http://msdn.microsoft.com/es-es/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) para ver una explicación más detallada y consejos.  
  
2.  Si la referencia deseada es a un archivo DLL de COM en lugar de un archivo DLL de COM\+, use el [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) para generar la referencia.  
  
3.  Si el error persiste, reúna información sobre las circunstancias y notifíquelo a los Servicios de soporte técnico de Microsoft.  
  
## Vea también  
 [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Errores y advertencias de la herramienta Al.exe](http://msdn.microsoft.com/es-es/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [PAVEOVER Compatibilidad de productos y accesibilidad](http://msdn.microsoft.com/es-es/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)