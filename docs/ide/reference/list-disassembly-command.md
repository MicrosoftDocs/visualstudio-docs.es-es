---
title: Mostrar desensamblador (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dc4bddefe0240a8e53babeec1fdce4f83ce5ef1
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926222"
---
# <a name="list-disassembly-command"></a>Mostrar desensamblador (Comando)
Inicia el proceso de depuración y le permite especificar cómo se deben tratar los errores.

## <a name="syntax"></a>Sintaxis

```cmd
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

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Otras referencias

- [Mostrar pila de llamadas (Comando)](../../ide/reference/list-call-stack-command.md)
- [Mostrar subprocesos (Comando)](../../ide/reference/list-threads-command.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)