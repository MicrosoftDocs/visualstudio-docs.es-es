---
title: "La variable est&#225;tica &#39;&lt;variablename&gt;&#39; se ha declarado sin una cl&#225;usula &#39;As&#39;; se supone el tipo de &#39;Object&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42111"
  - "bc42111"
helpviewer_keywords: 
  - "BC42111"
ms.assetid: ca6b625c-21a5-45f7-ac67-282f6993a724
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable est&#225;tica &#39;&lt;variablename&gt;&#39; se ha declarado sin una cl&#225;usula &#39;As&#39;; se supone el tipo de &#39;Object&#39;
El compilador no deduce el tipo de datos de las variables locales estáticas. En el ejemplo siguiente, con el valor de `Option Strict` establecido en `Off`, el tipo de `m` será `Object`, independientemente de si el valor de `Option Infer` está establecido en `On` o `Off`. La inferencia de tipo local no se aplica.  
  
```  
Sub Main() Static m = 10 End Sub  
```  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Id. de error:** BC42111  
  
### Para resolver esta advertencia  
  
-   Especifique el tipo de datos de las variables locales estáticas.  
  
     Por ejemplo, si quiere que el elemento `m` del ejemplo anterior sea de tipo `Integer`, especifique el tipo en la declaración.  
  
    ```  
    Sub Main() Static m As Integer = 10 End Sub  
  
    ```  
  
## Vea también  
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [NO ESTÁ EN LA COMPILACIÓN Procedimiento: prolongar la duración de una variable](http://msdn.microsoft.com/es-es/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Inferencia de tipo de variable local](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer \(instrucción\)](/dotnet/visual-basic/language-reference/statements/option-infer-statement)   
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)