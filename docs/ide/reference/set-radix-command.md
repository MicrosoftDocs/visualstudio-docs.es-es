---
title: "Establecer base (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.setradix"
helpviewer_keywords: 
  - "Debug.SetRadix (comando)"
  - "Establecer base (comando)"
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Establecer base (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Establece o devuelve la base numérica utilizada para mostrar valores enteros.  
  
## Sintaxis  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## Argumentos  
 `10`, `16`, `hex` o `dec`  
 Opcional.  Indica decimal \(10 o dec\) o hexadecimal \(16 o hex\).  Si se omite un argumento, se devuelve el valor base actual.  
  
## Ejemplo  
 En este ejemplo se establece el entorno para mostrar valores enteros en formato hexadecimal.  
  
```  
>Debug.SetRadix hex  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)