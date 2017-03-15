---
title: "&#39;.&#39; o &#39;!&#39; inicial no puede aparecer en una expresi&#243;n constante | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30995"
  - "bc30995"
helpviewer_keywords: 
  - "BC30995"
ms.assetid: eed62684-66db-4fdb-9da7-f1407a55b172
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;.&#39; o &#39;!&#39; inicial no puede aparecer en una expresi&#243;n constante
El acceso a miembros \(.\) y el acceso a miembros de tipo diccionario \(\!\) requieren una expresión que especifique el elemento que contiene el miembro la mayoría de las veces, incluidas las expresiones constantes. La siguiente declaración no es válida.  
  
```  
' Not valid. Const c As String = .name  
```  
  
 **Identificador de error:** BC30995  
  
### Para corregir este error  
  
-   Especifique la instancia que contiene al miembro al que desea acceder.  
  
## Vea también  
 [Inicializadores de objeto: Tipos con nombre y anónimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Cómo: declarar una instancia de un tipo anónimo \(Visual Basic\)](http://msdn.microsoft.com/es-es/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Const \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/const-statement)