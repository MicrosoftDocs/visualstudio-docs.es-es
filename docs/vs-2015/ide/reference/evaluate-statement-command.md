---
title: Evaluar instrucción (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e2db8596c1c16f5c9fb54a8c7c867b06e997b7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657708"
---
# <a name="evaluate-statement-command"></a>Evaluar instrucción (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Evalúa y muestra la instrucción dada.

## <a name="syntax"></a>Sintaxis

```
Debug.EvaluateStatement text
```

## <a name="arguments"></a>Argumentos
 `text` Obligatorio. Instrucción que se va a evaluar.

## <a name="remarks"></a>Observaciones
 La ventana que se usa para escribir el comando **EvaluateStatement** determina si el signo igual (=) se interpreta como operador de comparación o como operador de asignación.

 En la ventana **Comandos**, un signo igual (=) se interpreta como un operador de comparación. Por lo tanto, por ejemplo, si los valores de las variables `a` y `b` son diferentes, entonces el comando

```
>Debug.EvaluateStatement(a=b)
```

 devolverá un valor de `false`.

 En la ventana **Inmediato**, por el contrario, un signo igual (=) se interpreta como un operador de asignación. Por lo tanto, por ejemplo, el comando

```
>Debug.EvaluateStatement(a=b)
```

 asignará a la variable `a` el valor de la variable `b`.

## <a name="example"></a>Ejemplo

```
>Debug.EvaluateStatement(a+b)
```

## <a name="see-also"></a>Consulte también
 [Comando Imprimir](../../ide/reference/print-command.md) comandos de [Visual Studio comandos](../../ide/reference/visual-studio-commands.md) de la [ventana comandos](../../ide/reference/command-window.md) [Buscar/comando cuadros](../../ide/find-command-box.md) de comandos de [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
