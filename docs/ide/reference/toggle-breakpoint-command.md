---
title: Alternar puntos de interrupción (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14f4d60bcbf7c7f394d62cc881c78ef9aa51e545
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946811"
---
# <a name="toggle-breakpoint-command"></a>Alternar puntos de interrupción (Comando)
Activa o desactiva el punto de interrupción, en función del estado actual, en la ubicación actual del archivo.

## <a name="syntax"></a>Sintaxis

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Argumentos
 `text` Opcional. Si se especifica texto, la línea se marca como un punto de interrupción con nombre. En caso contrario, la línea se marca como un punto de interrupción sin nombre, que es similar a lo que sucede cuando se presiona la tecla F9.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se alterna el punto de interrupción actual.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)