---
title: "Ir a (Comando) | Microsoft Docs"
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
  - "edit.goto"
helpviewer_keywords: 
  - "Debug.Goto (comando)"
  - "Ir a (comando)"
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Ir a (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Mueve el cursor a la línea especificada.  
  
## Sintaxis  
  
```  
Edit.GoTo [linenumber]  
```  
  
## Argumentos  
 `linenumber`  
 Opcional.  Entero que representa el número de la línea a la que se va a ir.  
  
## Comentarios  
 La numeración de líneas comienza por uno.  Si el valor de `linenumber` es menor que uno, se muestra la primera línea.  Si el valor de `linenumber` es mayor que el número de la última línea, se muestra la última línea.  
  
 Si no se especifica ningún valor para `linenumber`, se muestra el cuadro de diálogo **Ir a la línea**.  
  
 El alias de este comando es GoToLn.  
  
## Ejemplo  
  
```  
>Edit.GoTo 125  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)