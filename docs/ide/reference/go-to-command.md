---
title: Ir a (Comando)
description: Obtenga información sobre el comando Ir a y cómo mueve el cursor a la línea especificada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0ef161cb8108ed3244c263ee51fee4251fc05d8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305212"
---
# <a name="go-to-command"></a>Ir a, comando
Mueve el cursor a la línea especificada.

## <a name="syntax"></a>Sintaxis

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumentos
`linenumber`\
Opcional. Entero que representa el número de la línea a la que se debe ir.

## <a name="remarks"></a>Comentarios
La numeración de líneas empieza por el uno. Si el valor de `linenumber` es menor que uno, se muestra la primera línea. Si el valor de `linenumber` es mayor que el número de la última línea, se muestra la última línea.

Si no se especifica ningún valor para `linenumber`, se muestra el cuadro de diálogo **Ir a la línea**.

El alias de este comando es GoToLn.

## <a name="example"></a>Ejemplo

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Consulte también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
