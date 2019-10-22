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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ff5e620d4c53889afe17274364d6f92936025d3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672737"
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

 /Count: `number` [o]/c: `number` [o]/length: `number` [o]/l: `number` opcional. Número de instrucciones que se van a mostrar. El valor predeterminado es 8.

 /EndAddress: `expression` [o]/e: `expression` opcional. Dirección en la que se va a detener el desensamblado.

 /CodeBytes: `yes`&#124; `no` [o]/bytes: `yes`&#124; `no` [o]/B: `yes`&#124; `no` opcional. Indica si se deben mostrar bytes de código. El valor predeterminado es `no`.

 /Source: `yes`&#124; `no` [o]/s: `yes`&#124; `no` opcional. Indica si se debe mostrar código fuente. El valor predeterminado es `no`.

 /SymbolNames: `yes`&#124; `no` [o]/names: `yes`&#124; `no` [o]/N: `yes`&#124; `no` opcional. Indica si se deben mostrar nombres de símbolos. El valor predeterminado es `yes`.

 [/LineNumbers: `yes`&#124; `no`] Opta. Permite la visualización de los números de línea asociados con el código fuente. El modificador /source debe tener un valor de `yes` para usar el modificador /linenumbers.

## <a name="example"></a>Ejemplo

```
>Debug.ListDisassembly
```

## <a name="see-also"></a>Otras referencias
 Comando [enumerar pila de llamadas](../../ide/reference/list-call-stack-command.md) comandos de [subprocesos](../../ide/reference/list-threads-command.md) comandos de [Visual Studio comandos](../../ide/reference/visual-studio-commands.md) de la [ventana de comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
