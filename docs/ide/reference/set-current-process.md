---
title: "Establecer el proceso actual | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debug.SetCurrentProcess (comando)"
  - "Establecer el proceso actual (comando)"
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Establecer el proceso actual
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Establece el proceso especificado como el proceso activo en el depurador.  
  
## Sintaxis  
  
```  
Debug.SetCurrentProcess index  
```  
  
## Argumentos  
 `index`  
 Requerido.  Índice del proceso.  
  
## Comentarios  
 Puede asociar varios procesos mientras realiza la depuración, pero solo hay un proceso activo en el depurador en un momento determinado.  Puede utilizar el comando `SetCurrentProcess` para establecer el proceso activo.  
  
## Ejemplo  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)