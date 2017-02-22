---
title: "Sugerencias para depurar subprocesos en c&#243;digo nativo | Microsoft Docs"
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
  - "depurar [Visual Studio], subprocesos"
  - "subprocesamiento [Visual Studio], depurar"
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sugerencias para depurar subprocesos en c&#243;digo nativo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A continuación se muestran algunas sugerencias que puede usar al depurar subprocesos en código nativo:  
  
-   Puede ver el contenido del Bloque de información de subprocesos escribiendo `@TIB` en la ventana **Inspección** o en el cuadro de diálogo **Inspección rápida**.  
  
-   Puede ver el último código de error del subproceso actual escribiendo `@Err` en la ventana **Inspección** o en el cuadro de diálogo **Inspección rápida**.  
  
-   Las funciones de las bibliotecas en tiempo de ejecución de C \(CRT\) pueden ser útiles para depurar una aplicación multiproceso.  Para obtener más información, vea [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg).  
  
## Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)