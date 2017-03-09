---
title: "&lt;tipo1&gt; &#39;&lt;nombreDeTipo&gt;&#39; no se puede declarar &#39;Overrides&#39; porque no reemplaza un &lt;tipo1&gt; en un &lt;tipo2&gt; base | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30284"
  - "bc30284"
helpviewer_keywords: 
  - "BC30284"
ms.assetid: 8166bd09-dad3-495d-8cf7-66f90824a288
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;tipo1&gt; &#39;&lt;nombreDeTipo&gt;&#39; no se puede declarar &#39;Overrides&#39; porque no reemplaza un &lt;tipo1&gt; en un &lt;tipo2&gt; base
Una instrucción `Sub`, `Function` o `Property` especifica `Overrides` cuando no existe ningún tipo con el mismo nombre en una clase base.  
  
 **Identificador de error:** BC30284  
  
### Para corregir este error  
  
1.  Compruebe que el nombre del tipo está escrito correctamente.  
  
2.  Quite la palabra clave `Overrides` superflua.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)