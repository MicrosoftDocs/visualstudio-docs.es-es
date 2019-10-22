---
title: Comando Alternar punto de interrupción | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 25c9a22db7ae136068ec374f874453dbd4a7c4b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658617"
---
# <a name="toggle-breakpoint-command"></a>Alternar puntos de interrupción (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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

## <a name="see-also"></a>Otras referencias
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos de [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
