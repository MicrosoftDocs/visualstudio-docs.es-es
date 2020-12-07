---
title: Mostrar desensamblador (Comando)
description: Obtenga información sobre el comando Mostrar desensamblado y cómo inicia el proceso de depuración y le permite especificar cómo se administran los errores.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15e9016551b178b0a29656e615d029ddaf0ca279
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305340"
---
# <a name="list-disassembly-command"></a>Mostrar desensamblador (Comando)
Inicia el proceso de depuración y le permite especificar cómo se deben tratar los errores.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Conmutadores
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

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Consulte también

- [Mostrar pila de llamadas (Comando)](../../ide/reference/list-call-stack-command.md)
- [Mostrar subprocesos (Comando)](../../ide/reference/list-threads-command.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)