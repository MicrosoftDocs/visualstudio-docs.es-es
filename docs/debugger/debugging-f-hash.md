---
title: "Depurar F# | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Depurar [F#]"
  - "F#, depurar"
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar F# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La depuración de F\# es similar a la depuración de cualquier lenguaje administrado, con algunas excepciones:  
  
-   La ventana **Automático** no muestra variables de F\#.  
  
-   El modo Editar y Continuar no se admite en F\#.  Es posible editar código de F\# durante una sesión de depuración pero se debería evitar.  Dado que los cambios de código no se aplican durante la sesión de depuración, si se realizan cambios en el código de F\# durante la depuración, el código fuente no se corresponderá con el código objeto de la depuración.  
  
-   El depurador no reconoce expresiones de F\#.  Para escribir una expresión en una ventana de depurador o un cuadro de diálogo durante la depuración de F\#, se debe convertir la expresión en la sintaxis de C\#.  Al convertir una expresión de F\# en C\#, no olvide que C\# usa \=\= como operador de comparación de igualdad y que F\# utiliza \=.  
  
## Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)