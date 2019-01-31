---
title: Evaluar instrucción (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89f8eacc11e591545e1a542c0e1eeda3c45b7df3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002397"
---
# <a name="evaluate-statement-command"></a>Evaluar instrucción (Comando)
Evalúa y muestra la instrucción dada.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Argumentos
 `text` Obligatorio. Instrucción que se va a evaluar.

## <a name="remarks"></a>Comentarios
 La ventana que se usa para escribir el comando **EvaluateStatement** determina si el signo igual (=) se interpreta como operador de comparación o como operador de asignación.

 En la ventana **Comandos**, un signo igual (=) se interpreta como un operador de comparación. Por lo tanto, por ejemplo, si los valores de las variables `a` y `b` son diferentes, entonces el comando

```cmd
>Debug.EvaluateStatement(a=b)
```

 devolverá un valor de `false`.

 En la ventana **Inmediato**, por el contrario, un signo igual (=) se interpreta como un operador de asignación. Por lo tanto, por ejemplo, el comando

```cmd
>Debug.EvaluateStatement(a=b)
```

 asignará a la variable `a` el valor de la variable `b`.

## <a name="example"></a>Ejemplo

```cmd
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Vea también

- [Imprimir (Comando)](../../ide/reference/print-command.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)