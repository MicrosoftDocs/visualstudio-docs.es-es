---
title: "Advertencia del compilador (nivel 1) CS3014 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3014"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3014"
ms.assetid: 6825b42f-1820-4265-b8d8-9b3387d7c130
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3014
'member' no necesita ningún atributo CLSCompliant porque el ensamblado no tiene ningún atributo CLSCompliant  
  
 En un archivo de código fuente donde no se especificó la conformidad con Common Language Specification \(CLS\), una construcción en el archivo se marcó como conforme con CLS. Esto no está permitido. Para resolver esta advertencia, agregue un atributo conforme con CLS de nivel de ensamblado al archivo \(en el ejemplo siguiente, quite la marca de comentario de la línea que contiene el atributo de nivel de ensamblado\). Para más información sobre la conformidad con CLS, vea [Escribir código conforme con CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3) y [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS3014:  
  
```  
// CS3014.cs using System; // [assembly:CLSCompliant(true)] public class I { [CLSCompliant(true)]   // CS3014 public void M() { } public static void Main() { } }  
```