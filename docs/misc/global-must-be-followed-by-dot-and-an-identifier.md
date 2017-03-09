---
title: "&quot;Global&quot; debe ir seguido de &quot;.&quot; y un identificador | Microsoft Docs"
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
  - "bc36000"
  - "vbc36000"
helpviewer_keywords: 
  - "BC36000"
ms.assetid: 0007d7b4-54a2-4f09-904c-d5ad60a55f8e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Global&quot; debe ir seguido de &quot;.&quot; y un identificador
La palabra clave [Global \- delete](http://msdn.microsoft.com/es-es/18c8ba14-40f6-4978-8096-6a5852324635) aparece en un contexto distinto del de obtener acceso a un espacio de nombres.  
  
 El propósito de `Global` es permitir que el código tenga acceso a un espacio de nombres de nivel de raíz desde dentro de una estructura de espacio de nombres que tiene bloqueado el espacio de nombres de nivel de raíz.  
  
 **Identificador de error:** BC36000  
  
### Para corregir este error  
  
-   Si quiere obtener acceso a un espacio de nombres de nivel de raíz, especifíquelo poniendo un punto \(`.`\) después de la palabra clave `Global`.  
  
    ```  
    Dim keyInfo As Global.System.ConsoleKeyInfo  
    ```  
  
-   Si no quiere tener acceso a un espacio de nombres de nivel de raíz, quite la palabra clave `Global`.  
  
## Vea también  
 [Global \- delete](http://msdn.microsoft.com/es-es/18c8ba14-40f6-4978-8096-6a5852324635)