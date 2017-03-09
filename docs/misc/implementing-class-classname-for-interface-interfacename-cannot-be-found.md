---
title: "No se encuentra la clase de implementaci&#243;n &#39;&lt;nombreDeClase&gt;&#39; para la interfaz &lt;nombreDeInterfaz&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31094"
  - "bc31094"
helpviewer_keywords: 
  - "BC31094"
ms.assetid: 262cb67e-2930-4a4a-a63e-bb2e201b3b93
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se encuentra la clase de implementaci&#243;n &#39;&lt;nombreDeClase&gt;&#39; para la interfaz &lt;nombreDeInterfaz&gt;
Una clase de implementación del ensamblado de interoperabilidad no está disponible.  
  
 **Identificador de error:** BC31094  
  
### Para corregir este error  
  
1.  Compruebe que la biblioteca de tipos para el objeto COM sea válida.  
  
2.  Use el importador de la biblioteca de tipos \(Tlbimp.exe\) para crear manualmente un ensamblado de interoperabilidad y luego agregue una referencia a dicho ensamblado desde el proyecto.  
  
## Vea también  
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [Interoperabilidad COM](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)