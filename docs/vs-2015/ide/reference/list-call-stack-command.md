---
title: Mostrar pila de llamadas (Comando) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 69c3708960f5b1ddaf0ff6620b8d90eb64cd86d8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194381"
---
# <a name="list-call-stack-command"></a>Mostrar pila de llamadas (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Muestra la pila de llamadas actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]  
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]  
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]  
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]  
[/ShowExternalCode:yes|no] [Thread:n] [index]  
```  
  
## <a name="arguments"></a>Argumentos  
 `index`  
 Opcional. Establece el marco de pila actual y no muestra ninguna salida.  
  
## <a name="switches"></a>Modificadores  
 Cada modificador se puede invocar mediante su forma completa o una forma abreviada.  
  
 /Count:`number` [o] /C:`number`  
 Opcional. Número máximo de pilas de llamadas para mostrar. El valor predeterminado es Unlimited.  
  
 /ShowTypes:`yes`&#124;`no` [o] /T:`yes`&#124;`no`  
 Opcional. Especifica si se mostrarán o no los tipos de parámetros. El valor predeterminado es `yes`.  
  
 /ShowNames:`yes`&#124;`no` [o] /N:`yes`&#124;`no`  
 Opcional. Especifica si se mostrarán o no los nombres de parámetros. El valor predeterminado es `yes`.  
  
 /ShowValues:`yes`&#124;`no` [o] /V:`yes`&#124;`no`  
 Opcional. Especifica si se mostrarán o no los valores de parámetros. El valor predeterminado es `yes`.  
  
 /ShowModule:`yes`&#124;`no` [o] /M:`yes`&#124;`no`  
 Opcional. Especifica si se mostrará o no el nombre de módulo. El valor predeterminado es `yes`.  
  
 /ShowLineOffset:`yes`&#124;`no` [o] /#:`yes`&#124;`no`  
 Opcional. Especifica si se mostrará o no el desplazamiento de línea. El valor predeterminado es `no`.  
  
 /ShowByteOffset:`yes`&#124;`no` [o] /B:`yes`&#124;`no`  
 Opcional. Especifica si se mostrará o no el desplazamiento de bytes. El valor predeterminado es `no`.  
  
 /ShowLanguage:`yes`&#124;`no` [o] /L:`yes`&#124;`no`  
 Opcional. Especifica si se mostrará o no el idioma. El valor predeterminado es `no`.  
  
 /IncludeCallsAcrossThreads:`yes`&#124;`no` [o] /I:`yes`&#124;`no`  
 Opcional. Especifica si se deben incluir llamadas a otros subprocesos o desde otros subprocesos. El valor predeterminado es `no`.  
  
 /ShowExternalCode:`yes`&#124;`no`  
 Opcional. Especifica si se debe mostrar Solo mi código para la pila de llamadas. Cuando Solo mi código está desactivado, se muestra todo el código que no es del usuario. Cuando Solo mi código está activado, el código de usuario se muestra como `[external]` en la salida de la pila de llamadas.  
  
 Thread:`n`  
 Opcional. Muestra la pila de llamadas del subproceso `n`. Si no se especifica ningún subproceso, muestra la pila de llamadas del subproceso actual.  
  
## <a name="remarks"></a>Comentarios  
 Los cambios realizados en los argumentos o los modificadores se aplican a las invocaciones posteriores de este comando. Si emite el propio Debug.ListCallStackby, se muestra la pila de llamadas completa. Si, por ejemplo, especifica un índice,  
  
```  
Debug.ListCallStack 2  
```  
  
 el marco de pila actual se establece en ese marco (en este caso, el segundo marco).  
  
 También puede escribir este comando usando su alias predefinido, kb. Por ejemplo, puede escribir  
  
```  
kb 2  
```  
  
 para establecer el marco de pila en el segundo marco.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.CallStack /Count:4 /ShowTypes:yes  
```  
  
## <a name="see-also"></a>Vea también  
 [Mostrar desensamblador (Comando)](../../ide/reference/list-disassembly-command.md)   
 [Mostrar subprocesos (Comando)](../../ide/reference/list-threads-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



