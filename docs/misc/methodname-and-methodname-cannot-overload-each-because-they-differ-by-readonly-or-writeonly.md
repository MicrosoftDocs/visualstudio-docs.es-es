---
title: "&#39;&lt;nombreM&#233;todo&gt;&#39; y &#39;&lt;nombreM&#233;todo&gt;&#39; no se pueden sobrecargar el uno al otro debido a que solo se diferencian en &#39;ReadOnly&#39; o &#39;WriteOnly&#39;. | Microsoft Docs"
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
  - "vbc30366"
  - "BC30366"
helpviewer_keywords: 
  - "BC30366"
ms.assetid: 2440fd29-e205-4004-b2ee-9d954d17b8d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreM&#233;todo&gt;&#39; y &#39;&lt;nombreM&#233;todo&gt;&#39; no se pueden sobrecargar el uno al otro debido a que solo se diferencian en &#39;ReadOnly&#39; o &#39;WriteOnly&#39;.
Ha intentado sobrecargar dos métodos que solo se diferencian entre sí en sus declaraciones `ReadOnly` y `WriteOnly`. Solo puede usar la lista de argumentos para diferenciar las versiones.  
  
 **Identificador de error:** BC30366  
  
### Para corregir este error  
  
-   Asegúrese de que los métodos se diferencian en algo más que en `ReadOnly` y `WriteOnly`.  
  
## Vea también  
 [Consideraciones sobre la sobrecarga de procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)