---
title: "C&#243;digo mixto e informaci&#243;n no mostrada en la ventana Pila de llamadas | Microsoft Docs"
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
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "código administrado, ejecución paso a paso"
  - "Ventana Pila de llamadas, depuración en modo mixto"
  - "Ventana Pila de llamadas, solución de problemas"
  - "marcos nativos"
  - "pilas de llamadas administradas"
  - "depuración en modo mixto, pila de llamadas"
  - "ejecución paso a paso, fuera del código administrado"
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;digo mixto e informaci&#243;n no mostrada en la ventana Pila de llamadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Debido a las diferencias entre las pilas de llamadas para código administrado y código nativo, el depurador no siempre puede mostrar toda la pila de llamadas cuando se mezclan los tipos de código.  Cuando código nativo llama a código administrado, quizá observe las siguientes discrepancias en la ventana **Pila de llamadas**:  
  
-   Puede que el marco nativo inmediatamente encima del código administrado no esté en la ventana **Pila de llamadas**.  Para obtener más información, vea [Cómo: Salir de código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
-   En el caso de las aplicaciones en modo mixto iniciadas fuera del depurador, es posible que la ventana **Pila de llamadas** sólo muestre el código administrado y que no se vea ninguno de los marcos nativos.  
  
 Ninguno de estos casos es habitual.  En la mayoría de las llamadas nativas a código administrado, las pilas de llamadas se muestran correctamente.  
  
## Vea también  
 [Cómo: Utilizar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md)