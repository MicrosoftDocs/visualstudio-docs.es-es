---
title: Comando Mostrar desensamblador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ff87add99fb618eaa45d6f9a71a68d82149884e3
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54753400"
---
# <a name="list-disassembly-command"></a>Mostrar desensamblador (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Inicia el proceso de depuración y le permite especificar cómo se deben tratar los errores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## <a name="switches"></a>Modificadores  
 Cada modificador se puede invocar mediante su forma completa o una forma abreviada.  
  
 /count: `number` [o] /c: `number` [o] /length: `number` [o] /l: `number`  
 Opcional. Número de instrucciones que se van a mostrar. El valor predeterminado es 8.  
  
 /endaddress: `expression` [o] /e: `expression`  
 Opcional. Dirección en la que se va a detener el desensamblado.  
  
 /codebytes:`yes`&#124;`no` [o] /bytes:`yes`&#124;`no` [o] /b:`yes`&#124;`no`  
 Opcional. Indica si se deben mostrar bytes de código. El valor predeterminado es `no`.  
  
 /source:`yes`&#124;`no` [o] /s:`yes`&#124;`no`  
 Opcional. Indica si se debe mostrar código fuente. El valor predeterminado es `no`.  
  
 /symbolnames:`yes`&#124;`no` [o] /names:`yes`&#124;`no` [o] /n:`yes`&#124;`no`  
 Opcional. Indica si se deben mostrar nombres de símbolos. El valor predeterminado es `yes`.  
  
 [/linenumbers:`yes`&#124;`no`]  
 Opcional. Permite la visualización de los números de línea asociados con el código fuente. El modificador /source debe tener un valor de `yes` para usar el modificador /linenumbers.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.ListDisassembly  
```  
  
## <a name="see-also"></a>Vea también  
 [Comando Mostrar pila de llamadas](../../ide/reference/list-call-stack-command.md)   
 [Mostrar subprocesos (Comando)](../../ide/reference/list-threads-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
