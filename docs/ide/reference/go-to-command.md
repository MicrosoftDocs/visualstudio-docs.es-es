---
title: Ir a (Comando)
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
ms.openlocfilehash: 535906d8b8d7f8ba0c2984d22ceead18a0d47c2d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569210"
---
# <a name="go-to-command"></a>Ir a (Comando)
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

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
