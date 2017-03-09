---
title: "El objeto al que se hace referencia tiene un valor de &#39;Nothing&#39; | Microsoft Docs"
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
  - "bc30760"
  - "vbc30760"
helpviewer_keywords: 
  - "BC30760"
ms.assetid: 7e792fd8-2880-402b-a908-c89e5b028300
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El objeto al que se hace referencia tiene un valor de &#39;Nothing&#39;
El objeto que se está usando tiene el valor `Nothing`, pero se espera un valor que se pueda usar.`Nothing` es un valor que indica que un objeto no tiene ningún valor, ya sea porque no se le asignó ningún valor o porque se le asignó el valor `Nothing`.  
  
 **Identificador de error:** BC30760  
  
### Para corregir este error  
  
1.  Compruebe el objeto para asegurarse de que se declaró dentro del ámbito del procedimiento donde se produjo el error.  
  
2.  Compruebe que el valor del objeto se está estableciendo.  
  
    > [!NOTE]
    >  El valor `Nothing` no es igual a cero ni una cadena vacía. Puede usar `IsNothing` para comprobar si un objeto contiene el valor `Nothing`.  
  
## Vea también  
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [NO ESTÁ EN LA COMPILACIÓN: Función IsNothing](http://msdn.microsoft.com/es-es/5b2a4626-e6a9-49d1-b9b1-fcc6a1302319)