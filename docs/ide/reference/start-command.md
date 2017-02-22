---
title: "Iniciar (Comando) | Microsoft Docs"
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
  - "debug.start"
helpviewer_keywords: 
  - "Debug.Start (comando)"
  - "Iniciar (comando)"
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Iniciar (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Empieza a depurar el proyecto de inicio.  
  
## Sintaxis  
  
```  
Debug.Start [address]  
```  
  
## Argumentos  
 `address`  
 Opcional.  Dirección en la que el programa interrumpe la ejecución, similar a un punto de interrupción en el código fuente.  Este argumento sólo es válido en modo de depuración.  
  
## Comentarios  
 El comando **Start**, cuando se ejecuta, realiza una operación RunToCursor en la dirección especificada.  
  
## Ejemplo  
 En este ejemplo se inicia el depurador y se omite cualquier excepción que se produzca.  
  
```  
>Debug.Start  
```  
  
## Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)