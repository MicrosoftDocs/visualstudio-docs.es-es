---
title: Mostrar subprocesos (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b3ad3b30329d574145ce7de839a3e6c164df2d5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919079"
---
# <a name="list-threads-command"></a>Mostrar subprocesos (Comando)
Muestra una lista de los subprocesos del programa actual.

## <a name="syntax"></a>Sintaxis

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumentos
`index`

Opcional. Selecciona un subproceso por su índice para que sea el subproceso actual.

## <a name="remarks"></a>Comentarios
Cuando se especifica, el argumento `index` marca el subproceso indicado como el subproceso actual. Se muestra un asterisco (*) en la lista junto al subproceso actual.

## <a name="example"></a>Ejemplo

```
>Debug.ListThreads
```

## <a name="see-also"></a>Otras referencias

- [Mostrar pila de llamadas (Comando)](../../ide/reference/list-call-stack-command.md)
- [Mostrar desensamblador (comando)](../../ide/reference/list-disassembly-command.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)