---
title: "&lt;procedurename1&gt;  no puede invalidar &lt;procedurename2&gt; porque se diferencian en los par&#225;metros declarados como &#39;ParamArray&#39;. | Microsoft Docs"
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
  - "bc30906"
  - "vbc30906"
helpviewer_keywords: 
  - "BC30906"
ms.assetid: 12939030-732e-4c6d-8fe9-707b7532174b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;procedurename1&gt;  no puede invalidar &lt;procedurename2&gt; porque se diferencian en los par&#225;metros declarados como &#39;ParamArray&#39;.
Un procedimiento en una clase derivada reemplaza un procedimiento denominado de forma idéntica en la clase base, pero las listas de parámetros son diferentes.  
  
 Para reemplazar un procedimiento en una clase heredada, el procedimiento de reemplazo debe coincidir con su lista de parámetros, nivel de acceso y el tipo devuelto \(si existe\). En concreto, debe coincidir con cualquier declaración [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) o [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray).  
  
 **Identificador de error:** BC30906  
  
### Para corregir este error  
  
-   Si desea reemplazar el procedimiento, haga que el parámetro enumere exactamente lo mismo que la lista de parámetros en el procedimiento de clase base. Si el último parámetro se declara con `ParamArray` en el procedimiento de la clase base, declárelo con `ParamArray` en el procedimiento de reemplazo.  
  
-   Si desea una lista de parámetros distinta de la versión de la clase base, no podrá reemplazarlo. Considere, en su lugar, sobrecargarlo. Para obtener más información, consulta [Sobrecarga de procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading).  
  
## Vea también  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [NO ESTÁ EN LA COMPILACIÓN: Invalidar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)