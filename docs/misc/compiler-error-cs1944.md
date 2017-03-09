---
title: "Error del compilador CS1944 | Microsoft Docs"
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
  - "CS1944"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1944"
ms.assetid: e5e2c018-9a7e-48ee-8dd3-98e3553777c1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1944
Un árbol de expresión no puede contener una operación de puntero no segura  
  
 Los árboles de expresión no admiten tipos de puntero porque el método <xref:System.Linq.Expressions.Expression%601.Compile%2A?displayProperty=fullName> solo tiene permitido generar código comprobable. Vea los comentarios  
  
### Para corregir este error  
  
1.  No use tipos de puntero cuando intente crear un árbol de expresión.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS1944:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 En algunas situaciones es correcto usar punteros en árboles de expresión. Por ejemplo, considere el siguiente código:  
  
 `Expression<Func\<int*[], int*[]>) e = (int*[] i)=>i;`  
  
 Este código es un árbol de expresión válido porque ningún argumento de tipo es un tipo de puntero. Son matrices de punteros y las matrices no son tipos de puntero. Además, el cuerpo del árbol de expresión no hace nada peligroso con ningún puntero.  
  
## Vea también  
 [no seguras](/dotnet/csharp/language-reference/keywords/unsafe)