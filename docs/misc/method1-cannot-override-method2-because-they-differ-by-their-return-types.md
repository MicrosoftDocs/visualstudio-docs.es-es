---
title: "&#39;&lt;m&#233;todo1&gt;&#39; no puede reemplazar a &#39;&lt;m&#233;todo2&gt;&#39; porque se diferencian en sus tipos de valor devueltos. | Microsoft Docs"
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
  - "bc30437"
  - "vbc30437"
helpviewer_keywords: 
  - "BC30437"
ms.assetid: e566ae72-c597-4b33-b70d-5d4ea879d644
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;todo1&gt;&#39; no puede reemplazar a &#39;&lt;m&#233;todo2&gt;&#39; porque se diferencian en sus tipos de valor devueltos.
Ha intentado reemplazar un método con otro método que se diferencia por su tipo de valor devuelto. Un tipo puede reemplazar un método reemplazable heredado declarando un método con el mismo nombre y signatura y marcando la declaración con el modificador `Overrides`. Las signaturas de los dos métodos deben coincidir.  
  
 **Identificador de error:** BC30437  
  
### Para corregir este error  
  
-   Compruebe los tipos de valor devueltos de los dos métodos y cámbielos como corresponda para que coincidan.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)