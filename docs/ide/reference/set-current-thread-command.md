---
title: "Establecer subproceso actual (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.setcurrentthread"
helpviewer_keywords: 
  - "Debug.SetCurrentThread (comando)"
  - "Establecer subproceso actual (comando)"
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Establecer subproceso actual (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Establece el subproceso especificado como el subproceso actual.  
  
## Sintaxis  
  
```  
Debug.SetCurrentThread index  
```  
  
## Argumentos  
 `index`  
 Obligatorio.  Selecciona un subproceso por su índice.  
  
## Ejemplo  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)