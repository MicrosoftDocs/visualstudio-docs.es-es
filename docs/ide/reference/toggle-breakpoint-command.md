---
title: Alternar puntos de interrupción (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18473fbd8ee0f7c4b415880da61c86de0bae6fc5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925973"
---
# <a name="toggle-breakpoint-command"></a>Alternar puntos de interrupción (Comando)
Activa o desactiva el punto de interrupción, en función del estado actual, en la ubicación actual del archivo.

## <a name="syntax"></a>Sintaxis

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argumentos

`text`\
Opcional. Si se especifica texto, la línea se marca como un punto de interrupción con nombre. En caso contrario, la línea se marca como un punto de interrupción sin nombre, que es similar a lo que sucede cuando se presiona la tecla F9.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se alterna el punto de interrupción actual.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Otras referencias

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)