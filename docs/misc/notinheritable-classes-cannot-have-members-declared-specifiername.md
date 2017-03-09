---
title: "Las clases &#39;NotInheritable&#39; no pueden tener miembros declarados como &#39;&lt;specifiername&gt;&#39; | Microsoft Docs"
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
  - "vbc30607"
  - "bc30607"
helpviewer_keywords: 
  - "BC30607"
ms.assetid: c800e24e-d055-402f-b378-6d2f4041ff16
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las clases &#39;NotInheritable&#39; no pueden tener miembros declarados como &#39;&lt;specifiername&gt;&#39;
Los modificadores de reemplazo no pueden utilizarse con clases `NotInheritable` porque no se pueden reemplazar sus miembros.  
  
 **Id. de error:** BC30607  
  
### Para corregir este error  
  
-   Quite los modificadores de reemplazo, como `Overridable`, `NotOverridable` o `MustOverride`, de la definición de clase.  
  
## Vea también  
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)