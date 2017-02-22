---
title: "Alternar puntos de interrupci&#243;n (Comando) | Microsoft Docs"
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
  - "debug.togglebreakpoint"
helpviewer_keywords: 
  - "Debug.ToggleBreakPoint (comando)"
  - "Alternar puntos de interrupción (comando)"
  - "ToggleBreakpoint (comando)"
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Alternar puntos de interrupci&#243;n (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Activa o desactiva el punto de interrupción, en función del estado actual, en la ubicación actual del archivo.  
  
## Sintaxis  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## Argumentos  
 `text`  
 Opcional.  Si se especifica texto, la línea se marca como un punto de interrupción con nombre.  De lo contrario, la línea se marca como un punto de interrupción sin nombre, que es similar a lo que sucede al presionar F9.  
  
## Ejemplo  
 El ejemplo siguiente alterna el punto de interrupción actual.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)