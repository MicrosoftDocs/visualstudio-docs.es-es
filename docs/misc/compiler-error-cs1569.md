---
title: "Error del compilador CS1569 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1569"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1569"
ms.assetid: 1d5e89d6-0a05-4e4f-b472-9089146696bb
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1569
Error al generar el archivo de documentación XML 'Filename' \('reason'\)  
  
 Al intentar escribir la documentación XML en el archivo mencionado en el mensaje, se produjo un error por el motivo especificado. El motivo puede ser algo como "unidad de red no encontrada" o "acceso denegado". A menudo, el motivo sugerirá qué se debe hacer para corregir el error. Por ejemplo, si el error indica "acceso denegado", debe comprobar que tiene permiso de escritura para el archivo.  
  
## Ejemplo  
  
```  
// 1569a.cs // compile with: /doc:CS1569.xml // post-build command: attrib +r CS1569.xml class Test { /// <summary>Test.</summary> public static void Main() {} }  
```  
  
## Ejemplo  
 En el ejemplo anterior se generó un archivo .xml establecido como de solo lectura. En este ejemplo se intenta escribir en el mismo archivo. El ejemplo siguiente genera la advertencia CS1569:  
  
```  
// CS1569.cs // compile with: /doc:CS1569.xml // CS1569 expected class Test { /// <summary>Test.</summary> public static void Main() {} }  
  
```