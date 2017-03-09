---
title: "Es necesaria una referencia al ensamblado &#39;&lt;nombreEnsamblado&gt;&#39; que contiene la interfaz implementada &#39;&lt;nombreInterfaz&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30009"
  - "bc30009"
helpviewer_keywords: 
  - "BC30009"
ms.assetid: b2dfb89d-7fde-4a8e-ba7f-fe1e59eabaca
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es necesaria una referencia al ensamblado &#39;&lt;nombreEnsamblado&gt;&#39; que contiene la interfaz implementada &#39;&lt;nombreInterfaz&gt;&#39;.
Es necesaria una referencia al ensamblado '\<nombreEnsamblado\>' que contiene la interfaz implementada '\<nombreInterfaz\>'. Agregue una al proyecto.  
  
 La interfaz se define en una biblioteca de vínculos dinámicos \(DLL\) o ensamblado al que no se hace referencia directamente en el proyecto. El compilador [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] necesita una referencia para evitar la ambigüedad en caso de que la interfaz esté definida en más de una DLL o ensamblado.  
  
 **Identificador de error:** BC30009  
  
### Para corregir este error  
  
-   Incluya el nombre de la DLL o ensamblado no referenciados en las referencias del proyecto.  
  
## Vea también  
 [NIB: Hacer referencia a espacios de nombres y componentes](http://msdn.microsoft.com/es-es/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)