---
title: "Mostrar subprocesos (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listthreads"
helpviewer_keywords: 
  - "Debug.ListThreads (comando)"
  - "Mostrar subprocesos (comando)"
  - "ListThreads (comando)"
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Mostrar subprocesos (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Muestra una lista de los subprocesos del programa actual.  
  
## Sintaxis  
  
```  
Debug.ListThreads [index]  
```  
  
## Argumentos  
 `index`  
 Opcional.  Selecciona un subproceso por su índice para que sea el subproceso actual.  
  
## Comentarios  
 Cuando se especifica, el argumento `index` marca el subproceso indicado como el subproceso actual.  Se muestra un asterisco \(\*\) en la lista junto al subproceso actual.  
  
## Ejemplo  
  
```  
>Debug.ListThreads   
```  
  
## Vea también  
 [Mostrar pila de llamadas \(Comando\)](../../ide/reference/list-call-stack-command.md)   
 [Mostrar desensamblador \(Comando\)](../../ide/reference/list-disassembly-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)