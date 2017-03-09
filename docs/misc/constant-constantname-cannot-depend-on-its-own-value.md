---
title: "La constante &#39;&lt;constantname&gt;&#39; no puede depender de su propio valor | Microsoft Docs"
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
  - "bc30500"
  - "vbc30500"
helpviewer_keywords: 
  - "BC30500"
ms.assetid: 0dad89bc-9196-492f-acd9-7777757362f7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La constante &#39;&lt;constantname&gt;&#39; no puede depender de su propio valor
Ha creado una dependencia circular en el código, donde una constante depende de su propio valor. Por ejemplo: `Const a = Const b; Const b = Const a`.  
  
 **Identificador de error:** BC30500  
  
### Para corregir este error  
  
1.  Compruebe el código para ver dónde se evalúa la constante y modifíquela según corresponda.  
  
## Vea también  
 [NOTINBUILD Información general sobre las constantes](http://msdn.microsoft.com/es-es/5c7f57fb-48b2-4a2f-afee-79d8e3adf15b)