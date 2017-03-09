---
title: "&#39;&lt;m&#233;todo1&gt;&#39; no puede invalidar &#39;&lt;m&#233;todo2&gt;&#39; porque se diferencian en un par&#225;metro que est&#225; marcado como &#39;ByRef&#39; frente a &#39;ByVal&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30398"
  - "bc30398"
helpviewer_keywords: 
  - "BC30398"
ms.assetid: 78d62276-4ad9-4876-8c35-a30c9c195638
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;todo1&gt;&#39; no puede invalidar &#39;&lt;m&#233;todo2&gt;&#39; porque se diferencian en un par&#225;metro que est&#225; marcado como &#39;ByRef&#39; frente a &#39;ByVal&#39;.
Ha intentado reemplazar un método con otro método que se diferencia por un parámetro marcado como `ByRef` en lugar de `ByVal`. Los miembros reemplazados deben tener los mismos argumentos que los miembros heredados de la clase base.  
  
 **Identificador de error:** BC30398  
  
### Para corregir este error  
  
-   Asegúrese de que los parámetros son ambos `ByRef` o ambos `ByVal`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Pasar argumentos por valor y por referencia](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)