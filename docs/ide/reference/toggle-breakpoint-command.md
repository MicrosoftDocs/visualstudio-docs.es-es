---
title: Alternar puntos de interrupción (Comando)
description: Obtenga información sobre el comando Alternar puntos de interrupción para activar o desactivar el punto de interrupción, en función del estado actual, en la ubicación actual del archivo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0a02cb0659df431b3e6eca7c9ad1f13f8c3676b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886488"
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

## <a name="see-also"></a>Consulte también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
