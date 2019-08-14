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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bdc1c97d35b79fec40bbaf8994176cfbb27b8e8
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919217"
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

## <a name="see-also"></a>Otras referencias

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)