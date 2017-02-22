---
title: "Mostrar desensamblador (Comando) | Microsoft Docs"
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
  - "debug.listdisassembly"
helpviewer_keywords: 
  - "Debug.ListDisassembly (comando)"
  - "Mostrar desensamblador (comando)"
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Mostrar desensamblador (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Comienza el proceso de depuración y permite especificar cómo se controlan los errores.  
  
## Sintaxis  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## Modificadores  
 Se puede invocar todos los modificadores utilizando su forma completa o una forma abreviada.  
  
 \/count: `number` \[o\] \/c: `number` \[o\] \/length: `number` \[o\] \/l: `number`  
 Opcional.  Número de instrucciones que se va a mostrar.  El valor predeterminado es 8.  
  
 \/endaddress: `expression` \[o\] \/e: `expression`  
 Opcional.  Dirección en la que detener el desensamblado.  
  
 \/codebytes:`yes`&#124;`no` \[o\] \/bytes:`yes`&#124;`no` \[o\] \/b:`yes`&#124;`no`  
 Opcional.  Indica si se van a mostrar bytes de código.  El valor predeterminado es `no`.  
  
 \/source:`yes`&#124;`no` \[o\] \/s:`yes`&#124;`no`  
 Opcional.  Indica si se va a mostrar código fuente.  El valor predeterminado es `no`.  
  
 \/symbolnames:`yes`&#124;`no` \[o\] \/names:`yes`&#124;`no` \[o\] \/n:`yes`&#124;`no`  
 Opcional.  Indica si se van a mostrar nombres de símbolos.  El valor predeterminado es `yes`.  
  
 \[\/linenumbers:`yes`&#124;`no`\]  
 Opcional.  Permite ver los números de línea asociados al código fuente.  El modificador \/source debe tener un valor de `yes` para poder utilizar el modificador \/linenumbers.  
  
## Ejemplo  
  
```  
>Debug.ListDisassembly  
```  
  
## Vea también  
 [Mostrar pila de llamadas \(Comando\)](../../ide/reference/list-call-stack-command.md)   
 [Mostrar subprocesos \(Comando\)](../../ide/reference/list-threads-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)