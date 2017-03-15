---
title: "Advertencia del compilador (nivel 1) CS1695 | Microsoft Docs"
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
  - "CS1695"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1695"
ms.assetid: cc4e4d00-0618-400d-985b-90968e98772c
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1695
Sintaxis de \#pragma checksum no válida; debe ser \#pragma checksum "nombre de archivo" "{XXXXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXXXXX}" "XXXX..."  
  
 Raramente encontrará este error, ya que normalmente la suma de comprobación se inserta en tiempo de ejecución si está generando código por medio de la API de Code Dom.  
  
 Sin embargo, si escribiera en esta instrucción `#pragma` y no especificara correctamente el GUID o la suma de comprobación, obtendría este error. La comprobación de sintaxis del compilador no valida que haya escrito un identificador GUID correcto, pero sí comprueba el número correcto de dígitos y delimitadores, y que los dígitos sean hexadecimales. De igual forma, comprueba que la suma de comprobación contenga un número par de dígitos y que los dígitos sean hexadecimales.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1695.  
  
```  
// CS1695.cs #pragma checksum "12345"  // CS1695 public class Test { static void Main() { } }  
```